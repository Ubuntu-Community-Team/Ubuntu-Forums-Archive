---
title: "Breezy loading into CLI"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-10-23
Upgraded to breezy, but upon reboot, I can only get the CLI.  I followed the wiki as to how to upgrade, but mine was unsucsessfull. I did a "dpkg-reconfigure xserver-xorg" and then "/etc/init.d/gdm restart. But still nothing happening. Even after reboot, I still can't get it working. I always get the "cannot open display" problem. My initial Ubuntu install, gave me similair problems, but up to now, my old tricks did not help.

Any idea what to do.

---

### Post by Kapre on 2005-10-23
[QUOTE=GrootBrak]Upgraded to breezy, but upon reboot, I can only get the CLI.  I followed the wiki as to how to upgrade, but mine was unsucsessfull. I did a "dpkg-reconfigure xserver-xorg" and then "/etc/init.d/gdm restart. But still nothing happening. Even after reboot, I still can't get it working. I always get the "cannot open display" problem. My initial Ubuntu install, gave me similair problems, but up to now, my old tricks did not help.

Any idea what to do.[/QUOTE]

Grootbrak - what would typing "startx" return?

---

### Post by GrootBrak on 2005-10-23
[QUOTE=Kapre]Grootbrak - what would typing "startx" return?[/QUOTE]

Complaints about fonts and things I need to check if I'm an inexperienced user. The last file is a complaint of a fatal error.

---

### Post by GrootBrak on 2005-10-24
Just an update. I loaded some new files, but it still goes into CLI and asks me to configure Xserver. As I did this for a few different options, I still can't get it working. 

The command startx tries to bringup a GUI now, but its really scrambled and it flickers a couple of times, before going back to CLI. 

At least I can "pon" and download files with apt-get. Please anyone?

---

### Post by heimo on 2005-10-24
Try reconfiguring again, but this time select vesa driver and include low resolutions like 640x460,800x600 and 1024x768. (these have better chance of working) What graphics card do you use? And what kind of monitor do you have? This is either graphics driver issue or resolution/refresh rate issue.

These instructions may be helpful:
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by GrootBrak on 2005-10-24
Thanx, Done it, and followed the links you provided. I remembered using those when I first set up Ubuntu warty months ago. I upgraded to Hoary with no hassles, and now Breezy come and bite me!!! 
Some hardware info. I use and Intel915 onboard graphics driver and a Samsung Syncmaster 793s.

---

### Post by GrootBrak on 2005-10-25
After I downloaded fonts as suggested after I tried to do a "startx" I rebooted because my PC hanged. After that X came back on. Icons etc. look new, but "About Gnome" still shows I'm using Haory. I've checked my repos and noticed that I have both Hoary and Breezy security updates active. Don't know if that caused my problems. 

As for most things, I doubt if my real problem is solved. Any help or suggestions.

---

### Post by heimo on 2005-10-25
Check the sources.list / repositories and do:
[LIST]
[*]sudo apt-get update   
[*]sudo apt-get dist-upgrade (just to make sure it went through nicely)   
[*]sudo dpkg --configure -a (to make sure every package is configured) [/LIST]

---

