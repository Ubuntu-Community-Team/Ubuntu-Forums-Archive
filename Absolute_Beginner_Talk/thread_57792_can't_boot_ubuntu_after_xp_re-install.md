---
title: "can't boot ubuntu after xp re-install"
date: 2005-08-17
forum: Absolute Beginner Talk
---

### Post by Abandonallhope on 2005-08-17
[SIZE=1]hi guys - installed ubuntu, it looked OK, even though I didn't have a clue how to operate linux (couldn't even install a flash plugin for firefox!!!), but vowed that I would learn how to use it --- anyway, then desaster struck, I had to reinstall XP after tinkering with my hardware and now it boots straight into windows - what can I do to get the dual boot back?? (preferably to go to XP by default, but at least give me the option to select ubuntu) -- any advice will be greatly appreciated, but please bear in mind, that I have absolutely no linux knowledge whatsoever *I'm pretty nifty with hardware and also still remember a good bit of DOS, but thats of no help to me right now) - this old dog needs to learn a few new tricks - please help and be patient!!  :? [/SIZE]

---

### Post by Buffalo Soldier on 2005-08-17
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

---

### Post by Brunellus on 2005-08-17
[QUOTE=Abandonallhope][SIZE=1]hi guys - installed ubuntu, it looked OK, even though I didn't have a clue how to operate linux (couldn't even install a flash plugin for firefox!!!), but vowed that I would learn how to use it --- anyway, then desaster struck, I had to reinstall XP after tinkering with my hardware and now it boots straight into windows - what can I do to get the dual boot back?? (preferably to go to XP by default, but at least give me the option to select ubuntu) -- any advice will be greatly appreciated, but please bear in mind, that I have absolutely no linux knowledge whatsoever *I'm pretty nifty with hardware and also still remember a good bit of DOS, but thats of no help to me right now) - this old dog needs to learn a few new tricks - please help and be patient!!  :? [/SIZE][/QUOTE]
 winXP hoses the Master Boot Record like a jihadi on PCP.  There is no OS but Windows, and Bill Gates its Prophet.....

But this thread might have some clues

[http://ubuntuforums.org/showthread.php?t=42523&highlight=dual-boot+windows+bootloader](http://ubuntuforums.org/showthread.php?t=42523&highlight=dual-boot+windows+bootloader)

---

### Post by Brunellus on 2005-08-17
[QUOTE=Brunellus]winXP hoses the Master Boot Record like a jihadi on PCP.  There is no OS but Windows, and Bill Gates its Prophet.....

But this thread might have some clues

[http://ubuntuforums.org/showthread.php?t=42523&highlight=dual-boot+windows+bootloader](http://ubuntuforums.org/showthread.php?t=42523&highlight=dual-boot+windows+bootloader)[/QUOTE]
 or this:
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

---

### Post by Abandonallhope on 2005-08-18
[QUOTE=Buffalo Soldier][http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)[/QUOTE]
 Thanks for ur reply Buffalo Soldier - but unfortunately the probably interesting part of that thread is all greyed out for me and I cant read it

---

### Post by Abandonallhope on 2005-08-18
[QUOTE=Brunellus]or this:
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)[/QUOTE]
 Thanks for ur help Brunellus - that looks promising (doable even for a not-yet linux guy like me) - I'll let u know how I got on!!

---

### Post by Buffalo Soldier on 2005-08-18
[QUOTE=Abandonallhope]Thanks for ur reply Buffalo Soldier - but unfortunately the probably interesting part of that thread is all greyed out for me and I cant read it[/QUOTE]I will copy and paste the instructions here.

**[General Notes](http://ubuntuguide.org/#generalnotes)**
[list=1]
[*] This is an Unofficial Ubuntu 5.04 Starter Guide. It is not associated with Ubuntu and Canonical Ltd.
[*] Guide is tested on a full installation of the Ubuntu 5.04 x86 Install CD (Hoary Hedgehog)
[*] If you see black box, means you have to execute the commands in Terminal mode (Applications -> System Tools -> Terminal)
[*] To reduce typo mistakes, copy and paste the commands into Terminal mode (right click on the commands -> "Copy" or "Paste")
[*] "sudo" means superuser do. "sudo" will prompt for "Password:". Please specify user password
[*] If you are tired of typing "sudo" all the time, switch to root user by issuing "sudo -s -H" followed by user password
[*] If you are tired of typing "apt-get" all the time, Read [How to apt-get the easy way (Synaptic)?](http://ubuntuguide.org/#synaptic)
[*] "apt-get" and "wget" requires Internet connection to install/update/download programs
[*] To download file, right click on the link -> Select "Save Link As..." -> Make sure file name and extension are correct
[*] Some multimedia applications may not load/produce sound, Read [How to configure sound to work properly in GNOME?](http://ubuntuguide.org/#configuresoundproperly)
[*] For any feedbacks, suggestions, discussions and bugs report to the author, please post comments: [Here](http://ubuntuforums.org/showthread.php?p=112654)
[*] May the "humanity to others" spirit be with you always...
[/list]

**[Q: How to use Ubuntu Installation CD, to gain root user access?](http://ubuntuguide.org/#gainrootinstallcd)**
[list=1]
[*] Read [General Notes](http://ubuntuguide.org/#generalnotes)
[*] Boot-up computer into Ubuntu Installation CD
[*] At "boot:" prompt, add "rescue" to the argument```

boot: rescue
```
[*] Follow the instructions on screen
[/list]

**[Q: How to restore GRUB menu after Windows installation?](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)**
[list=1]
[*] Read [General Notes](http://ubuntuguide.org/#generalnotes)
[*] Read [How to use Ubuntu Installation CD](http://ubuntuguide.org/#gainrootinstallcd), to gain root user access?
[*] e.g. Assumed that /dev/hda is the location of /boot partition
[*] ```
# grub-install /dev/hda
```
[/list]

---

