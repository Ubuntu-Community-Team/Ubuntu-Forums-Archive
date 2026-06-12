---
title: "Compilers, What comes with Ubuntu"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by ItsAmazazazing on 2007-08-18
The question that I have is what Compiler/s come with Ubuntu, or are installed when you install Ubuntu. I want to learn Java, and write some small games using Java/C++ but I don't know if I have a compiler, or where to start looking for a compiler, let alone what files I am going to need. Is there a beginners portion somewhere that addresses my needs? 

While Im here, I was wondering what I need to get my laptop to play movies. I tried to get the codecs, using a link that I saw in a previous post in a different section of the forum here, and it hasn't worked. Also where can I see a list of devices that are compatable, or have available drivers? I really want my wireless card to work, I miss my wireless.....

Much love...

---

### Post by taurus on 2007-08-18
You need to install them.  For GCC, you have to install the build-essential package.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```
For java, you need the JDK package.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

