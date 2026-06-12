---
title: "Md5"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by nkingcade on 2005-12-23
What are the MD5 numbers used for?? I am going to assume that these are hashes of some sort. Are they used to validate something?

Neal

---

### Post by fordfan753 on 2005-12-23
They are used mainly to check if files are whole, and not corrupted in transport, it's just a checksum really.

---

### Post by nkingcade on 2005-12-23
I'll bite. Is there a procedure for using the MD? Is the MD sent with the file? How do I check the file against the MD?

Neal

BTW, 17_ I'm 55 and still trying to get away from Microsoft products. What do I know? I'm having fun during the adventure.

---

### Post by ubuntu27 on 2005-12-23
About MD5, Wikipedia: [http://en.wikipedia.org/wiki/MD5](http://en.wikipedia.org/wiki/MD5)

---

### Post by XeRXeS on 2005-12-23
Basically, MD5 hashes are used in this case to provide a checksum for files to ensure that they are valid. 

When the distributors have a copy that they know to be complete and not corrupted, they use a program to calculate the md5 hash of the file. The file is then distributed, along with a separate file (usually called MD5SUM or some other variant) containing the valid hashes for the file. 

Once you have downloaded the file, you can use a program to calculate the md5 hash, which you can then compare with the provided hash. As md5 hashes are *virtually* unique, if there is even a few bytes difference between the files, the hashes will be different, and you can tell that there is a problem with the downloaded copy of the file.

On Unix / Linux, md5sum is the CLI program which is normally available for calculating checksums, although you'll have to google around a bit for an equivalent on Windows, if that is what you are using at the minute. I know there is a CLI port as part of UnxUtils ([http://unxutils.sourceforge.net/](http://unxutils.sourceforge.net/)) but there are GUI versions if you look around.

---

### Post by nkingcade on 2005-12-27
[LEFT]Thanks to all who replied. 

Neal

[/LEFT]

---

