---
title: "Can not view flash in firefox-about to shoot thy self"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by kdiggdy on 2007-06-19
Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. 
grr...
help please?

I have downloaded the package from the website
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
Option 1: .tar.gz
moved the plugin files to
```
kalpesh@kalpesh-desktop:~/Desktop$ sudo mv -f ~/Desktop/install_flash_player_9_linux/libflashplayer.so /usr/lib64/firefox/plugins
kalpesh@kalpesh-desktop:~/Desktop$ sudo mv -f ~/Desktop/install_flash_player_9_linux/flashplayer.xpt /usr/lib64/firefox/plugins

```
did not work, the files are in the plugin folder in firefox

Followed the installation on the adobe website

```
kalpesh@kalpesh-desktop:~/Desktop$ ~/Desktop/install_flash_player_9_linux/flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.


```

I also have the ubunti restricted extras package installed
and working

also I tried that nspluginwrapper but couldent figure it out because its in .rpm 

soooo............yeah any flash wont work... what now?

---

### Post by floke on 2007-06-19
Applications / Add-Remove / search for Flash
Install
Breathe

---

### Post by kdiggdy on 2007-06-19
Tried that,  the macromedia flash plugin would not let me install it, it wouldent cheack the box i guess it was because of the ubuntu restricted extras i installed

EDIT: Why I can not install that
Macromedia Flash plugin cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by amazingtaters on 2007-06-19
Are you running 64 bit ubuntu? I've heard that there are issues with flash in that version with flash, but there is a work around. I'm off to dinner so I havn't got time to look it up, but try the 64 bit section of the forums.

---

### Post by oilchangeguy on 2007-06-19
and if your not using 7.04 try automatix. [www.getautomatix.com](www.getautomatix.com)

---

### Post by floke on 2007-06-19
AFAIK there is no flash for AMD64 - at least not for Linux - so you're out of luck :(

---

### Post by nutz on 2007-06-19
;)

---

### Post by Spike-X on 2007-06-19
[This should do the trick.]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by kdiggdy on 2007-06-19
> **Spike-X said:**
> [This should do the trick.]("http://ubuntuforums.org/showthread.php?t=476924")
[SIZE="4"]voilà[/SIZE]
Get this man a coffee

---

