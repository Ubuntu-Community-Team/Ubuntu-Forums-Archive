---
title: "How Do You Dual Boot Windows XP and Ubuntu Linux?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by Nut on 2006-10-04
It's all in the title...

I'm going to Google it, but, while I Google it I thought I would make a thread.

---

### Post by Drakkor on 2006-10-04
Install XP first,then install Ubuntu,it will boot by default to Ubuntu,but you have the option to select XP on booting.

---

### Post by Sef on 2006-10-04
Read this exellent tutorial on how to [dual boot.]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Nut on 2006-10-04
But say at any time I wanted to go to Windows XP, how would I do it? Also, won't it erase my hard drive during the installation of Ubuntu?

---

### Post by Drakkor on 2006-10-04
Not if you install Ubuntu on a seperate partition,are you using one or two hard drives ?

---

### Post by Kateikyoushi on 2006-10-04
Ubuntu installs a boot loader on your computer so at start up you can choose which OS to load. It is also able to resize your existing partitions so it won't overwrite anything, in case you tell it not to.

---

### Post by Nut on 2006-10-05
Problem... The XP partition takes up my whole hard drive, and it can't identify it nor change it's size so I can add a partition for Linux.

Help!

---

### Post by toddr on 2006-10-05
Check ou this site. I've used it on my laptop and my desktop and it worked great on both.[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

---

### Post by Nut on 2006-10-05
Ok, well, I understand how to do it, that's not my problem. Did you read my previous post?

---

### Post by Gioutsaman on 2006-10-05
i think gparted can resize the partitions. You can download it, there is a separate distribution gparted live cd, run the cd from boot , change the partitions and then reboot so that u can install ubuntu. But since you are a windows user u could use partition magic to resize your partition...then install ubuntu and no more windows :D

---

### Post by toddr on 2006-10-05
On that web site it describes what you must do to fix this problem. You have to run disk defragmenter to resize your windows partition

---

### Post by toddr on 2006-10-05
There is a distro that you run from a cd that has qtparted on it. It is called system rescue.

---

### Post by gn2 on 2006-10-05
Ask dyourself do you really want to dual boot.

If you don't play games and have hardware which is up to it (lots of RAM), I would suggest you install Ubuntu, then use VMWare Server to install Windoze.

VMWare server Creates a large folder which it uses as a Virtual hard drive where you can istall another OS, it's not without it's problems, but then neither is Dual Booting.

You can now run both Operating systems at the same time.....

---

### Post by Nut on 2006-10-05
> **Gioutsaman said:**
> i think gparted can resize the partitions. You can download it, there is a separate distribution gparted live cd, run the cd from boot , change the partitions and then reboot so that u can install ubuntu. But since you are a windows user u could use partition magic to resize your partition...then install ubuntu and no more windows :D

It can't... For some reason it won't allow it to be changed at all. I've already tried that. I'm not exactly, a Windows user, because I'm installing Linux, I mean, think about it. Plus, I'm just doing this so other members of my family can use Windows when needed.

---

### Post by Nut on 2006-10-05
> **gn2 said:**
> Ask dyourself do you really want to dual boot.

If you don't play games and have hardware which is up to it (lots of RAM), I would suggest you install Ubuntu, then use VMWare Server to install Windoze.

VMWare server Creates a large folder which it uses as a Virtual hard drive where you can istall another OS, it's not without it's problems, but then neither is Dual Booting.

You can now run both Operating systems at the same time.....

Yeah, but, my problem is when I install Ubuntu I have nowhere to go to get help with my not working network adapter... I need help with installing ndiswrapper.

So, could you help me with ndiswrapper?

---

### Post by Gioutsaman on 2006-10-05
hehe i meant since u are a windows user for the time being :D. sorry if i offended you :D....if you cannot do it with qgarted try partition magic......

---

### Post by gn2 on 2006-10-05
Is that a wireless network adapter, what make/model and what's the chipset?

---

### Post by Nut on 2006-10-05
Linksys Wireless-G USB Adapter... (External.)

---

### Post by toddr on 2006-10-05
When I resized my windows partition, I had to run the defragmenter 7 or 8 times to get it down to the right size.

---

### Post by Nut on 2006-10-05
I don't even know what that is or what it does...

Could you give me a link to download it? Or a manual or something?

---

### Post by gn2 on 2006-10-05
> **Nut said:**
> Linksys Wireless-G USB Adapter... (External.)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

You should find the solutions in the above links, you need to know the exact model of USB adapter and chipset?

I found this page which also may help: [http://www.linuxquestions.org/questions/showthread.php?t=462105](http://www.linuxquestions.org/questions/showthread.php?t=462105)

---

### Post by Gioutsaman on 2006-10-05
here is the trial....[http://www.soft32.com/download_151.html](http://www.soft32.com/download_151.html)
i hope this helps!

---

