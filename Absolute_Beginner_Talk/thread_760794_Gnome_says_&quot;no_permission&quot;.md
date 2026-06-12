---
title: "Gnome says &quot;no permission&quot;"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-04-20
Using the Gnome file manager, in a LiveCD session, it shows some folders in /home as locked. That is, to the upper right side of several folder icons, there is an orange circle with what appears to be an X in the circle.

From the command line, is there a chown command that will change ALL  the permissions to my user name: mark simultaneously?

---

### Post by SunnyRabbiera on 2008-04-20
you know how a live CD works right???

---

### Post by Mark_in_Hollywood on 2008-04-20
> **SunnyRabbiera said:**
> you know how a live CD works right???

This non-response response isn't useful. I guess you think I post questions to take the time of other people's lives for nothing.

But for the record: I have no idea of how a live CD works, WRONG!

---

### Post by twist2b on 2008-04-20
it should still work though. Open nautilus with terminal through this:

gtku nautilus


I think its gtku I always forget. ANYWAYS you need to open it as root (admin)

Then direct to the partition and open. You can do w/e you want after that.

---

### Post by SunnyRabbiera on 2008-04-20
> **Mark_in_Hollywood said:**
> This non-response response isn't useful. I guess you think I post questions to take the time of other people's lives for nothing.

But for the record: I have no idea of how a live CD works, WRONG!


Nono, I was just inquiring on your knowledge not being smart or anything.
As for the subject the Live CD is actually more or less like a virtual session/OS, it is not really meant to be a OS on its own.
What you were trying to do was use the OS off the live like your main OS, yes you can probably edit some files with the Live but the rest of it is virtual and not intended to act like a real install.
have you actually done a full install?
I am just wondering as I am not sure on how experienced/knowledgeable you are

---

### Post by Oldsoldier2003 on 2008-04-20
> **twist2b said:**
> it should still work though. Open nautilus with terminal through this:

gtku nautilus


I think its gtku I always forget. ANYWAYS you need to open it as root (admin)

Then direct to the partition and open. You can do w/e you want after that.

gksu or gksudo

---

### Post by Joeb454 on 2008-04-20
> **twist2b said:**
> it should still work though. Open nautilus with terminal through this:

gtku nautilus


No not quite.

It's the following from a terminal ```
gksu nautilus
``` :) Though it should be noted that gksudo also works :)

---

### Post by Mark_in_Hollywood on 2008-04-20
it should still work though. Open nautilus with terminal through this:
gtku nautilus

I think its gtku I always forget. ANYWAYS you need to open it as root (admin)

Then direct to the partition and open. You can do w/e you want after that.

I believe the command is 

Alt-F2

gksudo nautilus

at least, I believe I've got it working that way

At the moment, the LiveCD is copying about 14 gig off the 320 gig primary master over the the external usb drive.

All are required to keep their fingers crossed, please.

---

### Post by vanadium on 2008-04-20
In a life CD session, you are not logged in as a regular user. Thus it might be that some directories are locked. Use root permissions only when you know what you are doing. Otherwise, just boot the machine normally.

---

### Post by bwallum on 2008-04-20
You can access as root with
```
gksudo nautilus
```

Mark, you have your bean count hidden so it is difficult to know at what level you are at. However if you are unsure how the live CD works then I will try to help as though you are a beginner.

At the top of the desktop choose the Applications menu, then Accessories then Terminal. We tend to use something like Applications>Accessories>Terminal to indicate the navigation.

When you have a terminal open type in the code highlighted above. You will be presented with all files on your PC. The filesystem you are running is the one generated from your live cd and now held in memory. You will see your harddrive. It may be labelled something like XX.X GB Media. You can click on this item and it will give you access to the files on that media.

May I ask your intent? Do you want to install a Ubuntu OS onto your harddrive? Do you want to keep your old OS for now?

---

### Post by Mark_in_Hollywood on 2008-04-20
Disk /dev/sde: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062756

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        4982    40017883+  83  Linux

So I think I've got a 40gig drive, as: primary partition and ext3 filesystem, but when I try to copy my /home folder (about 20 gig) to the 40 gig, I get an error about "insufficient space"

anybody got some ideas?

---

### Post by bwallum on 2008-04-20
If you are still using the live cd then you have run out of space for the live OS to copy 20 gig.

Why can't you boot up with the hard drive Ubuntu? (which you appear to have given that your home folder has 20 gig in it.)

Extra foam sugar free Ubuntu seems to indicate you are quite experienced. You could help us a little bit I think.

---

### Post by Mark_in_Hollywood on 2008-04-20
In trying Psychocat's how-to for putting /home in it's own partition, I blew up the 320 gig drive. I'm trying to back up all my files to an external usb drive. Then, per others at this forum I'm going to, from a LiveCD with the 320 gig unmounted, do 

fsck

which will be the first time I've ever done that.

As for what you said, I'm now trying to copy one folder at a time, while in the LIveCD session from /home to the usb drive. Some folders are copying just fine, others are saying 

[B]Error while copying to: "media/usbdrive"

There is not enough space on the destination[/B]

which isn't exactly true, as the 40 gig drive has about: 433 MEG on it at the moment.

---

### Post by Joeb454 on 2008-04-20
> **bwallum said:**
> Mark, you have your bean count hidden so it is difficult to know at what level you are at. However if you are unsure how the live CD works then I will try to help as though you are a beginner.


Not true, you can view his forum profile page, and it will tell you on there :)

Also Bean Count isn't a way of knowing how knowledgeable a user is. Many experienced users lurk about these forums but may have only recently signed up :)

---

### Post by Oldsoldier2003 on 2008-04-20
> **bwallum said:**
> You can access as root with
```
gksudo nautilus
```

**Mark, you have your bean count hidden so it is difficult to know at what level you are at. However if you are unsure how the live CD works then I will try to help as though you are a beginner.**

At the top of the desktop choose the Applications menu, then Accessories then Terminal. We tend to use something like Applications>Accessories>Terminal to indicate the navigation.

When you have a terminal open type in the code highlighted above. You will be presented with all files on your PC. The filesystem you are running is the one generated from your live cd and now held in memory. You will see your harddrive. It may be labelled something like XX.X GB Media. You can click on this item and it will give you access to the files on that media.

May I ask your intent? Do you want to install a Ubuntu OS onto your harddrive? Do you want to keep your old OS for now?

just so you know, if you're curious about bean count and a user has their count hidden, all you have to do is look at their profile and post count is listed. That is why I don't bother to hide my beancount...

---

### Post by Frak on 2008-04-20
In any case, to change the ownership of a directory, run:

```
sudo chown -R $USER <directory here>
```

to change the ownership of, not only the folder, but all the files within that, recursively.

---

### Post by Mark_in_Hollywood on 2008-04-20
> **Oldsoldier2003 said:**
> just so you know, if you're curious about bean count and a user has their count hidden, all you have to do is look at their profile and post count is listed. That is why I don't bother to hide my beancount...

Frankly, guys, I'm confused. I need some (a little help) with saving my documents or folders. I'm here for the technology. Not philosophy.

I hide my bean count to try to discourage people from looking at it and thinking I know much. When I first installed Ubuntu I had a internal dial-up modem. I must have 100 posts about trying to get that device alone to work. I'm not a software guy, I write cookbooks for a living. I have no idea of what I'm doing most of the time, which shows the power of Linux "it just works".

PLEASE -- if you can help me figure out the premissions and "lack of space" issue, do, otherwise, private message me if you just want to chat. Thanks.

---

### Post by bwallum on 2008-04-21
Are you finding that files above a certain size are not copying? The live cd has it's own (restricted) memory space and you may find that it is this space that is 'not enough space on the destination'. Consider the live cd memory as a clipboard. The clipboard size is restricted. To move a file the live cd copies it to the clipboard and then writes it to the actual destination.

fsck is normally auto run at boot to check a file system. Do you have a damaged file system? Can you boot up with your harddrive OS rather than the live cd? You would be much better off if you can boot an installed system so that you can use the full swap resources of an installed system.

Its difficult to blow up a hard drive completely. If you have corrupted, or think you have corrupted, a partition table then I would try to fix that first. testdisk will enable you to do precisely that. You can run testdisk from the live cd with:```
sudo testdisk
```Start by using 'Analyse' after chosing the drive. It is pretty much 'follow the default option' after that. It will find all files on the system and identify any damaged partition. You may have questions as you go along. Have a look first at:

[http://www.cgsecurity.org/wiki/OS_Notes#Linux_and_48-bit_LBA](http://www.cgsecurity.org/wiki/OS_Notes#Linux_and_48-bit_LBA)

Its a good, short overview of what you need to do. You can link from this page to more detail as required.

---

### Post by Mark_in_Hollywood on 2008-04-21
> **bwallum said:**
> 

fsck is normally auto run at boot to check a file system. Do you have a damaged file system?

I tried to make a separate /home following Psychocats instructions.

Can you boot up with your harddrive OS rather than the live cd? 

No, the OS gets past Grub, past "starting up", and as far as about 25% of the completion bar on the Ubuntu splash screen. Then the screen goes to ASCII text and fsck runs. Then 1000s of lines flash by so fast there is no reading it, until the KB is locked. The error message is always the same about multiply claimed blocks in inode ...


You would be much better off if you can boot an installed system so that you can use the full swap resources of an installed system.

Its difficult to blow up a hard drive completely. If you have corrupted, or think you have corrupted, a partition table then I would try to fix that first. testdisk will enable you to do precisely that. You can run testdisk from the live cd with:```
sudo testdisk
```Start by using 'Analyse' after chosing the drive. It is pretty much 'follow the default option' after that. It will find all files on the system and identify any damaged partition. You may have questions as you go along. Have a look first at:

[http://www.cgsecurity.org/wiki/OS_Notes#Linux_and_48-bit_LBA](http://www.cgsecurity.org/wiki/OS_Notes#Linux_and_48-bit_LBA)

ubuntu@ubuntu:~$ wget [http://www.cgsecurity.org/testdisk-6.7.linuxstatic.tar.bz2](http://www.cgsecurity.org/testdisk-6.7.linuxstatic.tar.bz2)
--18:47:56--  [http://www.cgsecurity.org/testdisk-6.7.linuxstatic.tar.bz2](http://www.cgsecurity.org/testdisk-6.7.linuxstatic.tar.bz2)
           => `testdisk-6.7.linuxstatic.tar.bz2'
Resolving [www.cgsecurity.org](www.cgsecurity.org)... 193.168.50.59
Connecting to www.cgsecurity.org|193.168.50.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
18:47:56 ERROR 404: Not Found.

So, from a LiveCd session at the moment, I can't download/install and run testdisk.

All I want to do is copy the data to a usb external drive. Remove the usb cable and from a LiveCD run fsck and see if that fixes it. I'm more than willing to give 'testdisk' a try, but have to be able to install it.

---

### Post by Mark_in_Hollywood on 2008-04-21
I found a way to download, install and run 'testdisk'. I followed all the procedures outlined above in this thread.

On reboot, I had the same problem.

---

### Post by bwallum on 2008-04-21
Good, i have been getting testdisk running using the live cd and sudo apt-get install testdisk.

Have you got a good partition table on the drive you are trying to rescue?

If grub is running it seems as though the mbr on your bootable drive is ok. Can you check that all is well on the drive you boot from? In particular that the partition structure is ok. Use Intel/PC for hint on file system when running Analyse in testdisk.

Then remove all usb hardware plugged in to your machine.Unplug any ethernet cable. Please tell me how you normally access the internet wired,wireless,ethernet (RJ45 socket), usb, dial up or broadband, modem or router, adsl or cable. Try and boot up again if the partition on the bootable disk is sound.

I'm on a live cd so should be able to help a bit better. Sorry for the testdisk delay.

---

### Post by Mark_in_Hollywood on 2008-04-21
> **bwallum said:**
> Good, i have been getting testdisk running using the live cd and sudo apt-get install testdisk.

Have you got a good partition table on the drive you are trying to rescue?

[COLOR="Red"]I'm sorry to tell you I have no idea as to how to determine whether I have a "good partition table" or not.[/COLOR]

If grub is running it seems as though the mbr on your bootable drive is ok. Can you check that all is well on the drive you boot from? In particular that the partition structure is ok. Use Intel/PC for hint on file system when running Analyse in testdisk.
[COLOR="Red"]

Running 'testdisk', I selected Analyze, Intel, (or maybe Intel and then Analyze I've forgotten which order those commands occcur in) and then Write partition table. On reboot, I still have no OS.[/COLOR]

Then remove all usb hardware plugged in to your machine.Unplug any ethernet cable. Please tell me how you normally access the internet wired,wireless,ethernet (RJ45 socket), usb, dial up or broadband, modem or router, adsl or cable. Try and boot up again if the partition on the bootable disk is sound.
[COLOR="Red"]
My computer sees the 'net via wireless-g. i.e., an AT&T 2Wire modem-router. I don't know **adsl**, we pay for **dsl**[/COLOR]

I'm on a live cd so should be able to help a bit better. Sorry for the testdisk delay.

[COLOR="Red"]I have no wired 'net, dial-up,  upon unplugging all USB, and rebooting, shows, Grub works, then "Starting up ..." and then the splash screen which completion bar fills to 25% or so, when fsck runs and reports errors on /dev/sda1 AND booting via Recover Mode, does the same fsck forced, etc.[/COLOR]

---

### Post by bwallum on 2008-04-22
testdisk is the way to tell if your partition table on your bootable harddrive is ok. It will detect it. You appear to have re written it, thats ok and says to me that the table is probably ok.

To recap, we know that the bootable hard drive has a good mbr because grub runs ok. We know that the partition table is probably ok on the drive we are trying to recover.

More questions 

Is the bootable harddrive the one you are trying to recover? That is, do you have another drive that is booted first?

The next step is to repair the OS so that we can boot it and gain access to the whole computer resources and complete the backup of your data hard drive.

Can you boot into recovery mode from the grub menu? (Note that you can use any recovery kernel offered by grub). If you can choose recovery, you will see a lot of stuff scroll by and then you will end up with a prompt, something like mine:

> root@bob-desktop:~$ We can now use this command line interface to sort out the system. Just to get us fully up to date, and assuming you want the latest Hardy release candidate, do this:

```
apt-get dist-upgrade
```then

```
apt-get update
``` and then tidy up with

```
apt-get autoremove
```then to restart

```
reboot
```

On reboot, choose the latest kernel in grub (the one at the top), then let me know how things are going.

---

### Post by Mark_in_Hollywood on 2008-04-22
[QUOTE=bwallum;4763089]

More questions 

Is the bootable harddrive the one you are trying to recover?

The only hard drive in the computer is the drive that boots.

 That is, do you have another drive that is booted first? NO

Can you boot into recovery mode from the grub menu? YES

(Note that you can use any recovery kernel offered by grub). If you can choose recovery, you will see a lot of stuff scroll by and then you will end up with a prompt, something like mine: 

no: see last paragraph of my post above this one:

[COLOR="Red"]AND booting via Recover Mode, does the same fsck forced, etc.[/COLOR] the KB locks and I must Alt-Syq REISUBK to reboot.

I'm not changing horses mid-stream here, but I would like a way to back up all my /home, first, before we proceed. I have a 55 gig drive in an external usb cradle. It is GParted as Primary partition and formatted as ext3.

---

### Post by bwallum on 2008-04-22
It looks like a partition table problem to me. However we have done that route and you have re written the partition table. 

If, using the live cd, you can get some files off the 360GB drive and put them on your external drive, then it is a question of finding out the maximum size that the live cd can handle and knife and forking it all over to your external drive.

If some files won't copy over but seem to be small enough then they are likely to be corrupted or the pointer to them corrupted (back to partition table again). 

I think it is time to bring in some fresh ideas so I have made a new thread. That usually brings in some more ideas.

[http://ubuntuforums.org/showthread.php?p=4764672#post4764672](http://ubuntuforums.org/showthread.php?p=4764672#post4764672)

---

### Post by Mark_in_Hollywood on 2008-04-25
I have my entire /dev/sda1 "recovered". By allowing GParted to perform it's "test" function, it has found the multiply-claimed blocks in inode: xxxxx and the 320 gig drive is all good.

---

### Post by bwallum on 2008-04-26
Thats really good news, congratulations! I have learnt something too so thank you very much for that.

Regards
Bob

---

