---
title: "Speeding up Linux, BUM InitNG Prelinking - need help"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-24
I know how to use BUM, I'm pretty sure which things I want to disable.  I'm going to try this: [http://ubuntuforums.org/showthread.php?t=89491&highlight=boot-up+manager](http://ubuntuforums.org/showthread.php?t=89491&highlight=boot-up+manager) and speed up the internet with this: [http://ubuntuforums.org/showthread.php?t=202838&highlight=speed](http://ubuntuforums.org/showthread.php?t=202838&highlight=speed) firefox with this: [http://ubuntuforums.org/showthread.php?t=179540&highlight=speed](http://ubuntuforums.org/showthread.php?t=179540&highlight=speed).  Are these good idea?

What I want to know is how to use InitNG, and what exactly it's for.  

I've gotten some info on prelinking: [http://kudos.berlios.de/kf/kisimlar/tipsntrix.html#prelink](http://kudos.berlios.de/kf/kisimlar/tipsntrix.html#prelink), but it doesn't explain it very well. 

Hw to stop samba, and other applications that I don't need (and which applications I don't need)  

How to completely disable sound, my Dell Latitude has faulty Neomagic audio controlers anyway, and I use it for homework, I don't needsound.

Other ways to speed up linux, thanks!

---

### Post by siccness on 2006-06-24
Well, im my experiance, I didn't notice any difference with prelinking. Others have noticed improvement, others haven't. I'll see if I can find the guide to prelinking for you.

Edit: [http://bin-false.org/?p=10](http://bin-false.org/?p=10)

---

### Post by WADemosthenes on 2006-06-24
[QUOTE=siccness]Well, im my experiance, I didn't notice any difference with prelinking. Others have noticed improvement, others haven't. I'll see if I can find the guide to prelinking for you.

Edit: [http://bin-false.org/?p=10](http://bin-false.org/?p=10)[/QUOTE]

If you didn't notice much, I'll pass on the prelinking, it seems risky.  However, I have many other things I want to try.

Edit: is there any way to comment out the modules that load for sound in a text file somewhere?

---

### Post by WADemosthenes on 2006-06-25
I found this site: [http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=2](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=2)

I ran the cammand: hdparm -c3 -m16 /dev/hda, suppose change the multicount to 16, then the cammand: hdparm -X34 -d1 -u1 /dev/hda, that one didn't work, and then: hdparm -X66 -d1 -u1 -m16 -c3 /dev/hda, which didn't work either.  How can I get them to work?

---

### Post by siccness on 2006-06-25
What error output?

---

### Post by WADemosthenes on 2006-06-25
[QUOTE=siccness]What error output?[/QUOTE]

Says:
> hdparm - get/set hard disk parameters - version v6.3

Usage:  hdparm  [options] [device] ..

Options:
 -a   get/set fs readahead
 -A   set drive read-lookahead flag (0/1)
 -b   get/set bus state (0 == off, 1 == on, 2 == tristate)
 -B   set Advanced Power Management setting (1-255)
 -c   get/set IDE 32-bit IO setting
 -C   check IDE power mode status
 ...(yada yada)
 --security-help  display help for ATA security commands

I'm not sure what that means, but I'm pretty sure it didn't do anything.

---

### Post by siccness on 2006-06-25
I presume that output is actually just telling you how to correct use hdparm and it's paramaters. I'm not entirely sure what parameter is incorrect though.

---

### Post by WADemosthenes on 2006-06-25
[QUOTE=siccness]I presume that output is actually just telling you how to correct use hdparm and it's paramaters. I'm not entirely sure what parameter is incorrect though.[/QUOTE]

From another site I tried: sudo hdparm -d1 -c1 -m16 /dev/hda, which seemed to turn everything on that I needed.  Now how else can I speed up my computer?

---

### Post by siccness on 2006-06-25
I'm not real sure if Ubuntu is the perfect Linux Distribution for high-performance. Gentoo is well renowned for that.

---

### Post by WADemosthenes on 2006-06-25
[QUOTE=siccness]I'm not real sure if Ubuntu is the perfect Linux Distribution for high-performance. Gentoo is well renowned for that.[/QUOTE]

Is Gentoo similar to ubuntu or even debian?

Anyway, I a program to take modules out of the boot proccess, then used the hdparm trick, then sped up the internet with some trick, then firefox with some about:config editing.  It's much faster than before.

---

