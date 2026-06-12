---
title: "Directory Encryption/Password Protection"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by bobbocanfly on 2007-10-04
I am trying to make a small vault of semi-sensitive information (/var/vault) in which all the files will be encrypted. Is there a way to also set a password so that it cant be accessed at all? Thinking there probably will be some hacked up solution somewhere in the OSS world?

---

### Post by bbukh on 2007-10-04
I can recommend TrueCrypt. It can either encrypt a parition (which you can mount anywhere) or you can make a file which through devmapper is mapped to a "virtual partition" (I forgot the technical term), which is encrypted via TrueCrypt and mounted to anyplace you like.  Search google and forums for specific documentation.

--Boris

---

