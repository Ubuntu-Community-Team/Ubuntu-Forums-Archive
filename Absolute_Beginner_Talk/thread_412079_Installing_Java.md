---
title: "Installing Java"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by ffejrey on 2007-04-17
I'm trying to install Java with the instructions from [http://www.java.com/en/download/help/5000010500.xml#rpm]("http://www.java.com/en/download/help/5000010500.xml#rpm") .  

I can do the following command to change the permissions: ```
 chmod a+x jre-1_5_0-linux-i586-rpm.bin
``` 

 But when I do the this command to install it, it says command not found.  What am I missing? ```
./jre-1_5_0-linux-i586-rpm.bin
```

---

### Post by SOULRiDER on 2007-04-17
Just install it from the repositories, its a lot easier!

```
sudo aptitude install sun-java6-jre
```

Also, youre trying to install an RPM file which is a no no in Debian(Ubuntu is based on Debian) Here we use DEB files and NOT RPM.

---

### Post by Fidelio on 2007-04-17
I never managed to install the latest version of Java until I tried automatix, which does it fine. Still no idea what I, or you, were doing wrong.

---

### Post by ffejrey on 2007-04-17
Thanks, installing now.   

At the Java site they only had RPM and bin?  :confused: Why dont they have a DEB file then?

---

### Post by drmbogo on 2007-04-18
[edit]
see below...

---

### Post by drmbogo on 2007-04-18
> **SOULRiDER said:**
> Just install it from the repositories, its a lot easier!

```
sudo aptitude install sun-java6-jre
```

Also, youre trying to install an RPM file which is a no no in Debian(Ubuntu is based on Debian) Here we use DEB files and NOT RPM.

Couldn't get java6! Is there a repository I'm missing?
I did find java5 tho...and it seems to work

---

### Post by Perfect Storm on 2007-04-18
You need to have backports enable in your sourcelist. A good place to set up sourcelist is here: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by drmbogo on 2007-04-23
Aha! That did it!
Thanks!

---

