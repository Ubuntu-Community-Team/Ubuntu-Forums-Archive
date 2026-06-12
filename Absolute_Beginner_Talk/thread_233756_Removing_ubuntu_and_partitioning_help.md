---
title: "Removing ubuntu and partitioning help"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by j.singh on 2006-08-10
iv donwloaded ubuntu live desktop CD. & bunt the ISO.. and i want to try this out with minimal effect to my pc. 

At the moment im defragging.
I just want to know some information about partitioning as i dont really know much. Could someone explain how ubuntu works with the live CD (desktop)

And finally i was wondering, if i wanted to remove ubuntu from my pc after im done how would i go about this ? is it simple?


Cheers from a future ubuntu user:D

---

### Post by davebgimp on 2006-08-10
The live CD will not affect your hard drive. Booting with it will load Ubuntu, running off your RAM and the CD, no damage to your existing operating system.

If you do decide to install and then want to remove Ubuntu. All you need to do is delete the partitions Ubuntu uses.

---

### Post by cafg10 on 2006-08-10
About removing you can also use the ubuntu LiveCD, it has a partition manager, wich can easily remove your ubuntu partitions, however, it **will not remove the bootloader** that ubuntu installs, so you need to reinstall you previous OS bootloader as the default, if you neeed some more help don't hesitate to contact me

---

### Post by j.singh on 2006-08-10
thnx for the relpy,,

but how come i read in this guide that it partitions

[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by John.Michael.Kane on 2006-08-10
j.singh what that is in reguards to is the alternate install. since all you will be using is the live version that cd does not remove or partion your disk until you click the install icon which will be on your destop.should you find that ubuntu fits your need's. you can use the live-cd for installing ubuntu as well.

---

### Post by j.singh on 2006-08-10
Soo how would i do that?... boot the live cd from the start or from windows?

Whats the difference between the alternate install and the live cd since you can install from the live cd?..

---

### Post by nalmeth on 2006-08-10
The liveCD install is a new feature, and isn't perfect yet. Some people have problems with the partitioning process, and having the installer crash.

The alternate install is rock stable, but less pretty, and doesn't include the live system to check hardware compatibility. 

For what it's worth, I've only had 2/5 liveCD installs fail, and one of them was because my laptop didn't have enough ram to handle the installer (requires 256 megs)

EDIT:
To boot the CD, throw it in the drive and reboot the computer
Yes the installer will use a partitioner. Hopefully you've backed up data for better/worse, and good call on the defrag. You've done your homework

---

### Post by j.singh on 2006-08-10
> **SD-Plissken said:**
> j.singh what that is in reguards to is the alternate install. since all you will be using is the live version that cd does not remove or partion your disk until you click the install icon which will be on your destop.should you find that ubuntu fits your need's. you can use the live-cd for installing ubuntu as well.

mmh im a tad confused now.

You say that it doesnt need to partition anything 
yet nalmeth says it does...

at the moment i want to try it out without any effect.

---

### Post by Greycloak on 2006-08-10
If you run the CD just as a live cd, no partitioning is necessary.  If you want to install it you will need to have a partition set aside for Ubuntu, unless you don't mind losing your windows partition.

If you set aside a partition for Ubuntu you can dual-boot your system.  This way you have a choice at start up whether to run Windows or Ubuntu.

---

### Post by tehnad on 2006-08-10
Look at it like this.  A live CD means that no HD is needed to run.  It has everything that it needs right on the disk.  You restart the computer with the live disk in the drive and have your boot option sin the Bios set to boot form CD.  This will boot you into your live disk which only loads into ram and nothing else.

     If you decide to install Ubuntu then you can go to the system tab, go to administration, then go to gnome partition editor and build a new linux partition.  After going this and saving the new partition you can click the install icon on your desktop which will install Ubuntu into your new space.  Don't worry about the menu.lst file when doing this either because Ubuntu will rewrite it for you if you already have Windows installed.

---

### Post by John.Michael.Kane on 2006-08-10
j.singh i was simply saying that the live-cd does not install on your hdd untill you click the install icon which will be an option on your desktop.

---

### Post by j.singh on 2006-08-10
ok .. thanks for your help guys...

on average how long does it take to boot the live cd (without HDD partitioning?)

---

### Post by Jagot on 2006-08-10
> **j.singh said:**
> on average how long does it take to boot the live cd (without HDD partitioning?)

Shouldn't be longer than 5 minutes providing your system isn't ancient.

---

### Post by j.singh on 2006-08-10
OK..so i just reboot my pc with the live CD in and boot from disk and press "start or install" i think it was???

---

### Post by Jagot on 2006-08-10
If you're using the live cd then you should just need to select 'Start Ubuntu':

[IMG]http://img133.imageshack.us/img133/694/w2u185fs.png[/IMG]

---

### Post by j.singh on 2006-08-10
ok. iv got the desktop iso.and the first option is "start or run"i think.  Anyway the splash screen does its thing, & i think my CD drive is clicking loudly. then it trys 2 uncompress linux,then "time out waiting for DMA' help! cud som1 point me in the direction of the liveCD which has small effect on my pc, cheers

---

