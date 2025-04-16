## Welcome

### Project Tuva: Richard Feynman’s Messenger Lecture Series
[Project Tuva](https://www.microsoft.com/en-us/research/project/tuva-richard-feynman/)

### Unix commands
```markdown
# file files in top level dir, created 30 day ago
find . -maxdepth 1 -type f -mtime +30

# Find files less than 2 character size
find -name 'purge_ids_2025*' -type f -size -2c -exec stat --printf="%s %n\n" {} +

# Delete files less than 2 char size
find -name 'purge_ids_2025*' -type f -size -2c -exec stat --printf="%n\n" {} + | xargs rm

echo 'BM_BATCH_ITEM' | sed -e 's/$/_/' -e 's/\([^_]\)[^_]*_/\1/g'
 BBI

echo 'This is a test sentence' | sed -e 's/$/ /' -e 's/\([^ ]\)[^ ]* /\1/g' -e 's/^ *//'
 Tiats
```

## Shell Scripts
### Get All certs from store
```markdown
export KEYTOOL=/usr/local/jdk/bin/keytool
export KEYSTORE=/usr/local/jdk/jre/lib/security/cacerts
IFS=$'\n' 
for cert in `${KEYTOOL} -list -keystore ${KEYSTORE} -storepass changeit | grep trustedCertEntry | grep -Eo "^[^,]*"`;do
    `${KEYTOOL} -exportcert -keystore ${KEYSTORE} -alias ${cert}' -file ./certs/${cert}.crt -storepass changeit`
done
```

## AWS Commands
### Get All Running EC2 instances
```markdown
aws ec2 describe-instances --query "Reservations[*].Instances[*].{PublicIP:PublicIpAddress,PrivateIP:PrivateIpAddress,Name:Tags[?Key=='Name']|[0].Value,Status:State.Name}" --filters Name=instance-state-name,Values=running --output table
```


### Editor
1. Edit page using [Editor](https://github.com/wonkday/wonkday.github.io/edit/master/index.md) 
2. After commit, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/wonkday/wonkday.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
