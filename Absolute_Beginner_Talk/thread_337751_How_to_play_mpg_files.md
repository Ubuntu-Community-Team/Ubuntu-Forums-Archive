---
title: "How to play mpg files?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Zdravko on 2007-01-13
What should I do in order to be able to play mpg video file?

---

### Post by tkjacobsen on 2007-01-13
you should install some extra gstreamer plugins. Read this wiki which explains about the legan issues and how to install

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Best regards

---

### Post by justin_c18 on 2007-01-14
> **Zdravko said:**
> What should I do in order to be able to play mpg video file?

If you have the room on your computer, check out automatrix2. Download the .deb from 
[http://getautomatix.com/]("http://getautomatix.com/")

It'll download mostly all the popular codecs, and other essentials easily.

---

### Post by ardchoille42 on 2007-01-14
If you're using xine as your media player, you can view .mpg files after installing libxine-extracodecs:

sudo aptitude install libxine-extracodecs

then xine will play .mpf files.

---

### Post by Zdravko on 2007-01-19
I tried to install the winmedia codecs, by following the instruction from the link. I got:
> zdravko@ztm-desktop:~$ sudo dpkg -i w32codecs_20061022-0.0_i386.debsudo dpkg -i w32codecs_20061022-0.0_i386.deb
dpkg: error processing w32codecs_20061022-0.0_i386.debsudo (--install):
 cannot access archive: No such file or directory
dpkg: error processing dpkg (--install):
 cannot access archive: No such file or directory
dpkg: error processing -i (--install):
 cannot access archive: No such file or directory
(Reading database ... 129725 files and directories currently installed.)
Preparing to replace w32codecs 1:20061022-0.0 (using w32codecs_20061022-0.0_i386.deb) ...
Unpacking replacement w32codecs ...
Setting up w32codecs (20061022-0.0) ...
Errors were encountered while processing:
 w32codecs_20061022-0.0_i386.debsudo
 dpkg
 -i


---

### Post by brentroos on 2007-01-19
;)

---

### Post by Zdravko on 2007-01-19
[brentroos]("http://ubuntuforums.org/member.php?u=36774"), that was my first thought... :(

---

### Post by mcduck on 2007-01-19
> **Zdravko said:**
> I tried to install the winmedia codecs, by following the instruction from the link. I got:
The command you used is wrong:
```
sudo dpkg -i w32codecs_20061022-0.0_i386.debsudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

..and this is what it should be:
```
sudo dpkg -i w32codecs_20061022-0.0_i386.deb
```

Note, that you can also just double-click on the .deb package to install it :)

---

### Post by mcduck on 2007-01-19
> **brentroos said:**
> Use a real OS like Microsoft Windows

well that's a helpfull answer :rolleyes:

---

### Post by Zdravko on 2007-01-19
[mcduck]("http://ubuntuforums.org/member.php?u=17309"), then the wiki is wrong, heh :)

This package was actually already installed... I gave it the option - Reinstall...

---

### Post by mcduck on 2007-01-19
no, it's not. I bet you accidentally pasted the command twice ;)

Anyway, it's good that you got it installed.. (looking at the error messages it indeed did install w32codecs on the first try, and then complained about all extra stuff that was on the command)

---

