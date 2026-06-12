---
title: "VMWare ... instructions???"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by verby on 2007-03-19
Can you point me to VMWare - how to?
I installed VMWare, but how do I run win programs under this?
I have my second partition with win xp.
any step by step instructions how to set it up?
thnx

---

### Post by dfreer on 2007-03-19
Which VMWare are you using, Vmware Player, Workstation, or Server? The Vmware site has some pretty good how-to's ([http://www.vmware.com)](http://www.vmware.com)), as does [*_ubuntuguide.org_*]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29").

Note: You can only have one vmware product installed at a time, if you try to install a new one without completely uninstalling the old one it hoses things up. Also, it is best to run each OS (Ubuntu, Windows) on seperate hard drives. If you don't you'll have some major I/O requests, and in all likely-hood result in premature hard drive failure.

Although the default way is to install windows WITH vmware, it sounds like you can run an existing windows partition. Here's some links:
Using VMWare Player: [http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)
[http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)

---

### Post by charles.g.moore on 2007-03-19
After you install VMWare just fire it up and then you can install a new virtual machine, either through an .iso or from the installation CD's
As far as seeing a partition on your HDD im not sure it works that way.  There has to be a way i'm just not saavy enough to tell you.

Is that what you want to do?  Grab some info from your Windows partition?

---

### Post by oilchangeguy on 2007-03-19
as far as i know you can't run a program without an operating system. so you'll need to load an operating system on vmware to be able to run the programs. and for windows based software, that of course means loading a legal copy of windows on vmware.

---

### Post by dfreer on 2007-03-19
VMWare Player Install:
```
sudo aptitude install vmware-player
```

Step by Step VMWare Server Install:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Virtual_Machine_Manager_.28VMware_Server.29)
[http://www.ubuntuforums.org/showthread.php?t=183209](http://www.ubuntuforums.org/showthread.php?t=183209)

---

### Post by mills on 2007-03-19
that second link dfreer posted is the howto i've just used to install vmware 

works perfectly!!!

---

### Post by verby on 2007-03-19
I'm trying to run ms office 2007 (which doesn't install under wine). Someone suggested vmware. is it going to work?

---

### Post by jkeyes0 on 2007-03-19
Vmware will allow you to run a full install of Windows in a virtual layer within Linux. It's basically a machine within a machine. Thereby you can run your windows applications, in windows, but still be running Linux on the outside. It's more of a bandage than a solution, in my opinion.

Are you unsatisfied with OpenOffice.org?

---

### Post by oilchangeguy on 2007-03-19
not unless you load win xp sp2, or vista. vm ware=virtual machine, not virtual software player. meaning it needs an operating system in order to work.

---

### Post by dfreer on 2007-03-19
So basically, yes you can run MS Office 2007. As long as you have (1) a valid copy of windows (2) a valid copy of MS Office 2007. If your windows partition already had windows and MS Office installed, it should run fine.

---

### Post by tux_rox on 2007-03-19
Do you still need to make a Windows partition in your hard drive(s) if you're using VMWare, or is VMWare completely "shut off" from the rest of your computer?

---

### Post by verby on 2007-03-19
I do have original discs (from work)
we do lots of  document/mail margin (excel-word) which oo doesn't handle too good.

> **oilchangeguy said:**
> not unless you load win xp sp2, or vista. vm ware=virtual machine, not virtual software player. meaning it needs an operating system in order to work.

---

### Post by charles.g.moore on 2007-03-20
> **tux_rox said:**
> Do you still need to make a Windows partition in your hard drive(s) if you're using VMWare, or is VMWare completely "shut off" from the rest of your computer?

There is no need for a partition on your HDD, the XP OS would actually be a file in your linux filesystem, it will have an extension .vmx

The neat thing is if you hose your XP OS all you have to do is delete the .vmx and re-install.
I guess you could back up your .vmx but it is pretty large.

One thing to consider, when you are installing a new virtual machine you can split the file into 2GB partitions and uncheck the "allocate all 8GB now" box so your file will grow in 2Gb increments only as you need it...

---

