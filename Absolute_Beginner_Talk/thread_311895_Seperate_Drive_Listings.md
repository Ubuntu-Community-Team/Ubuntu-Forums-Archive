---
title: "Seperate Drive Listings"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-12-03
I was wondering if there was any way for me to get my root directory and my /data (second drive) to show when I goto Places->Computer Instead of seeing Filesystem?

---

### Post by Ecthelion on 2006-12-04
You can choose to add an entry under locations for those,
Or you can make a symbolic link in the dit you get in when you choose Places -> Computer

To add an entry you just have to "bookmark" a page in nautilus.

To make a symbolic link, do

```
ln -s ./<place to where the link sents> ./<place you want the link to be>
```

In this case you want to sent the link to your /data and you want it to be in the dir you get in when you choose Places -> Computer

Hope this helps...

---

