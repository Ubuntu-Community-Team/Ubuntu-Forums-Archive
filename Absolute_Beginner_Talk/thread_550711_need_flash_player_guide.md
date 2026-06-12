---
title: "need flash player guide"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-09-14
Hi I need to install flash player for firefox . I'm completely new to linux a guide on how to get it installed would be very helpful
cheers

---

### Post by philinux on 2007-09-14
Goto System>Administration>Synaptic Package Manager.

Use the search for flash and you will see a package named flashplugin-nonfree. Mark it for installation then click apply.

---

### Post by bigmonmulgrew on 2007-09-14
It says that I cannot install on my hardware (amd64)

---

### Post by overdrank on 2007-09-14
> **bigmonmulgrew said:**
> It says that I cannot install on my hardware (amd64)

Maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

---

### Post by philinux on 2007-09-14
You could try Gnash its another flash plugin. Its further down the list.

free Flash movie player
Gnash is a free Flash movie player, which works either standalone, or as
plugin for Firefox/Mozilla

---

### Post by Dan-O on 2007-09-14
heya Big

I fought with this for quite some time...even had a cry thread last night cause I couldn't get Flash 9 to work with 64-bit.

Bottom line is, Adobe hasn't put out a 64-bit version of Flash 9 and there doesn't seem to be any backward compatability with the older versions of Flash.

I finally gave in and loaded 32-bit Ubuntu and Kubuntu on my 64-bit machines.  Everything is working flawlessly.

I may have licked the lollipop of mediocrity by not staying the 64-bit course and trying to get something working but, I wanted to see something besides my desktop work.

In the end, the choice is yours.  As someone suggested to me, ask Adobe to get off their duff and put out a 64-bit Linux version of Flash 9.

Dan-O

---

### Post by The Populist on 2007-09-15
I found a thread that had the beta version of a 64 bit flash player. It was great, I didnt have to use command line or anything, just download, and click "run in terminal". My flash player worked for about two weeks, now it wont play any movies. 

Is there a reliable 64 bit flash player on this site? I really dont want to uninstall 64 bit ubuntu and install 32 bit ubuntu/flash. I'm running a vista machine and I really hate M$. 

...

---

### Post by philinux on 2007-09-15
Get the 32 bit flash .deb package and then use
```
sudo dpkg -i --force-architecture packagename.deb

```

---

### Post by marco123 on 2007-09-15
> **The Populist said:**
> I found a thread that had the beta version of a 64 bit flash player. It was great, I didnt have to use command line or anything, just download, and click "run in terminal". My flash player worked for about two weeks, now it wont play any movies. 

Is there a reliable 64 bit flash player on this site? I really dont want to uninstall 64 bit ubuntu and install 32 bit ubuntu/flash. I'm running a vista machine and I really hate M$. 

...

There's a simple script which does it for you here: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924) :)

---

### Post by rayj00 on 2007-09-15
> **philinux said:**
> Goto System>Administration>Synaptic Package Manager.

Use the search for flash and you will see a package named flashplugin-nonfree. Mark it for installation then click apply.

I've tried this twice but both time I get:

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Any ideas?

Thanks

Ray

---

