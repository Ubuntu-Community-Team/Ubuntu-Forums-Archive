---
title: "Help burning DVD ISO image"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-03-25
I am trying to burn a DVD ISO image with Gnomebaker. When I try it says /dev/hda: media is not recognized as recordable DVD. I have never done this with Linux(only cd images). I am using a DVD-R single layer 4.7 GB disc. I have two drives on my PC. I can't remember for sure because it has been a while, but I think with Windows I had to use the bottom tray to write DVD's. When I try to choose the drive, Gnomebaker will only let me choose the top tray. I know Ubuntu recognizes the bottom drive, because I watch DVD movies in it. I am not sure if it is hardware related or if I need to try another cd/dvd burner. Can anyone shed some light on this?

---

### Post by tonyr1988 on 2007-03-25
This is far from the optimal solution, but I use K3B for burning. I know a lot of people don't like running KDE apps in Gnome, but if you get past the dependencies (not hard, just a tad of disk space), I think K3B is the best burning application on any OS.

If you want to try it, do:

> sudo apt-get install k3b

(If you don't have any other KDE apps, it may take a while)

Just in case you change your mind, you can do these two:

> sudo apt-get remove k3b
sudo apt-get autoremove

It will remove K3B and all the dependencies, and bring you back to where you are now :D

---

### Post by machoo02 on 2007-03-25
+1 for K3B.  It's better than any burning software available for Gnome

---

### Post by 67GTA on 2007-03-25
I just tried using K3b and got the same error. It said that media was not found. I guess it is hardware related. Not sure where to go now.

---

### Post by Drakkor on 2007-03-25
Can you not just right click the .iso file and select "Write To Disk" ?

---

### Post by 67GTA on 2007-03-25
I saw that but wasn't sure if it would write the "image" or just the file. This is not a live dvd, so if it isn't right, I was afraid it would screw up my Ubuntu installation. If that is what that option is for then I will give that a try.

---

### Post by 67GTA on 2007-03-25
I tried right click>write to disc.. and it kept telling me to insert a blank disc. Something else is not right. I have no trouble burning cd iso's,only dvd. Is there something I'm missing to make this work?

---

### Post by Drakkor on 2007-03-25
Have you selected the proper burner ?  I have a CDRW,and and a DVDRW, and often have to make the choice.
It will properly burn the .iso  image, not the files.

---

### Post by 67GTA on 2007-03-25
I tried the right click>write to disc option and got the same error. It keeps telling me to insert a blank disc. My Gateway has combo drives. The top is listed as CD-RW/DVD+R (writer). The bottom drive is CD-ROM/DVD-ROM (reader). Every thing I have tried only gives me the HL-DT-STDVDRRW GWA-4164B(top drive) option. Both drives recognize all kinds of disc media, even blank CD's but not blank DVD's. I have no idea what is going on.

---

### Post by Drakkor on 2007-03-25
> The bottom drive is CD-ROM/DVD-ROM (reader)
Maybe that's your problem ?  You don't have a DVD writer ??

---

### Post by 67GTA on 2007-03-25
In my first post I stated that I had copied DVD's with Windows(no longer installed) and seemed like I used the bottom drive, but can't remember which now. Is it possible to be able to copy DVD's and not be able to write them? I assumed it would do both.

---

### Post by 67GTA on 2007-03-25
I was sure when I bought it that it would write CD and DVD. Something is not right. Here is the specs on my PC from Gateway:

CD / DVD
Optical Drive Type  What is this?
	DVD±RW Dual Layer
Optical Drive Read Speed 	16x (DVD) • 40x (CD)
Optical Drive Write Speed 	40x (CD-R) • 16x (DVD+R) • 16x (DVD-R)
Optical Drive ReWrite Speed 	24x (CD-RW) • 8x (DVD+RW) • 6x (DVD-RW)
2nd Optical Drive 	DVD-ROM
2nd Optical Drive Read Speed 	16x (DVD)

---

### Post by 67GTA on 2007-03-25
Something else of interest, when I insert a cd blank or not it will come up on my desktop as an icon and a pop up asking me what to do with it. This doesn't happen with dvd. It will if there is something on the dvd.

---

### Post by qamelian on 2007-03-25
> **67GTA said:**
> I am trying to burn a DVD ISO image with Gnomebaker. When I try it says [COLOR=Red]/dev/hda: media is not recognized as recordable DVD[/COLOR]. I have never done this with Linux(only cd images). I am using a DVD-R single layer 4.7 GB disc. I have two drives on my PC. I can't remember for sure because it has been a while, but I think with Windows I had to use the bottom tray to write DVD's. When I try to choose the drive, Gnomebaker will only let me choose the top tray. I know Ubuntu recognizes the bottom drive, because I watch DVD movies in it. I am not sure if it is hardware related or if I need to try another cd/dvd burner. Can anyone shed some light on this?

Why is it looking to /dev/hda for your DVD recorder? That device would normally be your first hard drive, unless you've done something unusual when cabling your drives. It might help resolve some confusion if you post the contents of /etc/fstab.

---

### Post by tagra123 on 2007-03-25
There were some updates that fixed this particular problem. Might check repositories and make sure updates is enabled.

I experienced this problem early with dapper on only one machine (hardware related) and it just went away after one of the updates, not exactly sure which one, but it was last year.  Actually I may have done a firmware update to the drive -- Sorry I just dont remember.  Don't give up you sould be able to make it work.

If all else fails -- try the command line.

This worked for troublesome +R media I once had

growisofs -dvd-compat -Z /dev/dvd=/path/to/myfile.iso



I

---

### Post by 67GTA on 2007-03-25
I have not changed anything since installation. I have not tried the command line method yet. etc/fstab output:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by 67GTA on 2007-03-25
Just tried to use the command line and got the same error. 

shawnr@fastback:~$ growisofs -dvd-compat -Z /dev/dvd=/home/shawnr/Desktop/foresi ght_9208_foresight-1.1-x86-dvd1.iso
:-( /dev/dvd: media is not recognized as recordable DVD: 0
shawnr@fastback:~$

I am using Memorex DVD-R (recordable)  8x-4.7GB-

---

### Post by tagra123 on 2007-03-25
Grab two cd of anything -- just make sure they have volume labels.  NOt which one is in the drives.

Next

Once both are in the drives. 

From the Menu : System-Administration-Diskmanager -- CDROM should be displayed and possibly a second one reading CDROM.

Click on each one and under General - not which  device is listed -- /dev/hda (my example) if you have two it could be  /dev/hda for one and /dev/hdb for the second.

NOw once you know these try this

Whichever one has to be the dvd -- l**ets say it's /dev/hdb**

Modify the command I gave earlier from this

growisofs -dvd-compat -Z /dev/dvd=/home/shawnr/Desktop/foresi ght_9208_foresight-1.1-x86-dvd1.iso

to this

growisofs -dvd-compat -Z** /dev/hdb**=/home/shawnr/Desktop/foresi ght_9208_foresight-1.1-x86-dvd1.iso


if it works post back and someone will tell you how to fix this. I think you could make/hack a symlink to avoid the problem altogether,

---

### Post by 67GTA on 2007-03-25
What  is the fstab_automount file? It differs from the etc/fstab. I also do not have ntfs on my hard drive. It is refering to hdb, which should be my second disc drive(reader).

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0       0

---

### Post by tagra123 on 2007-03-25
From the Menu : System-Administration-Diskmanager -- CDROM should be displayed and possibly a second one reading CDROM.
TRY THIS
From the Menu : System-Administration-Diskmanager -- CDROM should be displayed and possibly a second one reading CDROM

Click on each one and under General - not which device is listed -- /dev/hda (my example) if you have two it could be /dev/hda for one and /dev/hdb for the second.

NOw once you know these try this

My guess after looking at you fstab is that it has to be hdc or hdd

Whichever one has to be the dvd -- lets say it's /dev/hdc

growisofs -dvd-compat -Z **/dev/hdc**=/home/shawnr/Desktop/foresi ght_9208_foresight-1.1-x86-dvd1.iso

---

### Post by 67GTA on 2007-03-25
It lists hda and hdb. hda is the writer and hdb is the reader. Itried modifying the command and got the same error. I tried both drives with a blank dvd just for the heck of it. Maybe my drive is screwed up. 

shawnr@fastback:~$ growisofs -dvd-compact -Z /dev/hda=/home/shawnr/Desktop/fores ight_9208_foresight-1.1-x86-dvd1.iso
:-( /dev/hda: media is not recognized as recordable DVD: 0
shawnr@fastback:~$ growisofs -dvd-compact -Z /dev/hdb=/home/shawnr/Desktop/fores ight_9208_foresight-1.1-x86-dvd1.iso
:-( /dev/hdb: media is not recognized as recordable DVD: 0
shawnr@fastback:~$

---

### Post by 67GTA on 2007-03-25
I have a stupid question. Whatis the difference between DVD+R and DVD-R? When I tried the right click>write method it said that that DVD+R was supported, but did not mention DVD-R(which is what I'm using).

---

### Post by Drakkor on 2007-03-25
Yeah, my CD writer is hdc, and DVD writer is hdd

---

### Post by Drakkor on 2007-03-25
Most of the older stand alone dvd players will play DVD-R , whereas most of the newer players will play both, but I think DVD+R will have a higher recording speed.

---

### Post by 67GTA on 2007-03-25
Here is screenshots of diskmanager with ubuntu iso in top and super grub in bottom. It says dvd write is enabled for hda which is my writer, but itjust won't recognize the blank dvd's.
[ATTACH]28284[/ATTACH]
[ATTACH]28285[/ATTACH]

---

### Post by Drakkor on 2007-03-25
According to your screenshots hda, which is green for write DVD, is the one ? 
That's really weird that it's hda, which , in my dual boot is the primary windows partition.
and hdb, my second hard drive, is Ubuntu !

---

### Post by 67GTA on 2007-03-25
Actually I have a SATA(S.M.A.R.T.) hard drive. My partitions are listed as sda under linux.

---

### Post by Drakkor on 2007-03-25
Sorry for the flippant remark,lol , but actually not too (S.M.A.R.T.)  :)
Stupid hard drives !,lol :)

---

### Post by 67GTA on 2007-03-25
Yeah, had alot of trouble with that one when I first installed Ubuntu because I couldn't get anything to work with "hda".

---

### Post by 67GTA on 2007-03-26
I tried putting one of the dvd's in my daughter's PC (WIN XP) and it did not recognize it either. It may be the stinking dvd's. I will pick up a couple of good DVD-RW tomorrow and see what happens.

---

### Post by 67GTA on 2007-03-26
Well, still no luck. I tried with DVD+R and still didn't recognize the disc. Is there a Linux program that  I can use to test the CD/DVD drives with?

---

### Post by halitech on 2007-04-01
> **67GTA said:**
> The top is listed as CD-RW/DVD+R (writer). 

Are you trying to burn in the top drive or the bottom drive? looks like your top drive is your burner for both cd and dvd. If you are trying the top drive, it may be the media or the drive. Not sure of any programs to test the drive. have you tried new media yet?

---

