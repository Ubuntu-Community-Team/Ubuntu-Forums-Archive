---
title: "How to install Java for firefox"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by weiyang on 2006-05-09
anyone there. New to ubuntu but able to get it running after browsing the forum. What I need to know now is hot to install the JRE from the download i586.bin folder. It is a steep learning curve as ubuntu does not "autorun". Please help Thanks.

---

### Post by Sef on 2006-05-09
Read the restricted formats.  It will tell you how to add Universe and Multiverse, and it has directions of how to install java.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by JKoder on 2006-05-09
I guess you hav downloaded jre from sun website.
If so all you need too do is:
create a directory called Java

sh <jrefile>.bin

link the folowing fils to /usr/bin

java,javac,jar,javaw
BE AWARE thet this symlinks already exist !
Delete them before proceeding !

reply if worked !
(Worked for me )

---

### Post by weiyang on 2006-05-10
I decide to reinstall ubuntu as after all the fiddling I think I messed. Anyway did things slowly and use Automatix to load JRE. It was a breeze. I just read the post earlier and just completed and tested and firefox has java plugins activated. Thanks anyway.

---

