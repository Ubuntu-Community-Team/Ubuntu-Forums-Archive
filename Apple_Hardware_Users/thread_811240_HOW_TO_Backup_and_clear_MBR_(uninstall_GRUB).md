---
title: "HOW TO: Backup and clear MBR (uninstall GRUB)"
date: 2008-05-28
forum: Apple Hardware Users
---

### Post by cyberdork33 on 2008-05-28
[SIZE="7"]**[COLOR="Red"]Try at your own risk.[/COLOR]**[/SIZE]
[COLOR=Red]WARNING: The following commands can easily wipe out your entire hard drive if you are not very careful (make a typo). Please make sure you have everything backed up before proceeding.[/COLOR]

If you happen to be one of several people that somehow end up with two different icons in rEFIt that boot GRUB for Ubuntu, then this will show you how to remove one of them.

**Background**
The issue is that the Ubuntu installer by default installs GRUB to the MBR of the Hard Drive. This is OK for most PCs as this will make it easiest to dual-boot with Windows. On Macs, however, We usually use rEFIt or Hold the Option Key at startup to select which partition to boot from, and having GRUB in the MBR means that you have to use both rEFIt and GRUB to get to windows (for a triple-boot), so most guides tend to install GRUB to the Ubuntu partition and that is OK, but with the advent of a [installer bug]("http://ubuntuforums.org/showthread.php?t=767677"). The MBR becomes corrupted and many users unknowingly reinstall GRUB to the Ubuntu partition after it has already been installed to the MBR, and thus you get two instances of GRUB to boot.

Before we begin, it is a good idea to **[COLOR="Red"]make sure that refit is installed and working[/COLOR]** so that you can access its tools in the boot menu if needed.

**Now, the Good Stuff**
[COLOR="Red"]_**Before you do any of the following,_ make a backup of the entire MBR and save it to a thumbdrive or other external media so that you can restore it from a LiveCD if anything goes wrong.**[/color] 
Do this by opening a terminal and running:
```
sudo dd if=/dev/sda of=/home/username/mbr_backup bs=512 count=1
```

replace "username" with your Ubuntu username. This will create the file "mbr_backup" in your home folder. Copy this somewhere safe where you can get to it if you are left with an unbootable machine!

**Now we will write over your current MBR with a new dummy version that has no real information in it, but will still allow you to boot your system. Download the "fakembr80.txt" file attached to this post (thanks [pxwpxw]("http://ubuntuforums.org/member.php?u=85693")) to your home folder.**

Now we will right the binary contents of this file to your MBR:
```
sudo dd if=/home/username/fakembr80.txt of=/dev/sda bs=512 count=1
```

You should get output that looks like:
```
1+0 records in
1+0 records out
512 bytes transferred in 0.350948 secs (1459 bytes/sec)
```
If you don't, try this procedure from the Ubuntu LiveCD (no need to backup again).

**If you have issues after clearing a portion of the MBR. This command shows you how to restore it from the backup file that you made:**
```
sudo dd if=/home/username/mbr_backup of=/dev/sda bs=512 count=1
```

Anytime you write to your MBR, you should resync the partition tables. You can do this with rEFIt's "Partition Tool" in the main rEFIt boot menu or you can use the gptsync utility in Ubuntu:
```
sudo apt-get install refit
sudo gptsync
```

---

### Post by meierfra. on 2008-05-29
> ssudo

Is this a Mac command or a typo?

---

### Post by cyberdork33 on 2008-05-29
> **meierfra. said:**
> Is this a Mac command or a typo?typo... and fixed. Thanks.

---

### Post by ipina on 2008-06-21
Hi, your help is very appreciated, I think you're a great reference concerning the implementation of Ubuntu on Mac. In respect to this issue, maybe it's a good idea to specify that in the first post aren't described a series of steps to follow, rather they are alternatives the user can choose, except the first one which is mandatory. Greetings.

---

### Post by ipina on 2008-06-21
And I should add that the first post works! at least in a Mac Pro 1 (four Xeon nuclei, Nvidia card and Leopard 10.5.3). Thanks once more for your help.

---

### Post by umbrAtrorum on 2008-07-04
a question for understanding: how can i resync with refit when the mbr is gone? i mean, can the system start refit after deleting the entire mbr? and what use does the backup copy have when i kill the entire mbr? how will you be able to access this backup then? i like the idea, but does it really work?

---

### Post by Nikolai D. on 2008-07-30
Hi guys. Hi Cyber :)

I've a little question. I've been trying to install Debian. Wanted to try it cuz Ubuntus X was hanging or something like that. When i used up all my ram (1gig). Althou it was working ok with Fluxbox. I've been trying to test virtual network. XP and 2003 (DNS server). Also Debian is going to be secondary DNS. So i've decided to try Debian (the stable they say;).
So at one moment i've tryed to install elilo on mbr. And after that i've got two Tux icons in rEFIt but neither of them boots up. Also reinstalled grub via live cd on linux partition. One says booting "elilo.efi blah blah blah" and then nothing further. Another gives "grub>" prompt. Happily Mac still boots up.

So, to the case. I guess my next thing to do is to try method explained above. But i have a question. If i
 sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
how does my system going to boot then?
 Waiting for your response.

Have a nice day!
Nikolai

---

### Post by mabovo on 2008-07-30
Same situation here.

---

### Post by cyberdork33 on 2008-07-30
> **Nikolai D. said:**
> So at one moment i've tryed to install elilo on mbr. And after that i've got two Tux icons in rEFIt but neither of them boots up. Also reinstalled grub via live cd on linux partition. One says booting "elilo.efi blah blah blah" and then nothing further. Another gives "grub>" prompt. Happily Mac still boots up. I don't know anything about elilo... as far as I know it is still quite a bit buggy to boot via EFI.

> **Nikolai D. said:**
> So, to the case. I guess my next thing to do is to try method explained above. But i have a question. If i
 sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
how does my system going to boot then?
 Waiting for your response. That will clear the bootcode in the MBR. That means that if you do not have grub installed elsewhere (on a partition) then you will not be able to boot into Ubuntu (or whatever distro). But that is not to say that you cannot boot a livecd and reinstall GRUB how you like.

the "elilo.efi" is a result of your elilo install. I do not know anything about it, so I cannot really help you there.

On the second, since you are getting a grub prompt, then the stage1 installed appropriately (to wherever you installed it) but it likely cannot find the stage2 file and / or the menu.lst and such. This is likely a result of setting the wrong root partition during your manual install of grub.

so what I think you need to do is try again on installing GRUB manually to the Linux boot partition. On the liveCD, run 'sudo grub'. Then:
```
grub> find /boot/grub/stage[FONT=Verdana]2[/FONT]
```[FONT=monospace]You should get a result like (hdX,Y) where X and Y are numbers.
Then do:
[/FONT]```
grub> root (hdX,Y)[FONT=monospace]
[/FONT]grub> setup (hdX,Y)
```
That will install grub stage1 to the Linux partition, and point it to the linux partition to look for configuration.

---

### Post by Nikolai D. on 2008-07-31
Hi guys.

Oke. Heres what i did.

LiveCD
sudo grub
grub> find /boot/grub/stage2
(hd0,2)
grub> root (hd0,2)
grub> setup (hd0,2)

Rebooted in that linux partition pushing Alt key (i like it wothout rEFIt). And i get same "grub>" prompt. So i go for booting my MacOS from rEFIt. And i see there onemore partitionp appearred. Now there are three Tuxes :) Niether of them boots up :D (i guess ill go boot it up onemoretime and try all of the Tuxes, tobe sure).

And next ill try now to DD ZERO my boot loader (only boot loader not whole MBR).
Thats it.
ill post after, how its going on.

Thank you for help onemore time.
Have a nice day.
And see ya agane. ;)
Nikolai

---

### Post by cyberdork33 on 2008-07-31
I would guess that holding ALT on bootup is giving you the install in the MBR... One of the tux icons should now.... at least one...

PS, at the grub menu, you can use the grub console to load Ubuntu... I know this is not a solution, but it might garner more info.

```
grub> root (hd0,2)
grub> kernel /boot/vmlinuz-2.6.24-19-generic
grub> initrd /boot/initrd.img-2.6.24-19-generic
grub> boot
```

---

### Post by Nikolai D. on 2008-08-03
Hi guys.

Cyber. My mac is not doing it good at all. :) I was tired of all that .. (no any bootable Tux icon). So i tough, ill just reinstall OSX, and everything is going to be ok. But, huh, no. I still get elilo Tux in rEFIt. Now i dont even care aboutbooting linux up yet. But how do i get this elilo off my mac. :)

Hopely someone can give some advice.

HF
Nikolai

---

### Post by mabovo on 2008-08-03
I am giving up Hardy just tired to reinstall it.

Burned an Intrepid iso and will start another ammusement. Who knows if Intel driver gets better and iSight doesn't freeze !

---

### Post by cyberdork33 on 2008-08-03
> **Nikolai D. said:**
> Hi guys.

Cyber. My mac is not doing it good at all. :) I was tired of all that .. (no any bootable Tux icon). So i tough, ill just reinstall OSX, and everything is going to be ok. But, huh, no. I still get elilo Tux in rEFIt. Now i dont even care aboutbooting linux up yet. But how do i get this elilo off my mac. :)
elilo is likely a efi executable that was copied somewhere. Since I do not know much about it, I can't really tell you where to go... How did you install it? maybe you can search for a file ending in .efi to find it?

> **mabovo said:**
> Burned an Intrepid iso and will start another ammusement. Who knows if Intel driver gets better and iSight doesn't freeze !You seem to be the only one having a problem with the iSight freezing.

---

### Post by mabovo on 2008-08-03
> **cyberdork33 said:**
> elilo is likely a efi executable that was copied 

You seem to be the only one having a problem with the iSight freezing.

My iSight driver complained about so many kernels updates. Should be better go straight to 2.6.26.

---

### Post by Nikolai D. on 2008-08-04
Hellow World =]

Cyber, When i was installing Debian GRUB failed as usual. So i tryed elilo. And after that i cant get that unbootable efi tux outta here, also cant get toehr tux to boot. However before just a matual grub install did it. =]

I started another thread with auestion if OSX stays installable if i delete 200mb fat (efi?) partition.

Enjoy.
Nikolai

---

### Post by cyberdork33 on 2008-08-04
> **Nikolai D. said:**
> I started another thread with auestion if OSX stays installable if i delete 200mb fat (efi?) partition.
I replied there:
[http://ubuntuforums.org/showthread.php?t=879595](http://ubuntuforums.org/showthread.php?t=879595)

---

### Post by Nikolai D. on 2008-08-05
Hi all.

Cyber, im asking myself whats the difference between those two methodes.

Here:[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Ive found explanation on how to reinstall grub via livecd.

And it's:
sudo grub
find /boot/grub/stage1
(hd0,2) in my case
root (hd0,2)
setup (hd0)
quit
And it worked for my Ubuntu.

But you told meonce to do:
sudo grub
find /boot/grub/stage1
(hd0,2) in my case
root (hd0,2)
setup (hd0,2)     <- see difference here
quit

Ok i understand that its pointing exactly to root partition. But how comes the first methode worked for me then. Cuz for me second methode looks more right.
Why am i asking is because i just 'bootcamped' my hd. And installed Debian agane. But chose to not install grub. So nowi have to install grub manually. And its second methode as i understand, but i keep asking myself how does the other worked for me then. :)

Okay.
Have a nice day.
Nikolai

---

### Post by cyberdork33 on 2008-08-05
> **Nikolai D. said:**
> Ok i understand that its pointing exactly to root partition. But how comes the first methode worked for me then. Cuz for me second methode looks more right.
Why am i asking is because i just 'bootcamped' my hd. And installed Debian agane. But chose to not install grub. So nowi have to install grub manually. And its second methode as i understand, but i keep asking myself how does the other worked for me then. :)
I am not sure why installing to the root partition was not working for you, but if it works the other way then do it. The only time that installing to the MBR is an issue is when windows gets involved because it's bootloader will take over the MBR.

The 'root' command tells grub where the grub files are (stage2, menu.lst).
The 'setup' command actually copies the stage1 bootcode into the header of the partition your specify (hd0,2), or the MBR if you just point to the disk (hd0). 

For some reason refit was not seeing the bootcode you installed to the root partition. Maybe elilo / another install of grub was confusing it.

---

### Post by stillingen on 2008-12-14
> **cyberdork33 said:**
> Try at your own risk.

If you happen to be one of several people that somehow end up with two different icons in rEFIt that boot GRUB for Ubuntu, then this will show you how to remove one of them.

**Background**
The issue is that the Ubuntu installer by default installs GRUB to the MBR of the Hard Drive. This is OK for most PCs as this will make it easiest to dual-boot with Windows. On Macs, however, We usually use rEFIt or Hold the Option Key at startup to select which partition to boot from, and having GRUB in the MBR means that you have to use both rEFIt and GRUB to get to windows (for a triple-boot), so most guides tend to install GRUB to the Ubuntu partition and that is OK, but with the advent of a [installer bug]("http://ubuntuforums.org/showthread.php?t=767677"). The MBR becomes corrupted and many users unknowingly reinstall GRUB to the Ubuntu partition after it has already been installed to the MBR, and thus you get two instances of GRUB to boot.

[COLOR=Red]WARNING: The following commands can easily wipe out your entire hard drive if you are not very careful (make a typo). Please make sure you have everything backed up before proceeding.[/COLOR]

**Now, the Good Stuff**
[B]
_Before you do any of the following,_ make a backup of the entire MBR:[/B] 
```
sudo dd if=/dev/sda of=/home/username/mbr_backup bs=512 count=1
```

**Now complete the appropriate step below to clear the portion of the MBR you need.**

In order to Clear out the MBR except the partition table (Literally, write zeros over the current MBR contents):
```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```

To clear the complete MBR, including the partition table (On a Mac, the partition table can be recovered by syncing your partition tables with rEFIt):
```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
```

**If you have issues after clearing a portion of the MBR. These commands show you how to restore it.**
To restore only the Bootsector (not including the partition table):
```
sudo dd if=/home/username/mbr_backup of=/dev/sda bs=446 count=1
```

To restore the entire MBR:
```
sudo dd if=/home/username/mbr_backup of=/dev/sda bs=512 count=1
```

I've ended up with not being able to read /dev/sda after clearing the MBR. I've tried running from Ubuntu LiveCD. Is there a way to restore my MBR, or do I have to reinstall OSX and Ubuntu?

---

### Post by pxwpxw on 2008-12-15
> **stillingen said:**
> I've ended up with not being able to read /dev/sda after clearing the MBR. I've tried running from Ubuntu LiveCD. Is there a way to restore my MBR, or do I have to reinstall OSX and Ubuntu?

If the problem is an unusable MBR sector on sda, there is a procedure which may fix that.
It was done using  Macosx, but can be done from a Ubuntu live cd.
It just writes a fake MBR to allow the refit partition tool to resync the MBR.
You can then install the refit package and run gptsync from the Live CD.

 You first need to check the state of the sda MBR sector by doing a hexdump to see if this applies to you, it may not.

There is a record of a succesful fix using my posts in these links, you need to read around these posts for the full story..

Re: 8.04 cleared the MBR partition table
[http://ubuntuforums.org/showpost.php?p=6333155&postcount=24](http://ubuntuforums.org/showpost.php?p=6333155&postcount=24)

[http://ubuntuforums.org/showpost.php?p=6333398&postcount=30](http://ubuntuforums.org/showpost.php?p=6333398&postcount=30)
(attached dummymbr.txt)

[http://ubuntuforums.org/showpost.php?p=6333700&postcount=37](http://ubuntuforums.org/showpost.php?p=6333700&postcount=37)

---

### Post by cyberdork33 on 2008-12-15
My procedure seems to have stopped working appropriately very recently. I will modify the original post. 

Which command did you run?

If you created a backup of the MBR (as indicated in the original post) you should be able to restore it as instructed from the LiveCD.

pxwpxw, What should be modified (if anything) in the original commands so that this does not occur?

---

### Post by stillingen on 2008-12-15
> **pxwpxw said:**
> If the problem is an unusable MBR sector on sda, there is a procedure which may fix that.
It was done using  Macosx, but can be done from a Ubuntu live cd.
It just writes a fake MBR to allow the refit partition tool to resync the MBR.
You can then install the refit package and run gptsync from the Live CD.

 You first need to check the state of the sda MBR sector by doing a hexdump to see if this applies to you, it may not.

There is a record of a succesful fix using my posts in these links, you need to read around these posts for the full story..

Re: 8.04 cleared the MBR partition table
[http://ubuntuforums.org/showpost.php?p=6333155&postcount=24](http://ubuntuforums.org/showpost.php?p=6333155&postcount=24)

[http://ubuntuforums.org/showpost.php?p=6333398&postcount=30](http://ubuntuforums.org/showpost.php?p=6333398&postcount=30)
(attached dummymbr.txt)

[http://ubuntuforums.org/showpost.php?p=6333700&postcount=37](http://ubuntuforums.org/showpost.php?p=6333700&postcount=37)

Thank you. I've tried your suggestions, and everything seems to go ok, but I still can not boot. When I try to boot I end up with a envelope with an question mark on it (like before).

> **cyberdork33 said:**
> My procedure seems to have stopped working appropriately very recently. I will modify the original post. 

Which command did you run?

If you created a backup of the MBR (as indicated in the original post) you should be able to restore it as instructed from the LiveCD.

pxwpxw, What should be modified (if anything) in the original commands so that this does not occur?

I did indeed back up. But I can access /dev/sda, so I can't get to the back up. When I try to mount, I get "device not found".
I did both commands

sudo dd if=/dev/sda of=/home/username/mbr_backup bs=512 count=1

sudo dd if=/dev/zero of=/dev/sda bs=512 count=1

I just remembered that there was an Apple Boot / EFI update that I completed couple of days ago. Could that be related.
Really thankful for your support. I would really like to get my Macbook running again..

---

### Post by stillingen on 2008-12-15
Tried a your instructions pxwpxw a 2nd time, and got it rolling! Thank you, this saved me days...

I´m not able to boot using Ubuntu though..

---

### Post by cyberdork33 on 2008-12-15
> **stillingen said:**
> I´m not able to boot using Ubuntu though..
You'll still have to sync the partition tables with rEFIt and possibly reinstall grub.

---

### Post by pxwpxw on 2008-12-15
> **cyberdork33 said:**
> My procedure seems to have stopped working appropriately very recently. I will modify the original post. 

pxwpxw, What should be modified (if anything) in the original commands so that this does not occur?

I would just delete reference to clearing the 512 bytes, it makes it unbootable and gptsync refuses to sync it. 
[http://ubuntuforums.org/showpost.php?p=6176317&postcount=3](http://ubuntuforums.org/showpost.php?p=6176317&postcount=3)

There does not seem to be a need to clear all the MBR partition table unless entries are garbled and stop gptsync from correcting ( message  ' suspicious ... not touching that '  ). 

If there is a need,  clear 510 bytes leaving the dos mbr signature 55AA, which still wont boot, but gptsync will correct it.
Preferable to use the 512 byte dummymbr, or 'fakembr' - it  clears it but makes it bootable by making a valid entry (doesn't seem to require the correct size, just the valid entry format).
Might be and idea to attach a fake mbr in the thread for insurance.
And advise to check with hexdump first.

---

### Post by cyberdork33 on 2008-12-15
> **pxwpxw said:**
> I would just delete reference to clearing the 512 bytes, it makes it unbootable and gptsync refuses to sync it. 
[http://ubuntuforums.org/showpost.php?p=6176317&postcount=3](http://ubuntuforums.org/showpost.php?p=6176317&postcount=3)

There does not seem to be a need to clear all the MBR partition table unless entries are garbled and stop gptsync from correcting ( message  ' suspicious ... not touching that '  ). 

If there is a need,  clear 510 bytes leaving the dos mbr signature 55AA, which still wont boot, but gptsync will correct it.
Preferable to use the 512 byte dummymbr, or 'fakembr' - it  clears it but makes it bootable by making a valid entry (doesn't seem to require the correct size, just the valid entry format).
Might be and idea to attach a fake mbr in the thread for insurance.
And advise to check with hexdump first.
Ok, I thought maybe just posting the "fake" MBR would be better.
Odd, that this seems to suddenly not work anymore... I had done it countless times before, and now it breaks everything.

---

### Post by pxwpxw on 2008-12-15
> **cyberdork33 said:**
> Ok, I thought maybe just posting the "fake" MBR would be better.
Odd, that this seems to suddenly not work anymore... I had done it countless times before, and now it breaks everything.


The fake mbr has the advantage that one size seems to fit all drives, even though it is for a different drive size (i have 80GB and 300GB to try it), and it worked for 900GB. It is simply what parted does to the MBR, so it can be written to the mbr by running the parted toggle command twice - but that is for the 804/810 version so IDK.

---

### Post by pxwpxw on 2008-12-15
fakembr is actually from an 80GB but size doesn't matter.  
```

mb:~/Desktop/mbrcleard pxw$ hexdump -C fakembr80 
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001c0  01 00 ee fe ff ff 01 00  00 00 af f8 50 09 00 00  |............P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
mb:~/Desktop/mbrcleard pxw$ 

```

---

### Post by cyberdork33 on 2008-12-16
> **pxwpxw said:**
> fakembr is actually from an 80GB but size doesn't matter.  
```

mb:~/Desktop/mbrcleard pxw$ hexdump -C fakembr80 
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001c0  01 00 ee fe ff ff 01 00  00 00 af f8 50 09 00 00  |............P...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
mb:~/Desktop/mbrcleard pxw$ 

```

Ok, please review:
[http://ubuntuforums.org/showpost.php?p=5067436&postcount=1](http://ubuntuforums.org/showpost.php?p=5067436&postcount=1)

---

### Post by pxwpxw on 2008-12-16
> **cyberdork33 said:**
> Ok, please review:
[http://ubuntuforums.org/showpost.php?p=5067436&postcount=1](http://ubuntuforums.org/showpost.php?p=5067436&postcount=1)

I think do it just using Macosx terminal, that way its easier to make and retrieve a usb MBR, you could say don't do it unless you have macosx, and emphasize that it needs refit to regen the MBR after the fakembr. Live CD would need more explaining about mounting usb or the hd root system, seems to be getting too hard.

I can pm you with an outline if you like, or put it here (tomorrow).

---

### Post by cyberdork33 on 2008-12-16
> **pxwpxw said:**
> I think do it just using Macosx terminal, that way its easier to make and retrieve a usb MBR, you could say don't do it unless you have macosx, and emphasize that it needs refit to regen the MBR after the fakembr. Live CD would need more explaining about mounting usb or the hd root system, seems to be getting too hard.

I can pm you with an outline if you like, or put it here (tomorrow).

I choose to do it from the Linux commandline for two major reasons:
1. This is a Linux forum, and I like to emphasize using Linux to accomplish the task. (and yes I know that dd is a UNIX tool).
2. As far as I can tell, Linux happily writes over the MBR with dd even with mounted partitions on the disk unlike OSX sometimes.


I think I will just show how to install refit in Ubuntu and sync immediately instead of relying n the reboot too.

---

### Post by pxwpxw on 2008-12-16
> **cyberdork33 said:**
> I choose to do it from the Linux commandline for two major reasons:
1. This is a Linux forum, and I like to emphasize using Linux to accomplish the task. (and yes I know that dd is a UNIX tool).

Yes, agreed
> 
2. As far as I can tell, Linux happily writes over the MBR with dd even with mounted partitions on the disk unlike OSX sometimes.

Yes, I forgot macosx has problems that way.
> 
I think I will just show how to install refit in Ubuntu and sync immediately instead of relying n the reboot too.
I think yes, fairly safe to assume the fakembr will work.

---

### Post by cyberdork33 on 2008-12-16
> **pxwpxw said:**
> I think yes, fairly safe to assume the fakembr will work.

Ok, I mention both as a way to sync partitions now.

---

### Post by pxwpxw on 2008-12-16
I just looked at the #1 post again.

It seems to have drifted away from the main stated purpose -  to remove the duplicate tux by deleting the grub bootcode in the first 446 bytes of the MBR.
I think this probably is why most people use it.

As in the previous version, this only requires -

from Ubuntu live cd
```

$ sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
$ sudo apt-get install refit
$ sudo gptsync /dev/sda

```
gptsync will report 'no need to sync' if all was well before the operation, because the partition table is untouched.

The backup mbr is always desirable.

The fake mbr was for a a separate issue of accidental damage to mbr, entirely unnecssary for removing tux which is the topic of the thread, unless something goes wrong.

---

### Post by cyberdork33 on 2008-12-17
> **pxwpxw said:**
> I just looked at the #1 post again.

It seems to have drifted away from the main stated purpose -  to remove the duplicate tux by deleting the grub bootcode in the first 446 bytes of the MBR.
I think this probably is why most people use it.
Well, I did make it more generic than that on purpose (see the thread title).

> **pxwpxw said:**
> As in the previous version, this only requires -

from Ubuntu live cd
```

$ sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
$ sudo apt-get install refit
$ sudo gptsync /dev/sda

```gptsync will report 'no need to sync' if all was well before the operation, because the partition table is untouched.
Understood, but I think that one had the same problem as doing the whole MBR (it removed that MBR header or whatever it is that allows the disk to be bootable... Maybe a dummy mbr that is only 446 bytes long?

> **pxwpxw said:**
> The fake mbr was for a a separate issue of accidental damage to mbr, entirely unnecssary for removing tux which is the topic of the thread, unless something goes wrong.Yes, I think the issue was that people following this (as well as the grub install issue that seems to cause it sometimes) were the ones with the damaged MBR.

Maybe another thread is in order.

---

### Post by stillingen on 2008-12-30
> **cyberdork33 said:**
> You'll still have to sync the partition tables with rEFIt and possibly reinstall grub.

Probably reinstall. I updated MBR, no go. I´ll probably drop Ubuntu, got quite friendly with OSX..

---

### Post by JollyRogers on 2009-09-11
Cyberdork, Want to personally thank you on this one. You are DA' MAN!!! I have your home page book marked btw.

I dorked my primary disk MBR up and ended up with a phantom Windows boot option... took me a while to realise that GPT/MBR kind of live together on an intel mac... I used dd and it cleaned the MBR. THANK YOU!

---

### Post by flusi100 on 2010-11-18
downright silly...#-o

could someone please post the original MBR-content of an MacBookAir 3,2?

thanks

---

### Post by Dark_Ronius on 2011-09-26
This absolutely worked for me, better than any instructions to try and fix my gpt/mbr when I solely had Mac OS on here, so thanks!

The only thing I found was that, instead of

```
sudo gptsync
```

I actually needed to type

```
sudo gptsync /dev/sda
```

However this was using the Oneiric Beta so maybe there's been some changes with the program or something.

Many thanks!

---

### Post by Netsurfer38 on 2012-05-04
Two tux icons on Triple Booted System (Lion OSX, Linux Mint 9, Windows 7)

Previously I also had the problem of two tux icons in rEFIT, and tried every option that I could find to get rid of it. Eventually what worked for me was the following:
(Instructions for Windows 7)

[LIST=1]
[*]Boot using Windows CD/DVD
[*]select **Repair your computer**
[*]select **Command Prompt**y
[*]enter **Bootrec.exe /FixMbr** (for XP I think one only needs **fixmbr**)
[/LIST]

Hope that this will work for others

---

