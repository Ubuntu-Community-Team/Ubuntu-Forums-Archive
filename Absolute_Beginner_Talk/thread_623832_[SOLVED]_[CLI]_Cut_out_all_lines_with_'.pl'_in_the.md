---
title: "[SOLVED] [CLI] Cut out all lines with '.pl' in them"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-11-26
When 'cat'ting my Apache2 access logs i always get a pile of lines from me accessing my stats (awstats.pl) which i dont really want to see.

What can i pipe cat /var/log/apache2/access.log through to only display lines without awstats.pl in it?

---

### Post by evilregis on 2007-11-26
Try the following:

```
cat /var/log/apache2/access.log | grep -v 'awstats.pl'
```

---

