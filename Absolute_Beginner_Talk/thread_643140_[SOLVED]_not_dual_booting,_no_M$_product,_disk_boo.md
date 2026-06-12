---
title: "[SOLVED] not dual booting, no M$ product, disk boot blues"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-12-17
There are NO microsoft products involved here, so posts/threads about dual-booting are not what I'm after.

I had a 40 gig drive I used as my boot disk, which was gutsy 7.10. I got a new drive, 320 gig. It is running Gutsy perfectly.

The 40 gig got fubar'd due to putting a win98 disk as pri/slave. Since the harm, I removed the win98 drive. And I curse the day I had M$ near my OS.

I have tried SuperGrub to fix the mbr and to reinstall grub. I just can't seem to get the hang of that. 

All I want to do is remove the files from the 40 gig /home to my new 320 gig drive.

When the 40gig is on the ide cable, if the bios senses it, I cannot boot from the 320 gig! Why? How can I resolve this. BUT bottom line, all I want to do is move the /home files from the 40 gig to the 320 gig. DD and G4L no longer useful ideas, I've tried that already. Had to reinstall due to partition craziness.

---

### Post by DrOlaf on 2007-12-17
I had a similar problem (although I never figured out how my disk got fubared) and the only way I was able to mount and read the drive was to take it out of the PC and put it into an external housing that I then connected via USB. Then I was able to copy all my files off without a hitch.

---

### Post by Mark_in_Hollywood on 2007-12-17
I have previously put the drive in a usb cradle. No Go!. lsusb shows the cradle, but the disk is a no-show.

---

### Post by cyclefiend2000 on 2007-12-17
sounds like the hd may have failed. i had one fail on me recently. i cant get anything to recognize it now. not sure there is anyway to get the files off of it.

---

### Post by perixx on 2007-12-17
I don't know if you didn't already try it, but - do you have W98 boot-disk at hand? Then you could try 'fdisk /mbr' on your (primary W98-hdd), but best pull the plug of your Linux-hdd for that.

Another thing - you can't select your other Linux-hdd from your Bios-bootmenu (via F8), I suppose?

If your Win-hdd has decided to blow up, because you've accidentially put the 32GB disk-size-limitation jumper in place, you could revive it with 'HDAT2' - this way you can overcome size-limitations and remove HPA-entries from the drive. Funny, but I suddenly had such an entry after playing around a bit with 2 hdd's, although I was pretty sure, not to have plugged the 32GB-jumper. I then had to use HDAT2 + (!) setting low-LBA before resetting the drive.*** 

If that doesn't help, you can still try to zero out the MBR with 'MHDD' (or some 'dd' command) and do 'fdisk /mbr' afterwards.***

Or you try out SGD (super grub disk)....

*** I can't guarantee for your W98-installation still being intact after using those tools...!

perixx

---

### Post by 720iD on 2007-12-17
if you booted a rescue disk to ram with both drives wired up could you see both drives?

---

### Post by jken146 on 2007-12-17
Have you checked the jumpers on the drives?

---

### Post by Mark_in_Hollywood on 2007-12-17
sounds like the hd may have failed. i had one fail on me recently. i cant get anything to recognize it now. not sure there is anyway to get the files off of it.
[B]
Possible, but unlikely, the mbr/fstab are more likely. The disk is found by the BIOS. [/B]

===========================

I don't know if you didn't already try it, but - do you have W98 boot-disk at hand? Then you could try 'fdisk /mbr' on your (primary W98-hdd), but best pull the plug of your Linux-hdd for that.
[B]
I would try SuperGrub before that (and I have), no luck as yet.[/B]

Another thing - you can't select your other Linux-hdd from your Bios-bootmenu (via F, I suppose?

If your Win-hdd has decided to blow up, because you've accidentially put the 32GB disk-size-limitation jumper in place, you could revive it with 'HDAT2' - this way you can overcome size-limitations and remove HPA-entries from the drive. Funny, but I suddenly had such an entry after playing around a bit with 2 hdd's, although I was pretty sure, not to have plugged the 32GB-jumper. I then had to use HDAT2 + (!) setting low-LBA before resetting the drive.***
[B]
Not the case, the drive is always 40gig[/B]

If that doesn't help, you can still try to zero out the MBR with 'MHDD' (or some 'dd' command) and do 'fdisk /mbr' afterwards.***

Or you try out SGD (super grub disk)....

**Been there, done that!**

*** I can't guarantee for your W98-installation still being intact after using those tools...!

=================
if you booted a rescue disk to ram with both drives wired up could you see both drives?

**yes, BIOS, "sees" the drive, but it isn't possible to access it; i.e., the OS doesn't "see" it.**

=================

Have you checked the jumpers on the drives?

**When the 40 gig is in the usb cradle, it has been set as Master/Slave/CS and no jumpers at all. No luck!**

---

### Post by 720iD on 2007-12-17
> **Mark_in_Hollywood said:**
> 
=================
if you booted a rescue disk to ram with both drives wired up could you see both drives?

**yes, BIOS, "sees" the drive, but it isn't possible to access it; i.e., the OS doesn't "see" it.**

so boot a live cd to ram [i.e. puppy/ clonezilla-gparted/ dsl] and get the job done. if you only want the data off the 40G.

---

### Post by Mark_in_Hollywood on 2007-12-17
> **720iD said:**
> so boot a live cd to ram [i.e. puppy/ clonezilla-gparted/ dsl] and get the job done. if you only want the data off the 40G.

How did we get so lost . . . OK, the purpose of this post, is to find a way, using a usb cradle if possible, but attaching the 40gig (former pri-slave) to the cable as primary slave (probably CS), if there is no other way and getting the /home off the drive.

I have already put the 40 gig drive on the ide cable as pri-slave. When this drive is attached to the "computer" that way, it prevents the pri-master from booting, i.e., no LiveCD works. I have SuperGrub, but so far it has been unable to fix either/or the mbr and grub and fstab or some combination.

Any ideas about that?

---

### Post by louieb on 2007-12-17
The fact that BIOS sees the drive means the controller card on the drive still works. The platters or heads inside may be what crapped out. 
Theres an old trick that will sometimes revive an old drive long enough to get the data copied off.  that is to wrap it in plastic to keep the moisture off and put in  the freezer overnight.  Take it out put it in your USB enclosure and hope for the best. 
Might see if [Tom's Hardware Forums]("http://www.tomshardware.com/forum/") has any other ideas.

---

### Post by Mark_in_Hollywood on 2007-12-17
OK, the deep-freeze. Thanks. I'm closing this thread for now.

---

### Post by 720iD on 2007-12-18
how did you solve this?

---

### Post by 720iD on 2007-12-18
oh i see! 

so what happens if you set the 40G as master and the 300G as slave?

---

### Post by perixx on 2007-12-18
well then, 

all I can suggest now is to use a native W98/DOS 7.x bootdisk and start fdisk, to see if there are still partitions recognized (you can also use gparted for that (Boot live-CD from secondary IDE-port, if connecting HDD together with it on the primary doesn't work).

You could also try BartPE-bootdisk, to access your drive, btw.
If there are still partitions found, do fdisk /mbr with the W98 disk (with the alone 40GB drive connected to the system). 

Last hope IMO: use some recovery tool (like Easyrecovery). Or get your HD to Ontrack ^^...

Another idea comes to my mind: if you used the 40gig-drive as slave in your system, Grub might have cancelled it's boot flag; you should also check this, if you look for partitions with fdisk, sfdisk or gparted... but either way, the partitions **should **be still there.


perixx

---

### Post by rkd on 2007-12-18
If the problem is that the partition table somehow got damaged, you might be able to recover it with testdisk.  Install it from the repositories.

---

### Post by 720iD on 2007-12-18
> **rkd said:**
> If the problem is that the partition table somehow got damaged, you might be able to recover it with testdisk.  Install it from the repositories.
he is not able to boot the operating system while the drive is wired up.

---

### Post by rkd on 2007-12-18
He said that when he put the drive in an external USB box, he could boot from the other disk.  Does testdisk not work with disks attached via USB?  If not, then you are right that my suggestion won't help.

---

### Post by louieb on 2007-12-18
> **Mark_in_Hollywood said:**
> OK, the deep-freeze. Thanks. I'm closing this thread for now.
You think I'm pulling you leg.


[Freeze your hard drive to recover data: Myth or reality? - [Geeks are Sexy] technology news]("http://geeksaresexy.blogspot.com/2006/01/freeze-your-hard-drive-to-recover-data.html")

[http://www.everything2.com/index.pl?node_id=1374232](http://www.everything2.com/index.pl?node_id=1374232)

:lolflag: And last but not least this guy went overboard with the idea.
[http://www.hardforum.com/showthread.php?p=1028112728](http://www.hardforum.com/showthread.php?p=1028112728)

---

### Post by 720iD on 2007-12-18
this thread is fun! lmao

---

