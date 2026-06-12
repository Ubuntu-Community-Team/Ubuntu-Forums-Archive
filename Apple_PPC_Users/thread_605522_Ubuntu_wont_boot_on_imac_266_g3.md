---
title: "Ubuntu wont boot on imac 266 g3"
date: 2007-11-07
forum: Apple PPC Users
---

### Post by Bong_Master_Darky on 2007-11-07
yo guys i got a bondi blue imac from the dump and thought i would give ubuntu a go on it, the specs of the Imac are 266mhz g3 40gb hdd and 256ram. the problem is with the bloody thing it wont boot ubuntu it manages to install fine with no problem but after the install is complete and the cd is ejected and the imac resets it just hangs on loading kernal image, is the imac fked or am i doing somthing wrong cheers people

---

### Post by PaganHippie on 2007-11-07
Well, of course it's possible that the machine is scrogged (how did it end up in the dump?), though if the install went OK that's probably not it.

Which version of Ubuntu are you trying to install?  There are known boot-up issues with 7.10 on PPC Macs, but I'm running 7.04 on a 233 MHz iMac with only 160MB of RAM and it's solid as a rock, if a bit sluggish.  6.06 also works well, but I had boot-up trouble with 6.10 as well.

I guess the upshot is, if you're trying to install 7.10, try again with a different, earlier version of Ubuntu and see what happens.  7.04 and 6.06 are both still available for download from [URL="http://cdimage.ubuntu.com"]http://cdimage.ubuntu.com
[/URL]

---

### Post by Bong_Master_Darky on 2007-11-08
yo the mac was at the dump because the local college had a clear out of the old stuff, im gonna give 7.04 ago the version i had was 5.04 which i had sent to me ages ago ill give a newer version ago and see if it works cheers for the reply :)

---

### Post by colinhayes on 2007-11-08
try giving 6.06 or 6.10 a shot.  6.10 is only version that loaded correctly to boot on my G5 (all the others required a bit of xorg.conf and video driver tweaking)

---

### Post by Bong_Master_Darky on 2007-11-08
yo guys i tried the 7.04 cd booted it but when gnome boots with the ubuntu bar loading it has an error message saying

"there was an error starting gnome sound daemon somthing suach as themes sound or back ground settings may not work correctly

the last error message was:
did not receive a reply. possible causes include the remote application did not send a reply, the message bus security policy blocked the relpy  the reply time out expired or the network connection was broken.

gnome will try to restart the setting daemon next time you log in 

wtf does this mean the booting doesnt get no further and just hangs does that mean its fked 

cheers

---

### Post by PaganHippie on 2007-11-09
The first message sounds like the sound hardware may be faulty.  The last one sounds like a networking error.  Faulty memory could also cause weird errors that can be very hard to trace.  I suspect that this particular computer may be a boat anchor.  If you want to give it one more try, though, try booting with the 'Alternate' CD instead of the 'Live' CD and see what happens.  If that fails, drop back 15 yards and punt.

---

### Post by oswaldkelso on 2007-11-09
> **Bong_Master_Darky said:**
> yo guys i got a bondi blue imac from the dump and thought i would give ubuntu a go on it, the specs of the Imac are 266mhz g3 40gb hdd and 256ram. the problem is with the bloody thing it wont boot ubuntu it manages to install fine with no problem but after the install is complete and the cd is ejected and the imac resets it just hangs on loading kernal image, is the imac fked or am i doing somthing wrong cheers people



I recently did a how to install debian on imac  ppc over at the [debian forun]("http://forums.debian.net/viewtopic.php?t=20481")  scroll down a bit and to" imac problems"  see some of the things you need to do that is imac crt related i.e firm ware, the  hard drive size problem, and xorg setting all relate to an ubuntu install.  The obvious one is you have a larger hd than it was designed  for. Early imacs can only see the first 8.gb so you must partition.

---

### Post by Bong_Master_Darky on 2007-11-10
yo i tried the debian install and the same thing happens which leads me to believe yaboot is fked and not the mac its self because after the install is complete i can throw in the opensuse cd and boot the system from the hdd fine, i think the problem is either partitioning or not configuring yaboot right, not to sure how partitioning should be.

thanks for the help so far guys

---

### Post by oswaldkelso on 2007-11-10
did you make sure your first partition was the root patrition and within the first 8gb then make your home partition on the rest? if you choose all on one partition it will fail.

---

### Post by Bong_Master_Darky on 2007-11-10
yo sorry to be a total noob when you say root partition is as in the hda3 where all the data is store my current layout is like this 

1. 32.3 kb apple 
2. 1.0MB Boot untitled 
3.40.7GB F Ext3 untitled 
4.378MB swap swap 

is this correct, i am a total noobie when it comes to this sorta thing if you could provide step by step for partitioning i would be greatful thank you 

:)

---

### Post by oswaldkelso on 2007-11-10
> **Bong_Master_Darky said:**
> yo sorry to be a total noob when you say root partition is as in the hda3 where all the data is store my current layout is like this 

1. 32.3 kb apple 
2. 1.0MB Boot untitled 
3.40.7GB F Ext3 untitled 
4.378MB swap swap 

is this correct, i am a total noobie when it comes to this sorta thing if you could provide step by step for partitioning i would be greatful thank you 

:)You can use my guide up to this  point original guide in blue 

[COLOR="Blue"][COLOR="Blue"]partitioning method:	guided use entire disk[/COLOR][/COLOR] **[COLOR="Red"]DON'T DO THIS. "SELECT SEPARATE HOME PARTITION"[/COLOR]**  
[COLOR="Blue"]
IMPORTANT NOTE: When you confirm (THIS WILL ERASE THE WHOLE DISK AND YOUR DATA!!!) Read up on disk partioning if you want to dual boot. If you have your mac OS install disks and have backed up all your data you can rebuild your system. If you don't there is no going back mac OS will be gone for good!!! proceed at your own risk.

select disk to partition:	mine was IDE MASTER (hda) -6.4 GB quantum fireball cr6.4a
partition scheme:	all files on one partition.

NOTE: I choose this as the Hard drive is small and there will be no vital data on it. You may want to have a separate home partition to aid data recovery should things ever go awol.

NOTE: after partitioning my 6.4 gb hard drive looked like this:
#1	32.3kb					apple
#2	1.0mb	B	K	Boot	untitled
#3	6.1GB		F	Ext3	untitled
#4	333.6mb		F	swap	swap[/COLOR]

Change your partiton so it looks something like this below. The guided partitioner will do it for you if you select separate home partition. NOTE: you can change the size manually if the / root partition is made to  big thought I doubt it would.

e.g.

#1      32.3kb					apple
#2	1.0mb	B	K	Boot	untitled
#3	6GB		F	Ext3	/          (this is your root partition where the main os goes must be less than 8GB)
#4	30GB		F	Ext3	home ( it maybe /home my memory fails)  (this is your home partition where you store your personel settings and data )
#5	500mb		F	swap	swap

The ubuntu alternate cd is the same system as the debian one so you can set up your  partitions with either. Then you could install any ppc linux distro you like on that / root partition. 

 
[COLOR="Blue"]
"The second big tray-loading iMac problem is shared with the WallStreet PowerBooks and beige G3 Power Macs - any drive over 8 GB must be partitioned, the first partition must be smaller than 8 GB, and these models will only boot from OS X if it's installed on the first partition."

This also applies to linux, if you have fitted a larger HD put boot and root on the first 8gb and a separate home partition on the rest. If your going to dual boot. Osx must be on the first partition. Linux on the second, both within the first 8gb. This is a hardware constraint not software.[/COLOR]

This means if you all ready have osx on all of the first 8gb your linux install will fail. You would need to back up your data and reinstall osx using the install cd and use the disc utility on the cd to partition your hd first.  
If you have no other os on there and want linux only use the ubuntu alternate cd or my debian instruction to set up your hard drive.

---

### Post by PaganHippie on 2007-11-11
Hmm... I wasn't aware of this 8GB limitation, though I had heard that they can't use drives > 127GB.  Good to know.

So, the trick is to create a small /boot partition within the first 8 GB?  (I've used a similar trick on old 486 PCs with 512MB BIOS limitations....)

---

### Post by oswaldkelso on 2007-11-11
> **PaganHippie said:**
> Hmm... I wasn't aware of this 8GB limitation, though I had heard that they can't use drives > 127GB.  Good to know.

So, the trick is to create a small /boot partition within the first 8 GB?  (I've used a similar trick on old 486 PCs with 512MB BIOS limitations....)

Yes the 127 limit affected "imac crt slot loaders" and some G4 towers if I remember correctly.   The "imac crt tray loaders"  ( imac up to 333mhz) had the 8gb limit. I have a 333mhz and remember having to partition the drive after fitting a larger HD. I remember I wasn't sure if the 8gb limit applied after the first partition so made 3x 7.95gb partitions :)

---

### Post by Bong_Master_Darky on 2007-11-11
probelm solved i followed the info for about partitioning giving by oswaldkelso, did the reinstall and every thing went fine no i have a free imac from the dump which runs ubuntu yipeeeee brought it back to life :)

thanks every one for you help 

oswaldkelso = the ubuntu doctor

---

### Post by oswaldkelso on 2007-11-11
> **Bong_Master_Darky said:**
> probelm solved i followed the info for about partitioning giving by oswaldkelso, did the reinstall and every thing went fine no i have a free imac from the dump which runs ubuntu yipeeeee brought it back to life :)

thanks every one for you help 

oswaldkelso = the ubuntu doctor

Well done :lolflag: make that debian doctor :) ( I'm not much more than a noob myself, just sharing)  Anyway no one running gnu/linux needs a doctor its the rest that need their head examined

---

### Post by stream303 on 2008-02-18
> **oswaldkelso said:**
> 
NOTE: after partitioning my 6.4 gb hard drive looked like this:
#1	32.3kb					apple
#2	1.0mb	B	K	Boot	untitled
#3	6.1GB		F	Ext3	untitled
#4	333.6mb		F	swap	swap

I forgot where I read this, but I recall some people having problems when the #2 boot partition is on the boundary of 1.0mb, so you can make it a tad smaller, like 977K or so.

Great info on how to partition btw!

---

