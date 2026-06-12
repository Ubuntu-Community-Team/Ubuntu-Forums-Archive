---
title: "Dual Boot, Grub - Please help"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Emceay on 2006-07-09
Hello, I've been using ubuntu for a day. I'm entirely fresh to linux, but it's stolen my heart and I want to dual boot it with XP so I can use cubase/cs2 and play games.
I jumped through some hoops earlier and got the ATI drivers working.

My XP is installed on a SATA and ubuntu got an entire IDE for it's install. The SATA drive has never been first to start and doesn't detect on startup unless I change the boot order in BIOS.
I just want these two OSes to co-exist with separate harddrives. Ubuntu was installed second. I don't care which one starts first, I just want the choice to pick when it starts.

I read previous postings with a grub edit. I copied all of Buzz's code that didn't match my menu.lst and gave it a restart.
The grub menu worked, and windows was an option. However, when I picked it the screen showed the options: 
> Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1

It did nothing else, it just hangs. Could someone help me fix this so I can move on to configuring my soundcard?

---

### Post by Emceay on 2006-07-09
My menu.lst thus far:
> 
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 (i'm guessing my password was the gibberish here?)
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


---

### Post by Nonno Bassotto on 2006-07-09
it seems that windows needs to think it is on the first hard drive. read this post
[http://www.ubuntuforums.org/showthread.php?t=210595&highlight=sata+sda](http://www.ubuntuforums.org/showthread.php?t=210595&highlight=sata+sda)
in particular Indroth reply.

---

### Post by Emceay on 2006-07-09
Check this out, when I opened device.map it had no entries. What am I supposed to do with that...? Otherwise this thread seems right on point.

*Scratch that, in a display of my noob-ness I forgot to actually enter the directory before looking for device.map*

---

### Post by Emceay on 2006-07-09
Ooookay..
The menu definitely shows up but if I pick windows it now goes further but instead now stops and says "ntldr is missing, ctrl-alt-del to restart".
If I set the SATA to boot first I get the same message.

Now I'm beginning to worry that my XP installation has been mysteriously locked out permanently.

Any Ideas on how to solve this?

---

### Post by molly_001 on 2006-07-09
Hopefully you made a back-up of 100% of your data from the Windows installation before beginning the Ubuntu install.

In either case, GAG Boot Manager can very likely come to your rescue.
Here: [http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

---

### Post by Emceay on 2006-07-09
Alright, I'm out of CDRs and I don't have an FDD.
Does that disk read error/ntldr missing message mean my windows drive is nuked? My OSes are on separate HDDs, so how could I have corrupted the MBR? Is there another solution to get windows to boot or is it all in the hands of a program I can't use?

btw, is there a way to make GAG run from a USB key at startup?

---

### Post by molly_001 on 2006-07-09
I do not believe there is a USB key bootable version.

You should get a CDR and try GAG though -- it has saved many in such a situation.

it's impossible to say for now if you are recoverable, but since your NTFS partition was on a separate drive, it is probably merely a matter of repairing the MBR.

---

### Post by confused57 on 2006-07-09
In your Windows menu.lst entry, you could try rootnoverify (hd1,0).

If this doesn't work, it sounds like your Windows mbr may be corrupted...if you have the Windows installation CD(not a recovery CD), boot up with it and press "r", then enter     fixmbr
I'm not sure, but you may want to disconnect your IDE drive when doing this or set the SATA drive to boot first.
This should repair the Windows mbr and allow it to boot, hopefully using grub from your IDE drive.

See if there is anything in this thread that may help:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Edit:  If it were my system, I would:
1.) Use the Windows install CD to fixmbr on the SATA drive(set bios to boot to it first)
2.) Once the mbr is repaired, see if Windows will boot, if it does:
3.) Set your bios to boot first from the IDE drive, reboot, and see if Windows can be booted from grub.

Your menu.lst Windows entry looks fine for doing this, but you still might want to try rootnoverify.

---

### Post by molly_001 on 2006-07-09
To confused57 --

Hello again.  That was an excellent post of yours from May 21, 2006.
It covers dual booting with two IDE hard disk drives.
Might I be able to include a link on my Vista+Linux dual boot page (see sig below) -- a link to your post?  My site for now only covers specifically single hard disk drive installations.

Thanks - just let me know.

---

### Post by confused57 on 2006-07-09
> **molly_001 said:**
> To confused57 --

Hello again.  That was an excellent post of yours from May 21, 2006.
It covers dual booting with two IDE hard disk drives.
Might I be able to include a link on my Vista+Linux dual boot page (see sig below) -- a link to your post?  My site for now only covers specifically single hard disk drive installations.

Thanks - just let me know.

Sure, feel free to do so...thanks for the endorsement.  I have 2 computers set up this way, I just prefer grub not being installed on the Windows mbr.

---

### Post by Emceay on 2006-07-09
Thanks for all your help!
I still haven't gotten it running, but I definitely have options to try. At least I'm not totally *** out, i'm writing this post using ubuntu.
Once again, thanks; hopefully I can sort this out once I get my hands on a disc.

---

### Post by molly_001 on 2006-07-09
confused57 --

I think many folks will share your desire to keep them on separate physical drives.

I have updated the introduction by adding a link to your May 21 post (properly credited to you), and have also updated your entry on my 'Acknowledgements' page, where you had previously been cited for your helpfulness.

Oddly enough, the page is now the top search entry returned by Google for the contextual search entry of: +dual +boot +vista +ubuntu.
This was unexpected.

It is also the third entry returned for +dual +boot +vista +linux
so your information will be particularly helpful.

By the way, do you have a web site?

Thanks.

---

### Post by confused57 on 2006-07-09
> **Emceay said:**
> Thanks for all your help!
I still haven't gotten it running, but I definitely have options to try. At least I'm not totally *** out, i'm writing this post using ubuntu.
Once again, thanks; hopefully I can sort this out once I get my hands on a disc.

All is not lost...if you can't find a Windows install CD and you have a floppy drive, you can create a Win98 boot disk:
[http://www.bootdisk.com/](http://www.bootdisk.com/)

You can repair the Windows XP mbr using the Win98 boot floppy, it's a different command though...fdisk /mbr

Also, while in Ubuntu, see what the output of these are:
```
sudo fdisk -l
```
The -l is a small "L"

and
```
cat /etc/fstab
```

---

### Post by Emceay on 2006-07-10
Yo, I pulled the FDD from my parent's PC, so I'm about to throw GAG on it. Should that fail, fixmbr is next. I did a sudo fdisk -l:
> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 15 MB, 15990784 bytes
1 heads, 31 sectors/track, 1007 cylinders
Units = cylinders of 31 * 512 = 15872 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1          560236     1128928     8814725+   3  XENIX usr
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1, 0, 4) logical=(560235, 0, 19)
Partition 1 has different physical/logical endings:
     phys=(1, 1, 5) logical=(1128927, 0, 17)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      594062     1196579     9339021+  13  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(1, 1, 17) logical=(594061, 0, 5)
Partition 2 has different physical/logical endings:
     phys=(1, 1, 21) logical=(1196578, 0, 20)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      627887     1264230     9863317+  23  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(1, 1, 33) logical=(627886, 0, 22)
Partition 3 has different physical/logical endings:
     phys=(1, 1, 37) logical=(1264229, 0, 23)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?       97297     1644804    23986364   33  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(1, 1, 49) logical=(97296, 0, 17)
Partition 4 has different physical/logical endings:
     phys=(1, 1, 53) logical=(1644803, 0, 27)
Partition 4 does not end on cylinder boundary.

fstab returned this:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 15 MB, 15990784 bytes
1 heads, 31 sectors/track, 1007 cylinders
Units = cylinders of 31 * 512 = 15872 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1          560236     1128928     8814725+   3  XENIX usr
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1, 0, 4) logical=(560235, 0, 19)
Partition 1 has different physical/logical endings:
     phys=(1, 1, 5) logical=(1128927, 0, 17)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      594062     1196579     9339021+  13  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(1, 1, 17) logical=(594061, 0, 5)
Partition 2 has different physical/logical endings:
     phys=(1, 1, 21) logical=(1196578, 0, 20)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      627887     1264230     9863317+  23  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(1, 1, 33) logical=(627886, 0, 22)
Partition 3 has different physical/logical endings:
     phys=(1, 1, 37) logical=(1264229, 0, 23)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?       97297     1644804    23986364   33  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(1, 1, 49) logical=(97296, 0, 17)
Partition 4 has different physical/logical endings:
     phys=(1, 1, 53) logical=(1644803, 0, 27)
Partition 4 does not end on cylinder boundary.


---

### Post by Emceay on 2006-07-10
I went through the GAG install, when I got to my partitions, only the linux physical and logical partitions showed. No SATA selection.. I tried to make a boot to ubuntu using the partitions available, but when I got back to GAG's OS selection screen, picking ubuntu wouldn't allow it. Said something about sectors. Even more confused :| Any ideas why GAG would fail like that?
Going to give fixmbr a shot from an XP install CD. Last chance - fingers crossed.

---

### Post by Emceay on 2006-07-10
My first cup of ubuntu is tasting mighty bitter.

GAG just couldn't seem to detect my windows or ubuntu installs.
FixMBR made it so I couldn't access either at all anymore.
Now I'm posting from the liveCD version of ubuntu.

It looks like I'm going to have to reinstall them both. I can't help but wonder if there's still some way to fix all this because as soon as I turn off the live CD, my comp will be a pile of junk again.

I really thought that since my operating systems were on separate harddrives I wouldn't run across this problem. I stand corrected.

If you're new to ubuntu/linux and you're unsure if your data will be safe, the answer is no. 6 hours and two drives are toast.

To anyone that knows how to recover after this kind of thing happens, your suggestions are greatly appreciated. I don't smoke, but I'm going to go have a cigarette. :mad:

---

### Post by molly_001 on 2006-07-10
I'm sorry that is the state of affairs.  I do understand how desparately frustrating that can be.  At my first install attempt of putting Ubuntu onto a volume with an existing Windows XP install, the same exact thing happened for me.  (I was using only a single hard drive.)  GAG was never able to assist, fixmbr didn't work, nothing booted.  So I needed to start from scratch, reinstalling both OS from ground zero.  Fortunately, before this ill-fated operation, I had at the time backed up 100% of my data just before putting my fingers onto that tempting Ubuntu LiveCD for the first time.  I had even backed up my original MBR!  (But it couldn't restore, so that, too, was a failed attempt to get my machine back.)

The second time around, I slowed things down.  I read several guides and got it right.  I know that I didn't do anything incorrectly on the first install attempt, but suffice it to say that the installer for the LiveCD has its faults and isn't perfected.  Nonetheless, it's a brilliant solution for most users.

I now have a dual boot XP + Ubuntu with a separate /home partition -- so that even if disaster occurs and I lose Ubuntu (which I love), I won't lose any data that I created using Ubuntu.  I also have a shared FAT32 partition which is read/writeable to both Windows and Ubuntu, so its shared data space.

Nonetheless I still use NIT BackIT! Now 4.0 to backup my entire Windows-side data every night ... onto a second, separate hard drive which has no OS installed on it at all.

I have seen the gurus here save people in your situation.  But it doesn't always work.  I'm living proof of that, having even backed up my MBR at the time when Windows was the only OS on the volume.

But, here I am.  Ubuntu is so much better than Windows, I won't go back!  Let me know if I can be of assistance.

---

### Post by Emceay on 2006-07-10
I'm with you, Molly. A beer and cig later, I've had time to vent and I've decided that even though this is a major setback. I still want to become a permanent linux user and I will sip this bitterness until it turns sweet. I've reinstalled ubuntu and reinstalled ATI drivers, back to scratch.

Here's a question though: Do you think it's possible that I could get ubuntu to mount my windows SATA drive so I can read it's contents? Or is that something that requires an MBR/working OS?

If I can't have windows back, I'd like to emulate everything that wasn't a game if possible.

I backed everything up before I started this whole campaign, but I had programs that won't be so lucky. Hopefully linux can bridge the gap I now have between drives, as my SATA is useless without an OS tapping it.

---

### Post by confused57 on 2006-07-10
Sorry it didn't work out, you can mount a Windows drive from Ubuntu:
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

Maybe you could try fixing the mbr on the SATA drive again, this time disconnect the IDE drive just to be on the safe side.  As I mentioned before, you can't use a Windows Recovery CD, it has to be a Windows Install CD.

I don't know if case matters in XP recovery, but I saw you had "fixmbr" in an earlier post as FixMBR...all instructions I've seen have had it all lowercase.
Good Luck.

---

