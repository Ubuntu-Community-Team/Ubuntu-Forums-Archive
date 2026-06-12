---
title: "No make in bash?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by jaywilson on 2006-08-19
I downloaded the KJV Bible for Linux yesterday and wanted to install it using the bash terminal provided by Ubuntu.

I managed to get through the **tar -xvf filename.tar** bit and unpacked it, then was left with some brief instructions to **make** the installation.

bash did not recognise **make** so I'm stuck at the moment.  There is a makefile in the directory but I don't know how to activate it.

(First post, sig to follow, will be along the lines of "Seven years of Windows v seven weeks of Linux")

---

### Post by GeekSpeek'r on 2006-08-19
nope, not default app

so:

apt-get install gcc
apt-get install make

done

---

### Post by taurus on 2006-08-19
All you need is build-essential and you are done...

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by msak007 on 2006-08-19
I would install more than just those 2 apps. In the terminal type

```
sudo aptitude install build-essential
``` 
to install any apps necessary for compiling apps from source.

EDIT: I see taurus already beat me to it :)

---

### Post by jaywilson on 2006-08-19
GeekSpeek'r - thankyou, done that with a sudo, off to the directory now.

taurus - thanks also, I may come back to your suggestion later.  I'm having too much fun at the moment learning the basics.  I ran automatix for [www.mp3unsigned.com](www.mp3unsigned.com) and have ended up with too many Debian add-ons.

---

### Post by taurus on 2006-08-19
I highly recommand you install "build-essential" instead of only "gcc" & "make" if you want to build something from source.  Build-essential will install other necessary files on your system...

---

### Post by GeekSpeek'r on 2006-08-19
yeah, i agree.... the essentials will help prevent other dependency issues as you go along... but your on the right path

Happy computing

---

