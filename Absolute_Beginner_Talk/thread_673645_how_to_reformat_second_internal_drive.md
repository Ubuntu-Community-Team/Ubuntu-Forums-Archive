---
title: "how to reformat second internal drive?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by neatokino on 2008-01-20
I've read a bunch of posts about using gparted, reformatting, etc., but I have some specific issues, and I hope someone here can  help me.

I installed a 200GB hard  as a second hd in my dual-boot XP/Gutsy PC.  The HD had seen duty as the principal hard drive in an old iMac, which was set up for dual booting Mac OSX and Gutsy PPC and is partitioned with a 6GB Mac OSX partition and a 179 GB ext3 partition.  

I'd love to wipe everything off of the drive and use it to as a media storage HD mostly for my music.  I suppose the best case scenario would be to have it accessible from Windows XP and Gutsy, though I rarely use XP and would be happy enough just to have it accessible for Gutsy.

What is the best way for me to wipe this hard drive completely clean and reformat it so it will mount up when I boot?    I have gparted, but with all the stuff that's already on the drive (there are 5 partitions in all, including the MacOS, ext3, hfs, hfs+ media/Mac OS, and 'unknown') I don't know how to use gparted to just wipe the whole drive clean and start over.

Oh, and when I run:  sudo fdisk -l    in the terminal, this is what I get:

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        7296    58572990    7  HPFS/NTFS
/dev/sda3            7297       13375    48829567+  83  Linux
/dev/sda4           13376       13618     1951897+   5  Extended
/dev/sda5           13376       13618     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


Thanks in advance!

Michael

---

### Post by Lvcoyote on 2008-01-20
Download killdisk, its bootable from a floppy.  When you run it it will show all the partitiions on the drive right below the name of the drive.  Just highlight the name of the drive and let it do its thing, it will basically return the drive to how it was when new.

---

### Post by neatokino on 2008-01-20
Thanks-- I don't have a floppy, but can I just run it in ubuntu on my primary drive???

---

### Post by logos34 on 2008-01-20
there's also a cd .iso
[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

---

### Post by Lvcoyote on 2008-01-20
Yes, if you dont have a floppy, use the ISO and boot from the CD....should be the same from there.

---

### Post by neatokino on 2008-01-20
Great, I can definitely download the iso and burn a cd to run it off of.  Now, once I wipe that disk clean, do I use gparted to format it as ext3 and go from there?  If so, is that process more or less self explanatory?

TIA again!

---

### Post by pavpan on 2008-01-21
Yes, should be self-explanatory. Hope you luck!

---

### Post by neatokino on 2008-01-21
Thanks again, everyone, for your help, but I'm still stuck.

I burned a killdisc, but when I run it, it only seems to see my primary hard drive, not the new one.  

If I boot the computer to Windows XP, the second drive also doesn't show up.

However, the drive DOES show up in Nautilus (or at least the partition that's formatted ext3), and I can access it, sort of:  it contains a file called 'lost and found.'   But I can't seem to do anything with the disk.

I burned a liveCD of Gparted, and it recognizes the new drive, and I was able to resize the ext3 partition (took hours), but there didn't seem to be any way to erase the disk or make it usable.

Once again, if I run sudo fdisk -l, I get the following:

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


The disk is there, it's recognized in some form or another by ubuntu if not Killdisk or XP, but I can't figure out how to mount it, reformat it, or erase it so I can use it for storage.  Any suggestions????

TIA

Michael

---

### Post by logos34 on 2008-01-21
What kind of disk is this, IDE or Sata?  If the former, is the jumper set for 'slave', and did you double check the bios hard disk detect settings? (should be set for 'auto', 'LBA').  That's probably not the issue since ubuntu sees the ext3, but I thought I'd mention it.

You could try 

> sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1

that will wipe the master boot record (first 446 bytes) AND the **partition table** that follows.  IF, that is, it can recognize the drive!

Or maybe [Darik's Boot and nuke]("http://dban.sourceforge.net/") can handle it.  Worth a try.

The lost+found folder is normal.  It always appears when you format anything ext3.

---

### Post by Lostincyberspace on 2008-01-21
sdb = sata logos.

you should just be able to unmount the drive and run gparted on ubuntu and be able to wipe it that way. if you don't have gparted you should look for it in synaptic.

---

### Post by logos34 on 2008-01-21
> **Lostincyberspace said:**
> sdb = sata logos.

Not necessarily.  Remember, since Feisty release Ubuntu has been using the libata scsi storage driver, so even IDE drives usually show up as 'sd_'.  (there are exceptions--as in my case--where a specific controller may cause the drives to still be designated as 'hd_')

---

### Post by neatokino on 2008-01-21
Thank you all for your help.  I was never able to completely erase and reformat the drive, but I did manage to make an 186GB partition and format it as ext3 and get it to mount, which is pretty much good enough.  I guess the old 10GB partition that had MacOS stuff on it is sort of lost in the shuffle somehow....

now, my next question is how to transfer music to this drive.  I have my music stored on a MacOS formatted firewire drive, and though the drive is recognized and readable on Ubuntu, I can't figure out how to transfer files from that external FW drive on to the new internal drive in my computer.  I apparently don't have permission to take those files off the FW drive and can't figure out how to do it.  Oh well... I'll do some searching, and if I can't figure it out, I'll put up another post on the forums.

thanks again to those who helped me!!!

---

