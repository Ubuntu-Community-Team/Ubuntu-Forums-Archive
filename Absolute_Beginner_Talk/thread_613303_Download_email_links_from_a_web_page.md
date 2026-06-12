---
title: "Download email links from a web page"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by bean77 on 2007-11-14
Is there software that will get me a list of email addresses off a web page?  (instead of right click, save as, etc)

Will Downthemall work?

---

### Post by jfinkels on 2007-11-15
You can save the web page as an html file by doing:```
wget -O file.html http://somerandomwebpage.com/file.htm
```, then use grep to search for strings that look like email addresses, and redirect the output to a file:```
grep -o -e "\S*@\S*\.\S*" *file.html* >> emailaddresses
```

The "-o" flag outputs only the part of the line that matches the regular expression. The "-e" flag says that the next thing will be the regular expression to match. The "\S*" means match any non-whitespace character, repeated any number of times. The "@" is a literal "@". The "\." is a literal period.

---

