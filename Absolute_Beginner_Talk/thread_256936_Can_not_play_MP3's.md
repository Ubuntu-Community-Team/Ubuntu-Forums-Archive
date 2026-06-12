---
title: "Can not play MP3's"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by lazermanx2 on 2006-09-13
Hello, I can not seem to play MP3 music files on Ubuntu. :-k  I get an error message "You do not have a decoder installed to handle this file." What do I need to do to get an MP3 decoder installed? THANKIES! :D

---

### Post by DirtDawg on 2006-09-13
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Christopher Cook on 2006-09-13
synaptic package, search for gstreamer ugly codec.

---

### Post by jcrnan on 2006-09-13
Or just follow this guide: [http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

that will get you support for all formats you need and pluginsupport in firefox, etc. works like a charm and has everything you will need.

---

### Post by buckethead27 on 2006-09-13
[www.getautomatix.com](www.getautomatix.com) - it has everything you need.

---

### Post by lazermanx2 on 2006-09-13
Allright, I have tried everything listed there, both conversion programs and MP3 codec installers, and every single one will not install. I get the error "Error, Dependency is not satisfiable: **********" I am possitive that I am downloaded the correct Arcitecture for my system and it just wont install. How can I get MP3's to play and why doesn't Ubuntu support MP3? ](*,)

---

### Post by jcrnan on 2006-09-13
lazerman: when following the guide did you update your sources.list first?

and did you use the excact commands listed there to get the codecs?

edit: ubuntu doesnt support mp3 automaticly because there is no open source mp3 codecs.

---

### Post by haxer on 2006-09-13
or just the easiest option sudo apt-get install xmms then your password :)

---

### Post by lazermanx2 on 2006-09-13
Sorry, I think that Automatix will work but I'll have to wait til I get home from work. Looks good though. I was refering earlier to the first reply. At any rate, why am I unable to install anything, I always get a dependeny error. Is there any good place to find programs or would you just recomend the Add/Remove utilty that comes with the OS. Thanks for the Automatix suggestion though :D

---

### Post by lazermanx2 on 2006-09-13
Thanks for all the help everyone. I got it working!! :D

---

### Post by jcrnan on 2006-09-14
lazerman: For installing programs the easiest way by far is getting a proper sources.list (as it said in the guide I linked you too) and then just use sudo aptitude install <program>  Not all programs can be installed like that tough (but all the ones in the add/remove programs). If you download programs its either in a deb file wich you just opens and it installs or its the source code wich you have to compile. Compiling is in most cases simple :)

---

