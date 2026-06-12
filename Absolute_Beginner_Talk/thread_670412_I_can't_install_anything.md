---
title: "I can't install anything"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by takeitback on 2008-01-17
any time I use the command "sudo apt-get" with anything but updates I get "E: Couldn't find"  I've tried installing beryl, linux-686-smp, compiz (although I think updates at least downloaded compiz) and I get the same thing every time.  I'm running ubuntu 7.10. I can't get the option of Desktop Effects in my preferences. or the option of Custom in the visual effects tab of the Appearance dialog box.
Here's my computer set up:

bfg 680i motherboard
intel quad core processor
4 gb of kingston hyper x pc-8500 ram
nvidea geforce 8500 and 7600 graphics cards
and over a tb of hard drive space.

I'm also multi booting to windows xp and server 2003 enterprise as well...

please help. I could use any advice I can get as of now.

---

### Post by oldb0y on 2008-01-17
You must update your repos, System>Adminstration>Settings>Repos 
Check of everything on the first page, and then update your Synaptic.

---

### Post by FuturePilot on 2008-01-17
Go System>Administration>Software Sources and make sure all the boxes are checked in the first tab. Also uncheck the one for the CD-ROM if it's checked. Then go to the Updates tab and check the first two and optionally the fourth one. Hit Close then Reload the sources when prompted. Also Beryl is no longer in the repos because Beryl has been merged into Compiz Fusion.

---

### Post by Nano Geek on 2008-01-17
To install programs, you run:```
sudo apt-get install <program name>
```However, Beryl is not in the repositories since it has merged with Compiz now.

Most programs you want can be installed from **Applicatins=>Add/Remove...**
Desktop-Effects is a different name for Compiz, and to run it you have to install the closed-source Nvidia driver which can also be found in **Add/Remove...**

Enjoy using Ubuntu.

EDIT: Three posts in one minute: amazing.

---

### Post by J0henz on 2008-01-17
Have you installed clamav? I did that and it caused the same problem for me, I just uninstalled it and everthing was fine.
To uninstall clamav type **sudo apt-get autoremove clamav** in the terminal.

---

### Post by svalding on 2008-01-17
It's interesting you are getting the "E: Could not find" message. Seems like a drive path to me, and that would most certainly not be what ubuntu calls a cdrom drive. Tell me, do you have Wine installed? It could be confusing a path to a virtualized cd-rom drive. Also, edit /etc/apt/sources.list and comment out all lines referencing a cd-rom drive. That way it only pulls from online sources.

---

### Post by nikoPSK on 2008-01-17
to learn more about managing software, look here:
[http://ubuntuforums.org/showthread.php?t=644478](http://ubuntuforums.org/showthread.php?t=644478)

nikoPSK

---

### Post by RebounD11 on 2008-01-17
> **svalding said:**
> It's interesting you are getting the "E: Could not find" message. Seems like a drive path to me, and that would most certainly not be what ubuntu calls a cdrom drive. Tell me, do you have Wine installed? It could be confusing a path to a virtualized cd-rom drive. Also, edit /etc/apt/sources.list and comment out all lines referencing a cd-rom drive. That way it only pulls from online sources.

I think E: comes from Error not the CD-ROM drive. Apt-get has nothing to do with Wine and that's not the way Linux names partitions.

PS: I thought the same thing when I came from Windows and my sister laughed at me so hard ... :)

---

