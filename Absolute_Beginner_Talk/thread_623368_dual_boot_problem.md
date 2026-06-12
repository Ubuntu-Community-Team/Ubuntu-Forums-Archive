---
title: "dual boot problem"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by rotithor on 2007-11-25
I have a HP Pavillion dv5163cl laptop and had windows XP. While installing Feisty Fawn I accidently  erased windows and had one hard disk partition used by ubuntu /dev/sda1 which was 71 GB. To dual boot, I used gpartd live CD and created following partitions:
Primary partition #1: (/dev/sda3): NTFS 34.18GB 
/dev/sda1: 37.46 GB EXT3 basically that shrunk ubuntu partition
Now I try to install XP hoping it gets installed in NTFS partition, but when it starts to load windows it says: set up did not find any hard drives installed on the computer and can't continue (F3 for exit)
How can I get windows set up to see the NTFS partition so it can install windows XP there?
Please point me to steps I need to follow so I can get it installed

Another issue I have faced with Ubuntu installation is that when I type text from keyboard my cursor jumps around sometimes randomly somewhere on previous text; how can I avoid this?lp

Will greatly appreciate help, I want to use more Ubuntu in the future and dual boot provides me that oppty.

Many thanks in advance
Hemant

---

### Post by bluepowder7 on 2007-11-25
you have a SATA drive in that laptop?  and, you don't have a floppy drive, right?  WinXP doesn't recognize SATA drives on its own and needs to have drivers installed during the initial blue-screen thingy - at the bottom, it says "Press F6 to install drivers" or something like that.  RAID / SATA drivers is what it likely needs.


regarding the cursor - it's possible that your hands are touching the touchpad surface as you type?

---

### Post by rotithor on 2007-11-25
Its an IDE drive not a SATA drive for this machine; that should have a driver in th window installation, right? what else could cause windows installation to not see the NTFS partition? does it matter if I crated NTFS partition before the EXT3 partition? does it need to have a specific name?


Thanks
Hemant

---

### Post by bluepowder7 on 2007-11-25
/dev/sda means SATA (/dev/hda means IDE)
hp.com says your laptop has an 80gig SATA drive
i'm not sure how to install XP on a laptop with SATA and no floppy drive

it's certainly not about XP being unable to see partitions.  i was installing 2k and xp on a SATA drive that had ext2 partitions, and windows saw them as "i dunno what that is, but it's a partition of some kind"

---

### Post by Pumalite on 2007-11-25
Usually Windows requires the whole drive formatted ntfs to install. Then you use Gparted Live CD to resize the XP partition. Then you install Ubuntu.

---

### Post by asaz989 on 2007-11-25
Generally it's a lot easier to install Ubuntu as a second OS than Windows; even if you succeed at this, you'll probably have the problem of the Windows bootloader not being able to load Ubuntu without some config file editing.

It looks like you've just started with Ubuntu, so I'd recommend starting over: installing only Windows XP, then installing Ubuntu after that, being careful not to overwrite the Windows. Here's the step-by-step I went through:

[LIST=1]
[*]Repartition your HD as one big partition with a LiveCD/GParted.
[*]Use your Windows XP recovery CD to make your hard drive XP-only.
[*]In Windows, run the disk defragmentation tool (Start Menu/Accessories/System tools). That'll keep your XP file nice and clustered together on the hard drive.
[*]Give the (currently only) partition a memorable name.
[*]Reboot from the Live CD; make a new partition or two for Ubuntu, and just make sure that you don't make your memorably-named XP partition into the root (/) or swap partitions by mistake, as Ubuntu will be putting stuff in there.
[/LIST]

Then just move all of your backups back to wherever they should be. It'll take some time, but it's probably easier than installing XP as a second OS.

---

### Post by zippy028 on 2007-11-25
What I would do in this case is use gparted or whatever tool you choose and format the windows partition to FAT32 and then XP should recognize it and you can change the format to NTFS during the XP install.. I always really liked using older versions of Mandrake Linux version 8 or 9, to do partitioning as you can set up the HDD and then bail out of the install and Mandrake has always had a nice partitioner.

---

### Post by bluepowder7 on 2007-11-25
do me a favour to satisfy my curiosity.

reboot, and when the computer is JUST starting, hit Del or F8 or whatever to get into BIOS, and tell us what the BIOS is reporting under hard drives.  copy down as much detail as you can.

---

### Post by rotithor on 2007-11-25
Yes you are right, its SATA. In the BIOS its says: Phoenix BIOS ver F.09 and says SATA support  [Enabled]. The HP did not come with recovery disks and they had put recovery on a disk partition and I did not create recovery disks when Ubuntu erased the windows XP. I am loading XP from a XP distribution I have. like you indicted, If I press F6 during windows set up; it looks for a floppy which I don't have. Will converting first partition to FAT 32 help at al as someone suggested? If its a SATA driver issue I am not sure that it will but will try if there is hope....short of that, I am not sure I can dual boot this; 

Also, the cursor jumping happens even if I don't touch the pad, not sure if that is a config/setting issue for keyboard or something else; other than Ubuntu seems to work well.

Thanks for your suggestions.

Hemant

---

### Post by bluepowder7 on 2007-11-25
i'm 99% sure that WinXP isn't set up to handle SATA without a driver, and it's silly enough to insist on loading SATA / RAID drivers from a floppy (and not a USB drive or whatnot).  also, to make life easier for you, you'd need to download the SATA / RAID drivers from HP or whoever makes the motherboard (like Asus or Intel or MSI or whoever).  even if you did have the drivers, you have no floppy drive.  you could try to see if the mobo has a floppy connector on it (a screwdriver will come in handy to take apart your laptop), and try to hook up a floppy drive that way.

or, ditch the idea of XP on that machine and just stick with Linux.

or (cringe) install Vista instead of XP.  Vista presumably does handle SATA on its own, but...  it's VIsta.  *shudder*

---

### Post by rotithor on 2007-11-25
The only reason I want to dual boot with XP is connecting to corporate network via VPN (that is not supported for ubuntu) and be able to use with my Photosmart printer; HP does not support this old printer with Vista and I am not sure how to access it over wireless print server (Linksys) via Ubuntu. If I could do these thing with UBUNTU I could live without dual boot. Downloading driver from HP does not help since it looks for floppy drive. Looks like no good options to fix this. Thanks

Hemant

---

### Post by bluepowder7 on 2007-11-25
have a look through this to see if there's some support for your HP printer:

[http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting)

you might find a driver that works in Ubuntu.  as for VPN, i never used it so i have no ideas on that.  maybe do a search on here for VPN and see if there's workarounds that someone figured out.  or maybe try a different distribution of Linux and see if that gets you VPN support.

---

