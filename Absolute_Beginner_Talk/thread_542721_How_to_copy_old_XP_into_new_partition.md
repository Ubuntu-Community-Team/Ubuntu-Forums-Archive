---
title: "How to copy old XP into new partition?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by bliffle on 2007-09-04
I've been running just fine for 6 months on the Feisty I installed. Almost everything I used under XP has been replaced by equivalent, or better, linux programs. 

But there are a couple reasons for having my old XP system bootable on the new big HDD that is mounted in my laptop. I figure that the easiest way is start with a new clean HDD, copy the XP system as the first partition, then copy the Feisty partition and setup Grub. I surmised that XP wants/needs to be the first partition on the HDD.

So all I have to do is copy that old XP from it's 12gb HDD to the new 80gb HDD in a right-sized partition. I've tried that with "pcopy", "dd" and "parted" and each one does the same thing: runs for about a half hour and then starts displaying read errors on the XP partition. If I let it run it will go for at least 2 days like this, with the disk address slowly advancing. When I kill the terminal session there is no apparent data on the target HDD.

I figure that there is no apparent output data because the copy program won't write the TOC or index data until the file data is complete.

I figure that the read IO errors are because the XP disk formatter doesn't actually format every disk track but only the TOC and that formatting writes are used as data is written to the disk, so any unused disk space remains unformatted and that's the chaotic way that pcopy or dd find it and they can't deal with it. 

Oh yeah, I've run "chkdsk /f" several times from XP until it stops reporting errors and it doesn't change the outcome.

Just recently I've discovered there's a thing called "partimage" with experimental NTFS support that may allow me to create an intermediary partition image and then from that the target partition. But will I run into the same IO read errors? Or will it understand that unformatted data is not within the TOC data areas of the NTFS?

And is "partimage" the only hope I have of getting what I want? Or is there something I'm missing in the use of "pcopy", "dd" and "parted"?

---

### Post by Officer Dibble on 2007-09-04
Just to clarify, you have a system that is booting soley from Ubuntu at the moment and you want to reintroduce an old XP partition you have stored on another drive or image somewhere. You want to do this so that you can dual boot between Ubuntu and XP.

Would that be a correct summary?

---

### Post by Gone fishing on 2007-09-04
I use the gparted live cd to clone XP PCs. Put both hard drives into a PC boot from the gparted live cd  and then use th gparted to copy and past the partition from one disk to another. After it is necessary to flag the newly copied partition as bootable again this can be done with the gparted live cd.

I suppose the gparted on the live ubuntu cd should work but I haven't tried it, the ubuntu version might be a little old.

---

### Post by tgalati4 on 2007-09-04
You can try the following:

>sudo su
# cp /dev/hdc2 /dev/hda2

This would make a copy from partition 2 on drive 2 to parition 2 on drive 1.  You obviously would have to modify the copy command to your situation.

You need to make sure that the target partition is the same size (or slightly bigger) than the source, otherwise you make get errors.

You can also copy entire disks as well:

# cp /dev/hda /dev/hdc

This will create a "ghost" image from one drive to the next. (including all partitions) Does windows XP do funky stuff to lock the operating system to a specific disk?  Probably.  They certainly lock it to the motherboard.  So don't expect windows to work properly with such a copy operation.  

Give it a try and let us know if windows boots and operates properly after such a transplant.

---

### Post by bliffle on 2007-09-04
> **Officer Dibble said:**
> Just to clarify, you have a system that is booting soley from Ubuntu at the moment and you want to reintroduce an old XP partition you have stored on another drive or image somewhere. You want to do this so that you can dual boot between Ubuntu and XP.

Would that be a correct summary?

Yes, I tried the ubuntu liveCD when I got it, then decided to install ubuntu on a new HDD I had handy (since there was no room on the old XP HDD) and so I did, and have run quite well with that system. I put the old XP HDD in a USB box so I could copy some data from it, and that worked quite well.

I foresee that I will have to use the XP occasionally, so rather than carry that old XP HDD around with me (and swap the internal laptop HDD) I would like to have both XP and ubuntu on one large HDD in a dual-boot configuration.

Seems simple enough; I'm sure there's a way to do it. But all the dual-boot articles I've read start with a resident XP and enough room on the HDD for an additional ubuntu partition.

---

### Post by Gone fishing on 2007-09-04
Does windows XP do funky stuff to lock the operating system to a specific disk? Probably

No - it doesn't - although you might need to reactivate.

You should be able to copy and past the XP partition from the 12 Gig hard drive on to the new drive and then install Ubuntu on the rest of the drive or copy and past that partition. I've cloned XP in this way several times.

---

### Post by bliffle on 2007-09-04
> **Gone fishing said:**
> Does windows XP do funky stuff to lock the operating system to a specific disk? Probably

No - it doesn't - although you might need to reactivate.

You should be able to copy and past the XP partition from the 12 Gig hard drive on to the new drive and then install Ubuntu on the rest of the drive or copy and past that partition. I've cloned XP in this way several times.

What is "reactivate"?

How did you "copy and paste" the XP partition? What utility?

Can you give specifics on how you've cloned XP in this way? Do you use the liveCD of Gparted?

---

### Post by Gone fishing on 2007-09-04
From the gparted live cd you can copy a partition and the paste it onto a different hard drive. Very handy if you have a PC setup as you want and don't want to go through the hassle of installing, patching and installing all the apps you need For Windows.

Activation a annoying process where by MS gives you permission to use an OS that you've all ready paid for. If you change bits of hardware MS may believe you have moved XP to a different PC and you may then need to re-activate.

---

### Post by bliffle on 2007-09-04
> **Gone fishing said:**
> From the gparted live cd you can copy a partition and the paste it onto a different hard drive. Very handy if you have a PC setup as you want and don't want to go through the hassle of installing, patching and installing all the apps you need For Windows.

Activation a annoying process where by MS gives you permission to use an OS that you've all ready paid for. If you change bits of hardware MS may believe you have moved XP to a different PC and you may then need to re-activate.

OK, so what I'm going to try  is this:

1-put the parted liveCD into the slimBay of the T40 (figuring that the liveCD will work better than the Gparted on the internal Travelstar HDD).

2-plug the old 12gb XP HDD in it's box into a USB port

3-plug the new 80gb target HDD into the other USB port

4-restart the T40 with the CD primary in the boot sequence.

5-find out where the 'copy'  function is in the Gparted GUI and start it.

I'll report back when it's done.

---

### Post by Gone fishing on 2007-09-04
Don't forget after you have copied and pasted the partition you will need to change the flags on the new hard drive to make it bootable.

USB port? not IDE or SATA?

---

### Post by bliffle on 2007-09-04
> **Gone fishing said:**
> ...

USB port? not IDE or SATA?

Yes, This is a laptop so I only have the one internal IDE slot for one HDD. But it has 2 USB ports and I've found that an IDE HDD in a USB box with a USB cable works very well.

OK, so I did steps 1-5, all of which went well and I did the "copy" and the "paste" buttons for the proper disks and that was fine. But when I tried the "apply" button it failed with this error (let's see how the HTML formatted response formats out):

GParted 0.3.4<BR><BR>
Libparted 1.7.1<BR><BR>
<TABLE border=0>
<TR>
<TD colspan=2>
<b>Copy /dev/sdb1 to /dev/sda2</b>&nbsp;&nbsp;00:01&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</TD>
</TR>
<TR>
<TD>&nbsp;&nbsp;&nbsp;&nbsp;</TD>
<TD>
<TABLE border=0>
<TR>
<TD colspan=2>
calibrate /dev/sda2&nbsp;&nbsp;00:01&nbsp;&nbsp;&nbsp;&nbsp;( SUCCES )
</TD>
</TR>
<TR>
<TD>&nbsp;&nbsp;&nbsp;&nbsp;</TD>
<TD>
<TABLE border=0>
<TR>
<TD colspan=2>
<i>path: /dev/sda2<BR />start: 65015055<BR />end: 132921809<BR />size: 67906755 (32.38 GiB)</i>
</TD>
</TR>
</TABLE>
</TD>
</TR>
</TABLE>
<TABLE border=0>
<TR>
<TD colspan=2>
calibrate copy of /dev/sdb1&nbsp;&nbsp;00:00&nbsp;&nbsp;&nbsp;&nbsp;( SUCCES )
</TD>
</TR>
<TR>
<TD>&nbsp;&nbsp;&nbsp;&nbsp;</TD>
<TD>
<TABLE border=0>
<TR>
<TD colspan=2>
<i>path: /dev/sda2<BR />start: 65015055<BR />end: 132921809<BR />size: 67906755 (32.38 GiB)</i>
</TD>
</TR>
</TABLE>
</TD>
</TR>
</TABLE>
<TABLE border=0>
<TR>
<TD colspan=2>
calibrate /dev/sdb1&nbsp;&nbsp;00:00&nbsp;&nbsp;&nbsp;&nbsp;( SUCCES )
</TD>
</TR>
<TR>
<TD>&nbsp;&nbsp;&nbsp;&nbsp;</TD>
<TD>
<TABLE border=0>
<TR>
<TD colspan=2>
<i>path: /dev/sdb1<BR />start: 63<BR />end: 23556959<BR />size: 23556897 (11.23 GiB)</i>
</TD>
</TR>
</TABLE>
</TD>
</TR>
</TABLE>
<TABLE border=0>
<TR>
<TD colspan=2>
check filesystem on /dev/sdb1 for errors and (if possible) fix them&nbsp;&nbsp;00:00&nbsp;&nbsp;&nbsp;&nbsp;( ERROR )
</TD>
</TR>
<TR>
<TD>&nbsp;&nbsp;&nbsp;&nbsp;</TD>
<TD>
<TABLE border=0>
<TR>
<TD colspan=2>
<b><i>ntfsresize -P -i -f -v /dev/sdb1</i></b>
</TD>
</TR>
<TR>
<TD>&nbsp;&nbsp;&nbsp;&nbsp;</TD>
<TD>
<TABLE border=0>
<TR>
<TD colspan=2>
<i>ntfsresize v1.13.1.1 (libntfs 9:0:0)<BR />Device name        : /dev/sdb1<BR />NTFS volume version: 3.1<BR />Cluster size       : 4096 bytes<BR />Current volume size: 12061131264 bytes (12062 MB)<BR />Current device size: 12061131264 bytes (12062 MB)<BR />Checking for bad sectors ...<BR />Bad cluster:   0x31ab - 0x31ab    (1)<BR />Bad cluster: 0x2c26e0 - 0x2c26e0    (1)<BR />ERROR: This software has detected that the disk has at least 2 bad sectors.<BR />****************************************************************************<BR />* WARNING: The disk has bad sector. This means physical damage on the disk *<BR />* surface caused by deterioration, manufacturing faults or other reason.   *<BR />* The reliability of the disk may stay stable or degrade fast. We suggest  *<BR />* making a full backup urgently by running &apos;ntfsclone --rescue ...&apos; then   *<BR />* run &apos;chkdsk /f /r&apos; on Windows and rebooot it TWICE! Then you can resize  *<BR />* NTFS safely by additionally using the --bad-sectors option of ntfsresize.*<BR />****************************************************************************<BR /></i>
</TD>
</TR>
</TABLE>
</TD>
</TR>
</TABLE>
</TD>
</TR>
</TABLE>
</TD>
</TR>
</TABLE>
<BR>========================================<BR><BR>


Sounds like I gotta remount that old XP in the computer again and do some more "chkdsk" and reboot action.

So then I fired up my ubuntu system again and tried "partimage", like so:


umount /dev/sdc1     * to allow partimage to access it, as I discovered *

sudo partimage save /dev/sdc1 /dev/sdb2/BK570image  * to run the partimage pgm *

and I got this response:

*Cannot create temp file          
*                    &#9474; [/dev/sdb2/pi950e1161.tmp]. Please,   *&#9474;                    ls
*                    &#9474; check there is space enough and you   *&#9474;                    
*                    &#9474; have access rights. 
*

So I looked at the access stuff for the /dev/sdb2, like so:

ls -l /dev/sdb2

and got :

brw-rw---- 1 root plugdev 8, 18 2007-09-04 13:08 /dev/sdb2

I don't know what to do with this trial.

---

### Post by bliffle on 2007-09-05
This is getting ridiculous. I ran the 'chkdsk /f' routine many times on XP and I still get errors from parted.

---

### Post by bliffle on 2007-09-05
Now I'm copying the old HDD to the new one on XP using a program called "XXCLONE", which doesn't do sector copies but file copies instead. Afterwards it fixes up the system stuff and MBRs and boot records , etc. 

I'm thinking that's a better way to copy a HDD with known surface defects, because the file data can either be recovered thru retries or discarded (!) as unimportant since the system is running.

When that's done (later today) I'll proceed onward with bringing that up on the old computer and installing ubuntu and dualboot.

---

### Post by bliffle on 2007-09-05
Well, I tried to bringup the copied XP system on the  80g HDD and it didn't work, so I better solve that problem first.

XXCLONE includes options for setting the BOOT stuff on the 'target' HDD and I may have to redo that.

---

### Post by bliffle on 2007-09-05
New XP system (copy of old system) won't bootup. Blinking cursor in UL of screen.

Damn!

---

### Post by bliffle on 2007-09-06
OK, I reran the XXCLONE program. This time I made sure that I employed
the "Cool Tools" to make it bootable and write the MBR, etc. then I
ran the 5 hour copy again. But I still can't boot the new 80g HDD
either from the boot menu list that presents at boot time, or by
plugging the 80g into the laptop directly. I get this msg:

"Windows could not start because of a computer disk hardware
configuration problem.
Could not read from the selected boot disk. Check boot path and disk
hardware.
Please check the windows documentation about hardware disk
configuration and your hardware reference manuals for additional
information."

Since this is a 2.5" Travelstar IBM HDD (IDE) I'm not aware that
there's any of the old master/slave jumpering that has to be done with
3.5" HDDs. Also, I've upgraded laptop drives previously using Norton
Ghost, which I detest because it seems to upgrade the drive but screws
up the installed user states.

That target HDD (80gb) was initialized with the linux 'Gparted'
standalone liveCD program, which is supposed to be just like Partition
Magic. It's always worked before.

Maybe I should try the copy with Acronis. But it seems to me that it's
just some trivial matter involving the boot data on the 80g HDD and
shouldn't require that.

If it's the USB box that I used, then I can try this another way since
I have a docking station for the laptop (an old IBM 570) that I can
put the new HDD into for the copy/boot initialization. Think I'll try
that next, since I don't have to swap the drive in/out of the laptop
itself, which is a nuisance (sometimes a pin gets bent!).

---

### Post by bliffle on 2007-09-06
Acronis worked just fine. And it was quite fast.

Now I have to figure how to install kubuntu on this old IBM 570. I have the 7.10 CD but the 570 doesn't want to boot off the USB CD player. I guess I could partition the 80g HDD and copy the CD onto a partition, then rig the boot.ini on XP to put that in the boot menu.

---

### Post by bliffle on 2007-09-18
Gparted copied the XP partition nicely, but I can't boot it even tho it's the first partition on the new drive.

Can I make it bootable after the copy with GParted?

The target HDD is in a USB external 2.5" box. Once it's bootable I'll mount it in the laptop as the internal drive and add a ubuntu partition.

I suppose I could do it the other way and put the new HDD in the laptop and copy from the old HDD in a USB box, but I don't see how that would make the target HDD bootable.

I couldn't solve this problem with the GRUB liveCD nor with the "Universal boot CD".

Seems to me we used to be able to solve these boot problems easily with the old "fdisk /mbr" option with old windows systems, and that win2k had a "recovery console" to do the same thing.

---

### Post by bliffle on 2007-09-20
Well, I think I got everything configured and copied OK (the target HDD has all the right folders and files for the XP and the Kubuntu systems, both, but they burp and barf when I try to bootup, until I use the GRUB CD to start).

I'm going to say that the target HDD is bad and bailout on this project. Later I'll run a standalone analysis/delete program when I have a little time to spare. In the meantime I'll just get a fresh new travelstar from Frys (only about $50 right now). Also, I'm not going to bid/buy any more eBay HDD auctions: I've been stung too many times, now, either with bad discs, non-delivery, or SATA drives when I need PATA (I have 2-3 SATAs stockpiled for a future T61!) Too much trouble to struggle with guys thru email and USPS, etc., I just write them off. HDDs are the only thing I've had persistent problems with in 8 years of eBay buying.

---

