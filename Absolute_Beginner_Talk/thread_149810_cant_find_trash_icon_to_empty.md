---
title: "cant find trash icon to empty"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by wolfee on 2006-03-24
please help me empt my trash. I can't find it and I would like to make a desktop icon for it, how?

---

### Post by Jagot on 2006-03-24
Applications -> System Tools -> Configuration Editor.

And then . . .Apps -> Nautilus -> Desktop

Tick the box next to trash_icon_visible

---

### Post by LORD_PoLvO on 2006-03-24
also it in bottom right hand corner of screen

---

### Post by wolfee on 2006-03-24
Thanx!!! My task bar is set for auto hide DUH that's why I couldnt find it!!!!
I have amule which seems slower than limewire for microshaft I CAN"T GET LIMEWIRE FOR LINUX TO WORK!!! I have java platform 2 installed I just got Ubunto yesterday and I want to throw away windows for good!! BUT..... p2p is hard to find,wmv wont play ( most stuff is avi or wmv) how do I make this system work? I am going to put together ubuntu on other computers for my friends but it needs to have all the same qualities that windows has so they dont need to write install commands. I've tried fedora core5, and mandrake 10.2 limited edition and they are ok except for installing software,Ubuntu makes it easy!!!! Pleasehelp me get wmv and avi to work as well as limewire pro

---

### Post by Jagot on 2006-03-24
To get WMV and AVI files to play you can either go the easy route with Automatix:

[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

Or alternatively you can do it manually:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by trent dillman on 2006-03-24
well, how are you trying to make limewire work? is it installing? if not, what errors does it throw? is java in your path (echo $PATH)?

---

### Post by wolfee on 2006-03-24
I went to the link posted and it ran in terminal fine but it does not show up on menu.
I think it downloaded a debian zip file into my home which wont open. ](*,)

---

### Post by Jagot on 2006-03-24
[QUOTE=wolfee]I went to the link posted and it ran in terminal fine but it does not show up on menu.
I think it downloaded a debian zip file into my home which wont open. ](*,)[/QUOTE]

I assume you're talking about automatix?  Providing you follow arnieboy's instructions exactly, it will show up in Applications -> System Tools

[QUOTE=arnieboy]wget [http://beerorkid.com/automatix/automatix_5.7-2_i386.deb](http://beerorkid.com/automatix/automatix_5.7-2_i386.deb)
sudo dpkg -i automatix_5.7-2_i386.deb[/QUOTE]

---

### Post by wolfee on 2006-03-24
i did find it in app sys tools and it toldme to run' winecfg' and then brought up a page with unchecked boxes so i checked win, amule update ect then it ran and a "new update message" came up so i installed all checked boxes and a " one broken file message came up' I dont know what wincfg is I have installed wine on mandrake 10.2 limited addition which was easy (point and click) still no programe to run wmv or avi

---

### Post by Jagot on 2006-03-24
You need to tick for multimedia codecs in automatix.  After it has installed these, WMV and AVI files should just play it the default player Totem, or indeed any other player you care to download.

Alternatively you can also download vlc player through syaptic which pretty much plays most media formats.

winecfg is a command that has to be run after installing the Windows emulator Wine.

---

