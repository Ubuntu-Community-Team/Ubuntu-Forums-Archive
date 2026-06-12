---
title: "[SOLVED] Some steup / post install / partition confusion."
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by icceric on 2008-01-23
An official 'Hello' as this is my first post.

First the system (also in my sig)
Pentium 4 2.4GHz
Abit BE7-RAID (with Highpoint 372 IDE raid)
1 GB Samsung DDR 333
Nvidia GeForce FX 5200 128MB video
IBM Deskstar 41GB (IDE #1)
DVD RW (IDE #2)
Maxtor 40GB (IDE #3)
Ubuntu 7.10

Problems...
I will start by saying that I have very little (but some) CLI experience as a Mac OS X occasional Terminal.app user.  But I am learning a bit here and there.  So far, it's been fun.  Anyway, I blew the dust off of my 6 year old PC a few days ago and went straight to Fedora and installed.  Ran fine, a few things held me up like wireless networking driver etc.  Ran accross a bit of info on Ubuntu.  Decided it was interesting enough to check out.  Downloaded the live cd / installer.  Was amazed that all of my hardware was auto detected correctly (for the most part, had some minor graphics / resolution issues that I fixed)... figured I had to have it!  Installed it.  When it came to the partitioning section, I choose "manual".  At this time, I had two physical drives in the computer (as listed above) and I chose the IBM drive to partition.  I created /, /home and swap partitions and continued the installer.  After it was finished, I pulled the cd and rebooted.  Only it didn't boot into Ubuntu, it booted into GRUB and I got this....

grub>

Sure, I am new to Linux, but I know that grub is a boot loader, made to choose what to boot, but I only got that command above and no options.  I checked out what commands were available, but I didn't really recognize any that would get me into Ubuntu.  So I thought maybe I messed up in the partitioning and created the wrong ones, or something to that effect.

Went for round two...
This time I choose a "guided" partitioning using the entire disk.  Ran through the rest of the setup with the exact same result...  booting to "grub>".

Third time is the charm...
Went for round three... this time, for whatever reason (I guess to try to simplify) I pulled the second drive (the Maxtor that is on the Highpoint raid IDE)... ran the installer, this time choosing a guided partition where it would only use half the drive (maybe it was set as default?  Can't remember if I used the slider or not).  Went through the rest of the installer... voila, it worked!

Anyway, I noticed that I have several partitions on this IBM drive now.  Or at least had... (but more on that in a minute).  Checking out gparted, the install resulted in five partitions...

/dev/sda1 ext3 (no mount point) 20.03 GB
/dev/sda3 ext 3 (mounted at "/" ) 15.96 GB
/dev/sda2 extended with two sub partitions...
     /dev/sda6 linux-swap 760.83 MB
     /dev/sda5 linux-swap 1.61 GB

The only two mounted partitions are /dev/sda3 ( / )  and /dev/sda6 (swap).  Here's the /etc/fstab...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1e91ffc7-e072-4c16-a08a-d62a25bb3f69 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=07459a42-4b56-4205-bbae-0c846e302357 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


And now here's what I did...
First I put the Maxtor drive back in... it is now /dev/hde1.  formatted it to ext3 edited my fstab to mount it at /media/Files, chowned it etc.  Rebooted, mounts fine to the desktop, files are readable / writable... excellent.

Next I explored this other 20GB partition that was unmounted.. /dev/sda1.  Opened the file manager, dbl clicked it, it asked for a password and mounted.  The contents however, on first glance were a mirror of /dev/sda3 with some exceptions (the "eric" home folder only had the folder "Examples" that was a shortcut) and a few other folders either had no files in it or a few less than the same folder on sda3.  So, in true form, I let it set in my brain for a night, the more it sits, the more I am willing to screw it up by playing around with it.  Today, I woke up and decided to format it and mount it thinking that it was some kind of temp files left over from installing.  So thats what I did.  Opened gparted and formatted it to ext3 and set it to mount in /media/Storage.

Restarted and it's fine.

Was this right or ok to do?  I am fully prepared to accept the responsibility which is why I went ahead and did it in the first place (I learn by doing).

Anyway, I could be wrong, but the layout of the drive just doesn't seem right and .. two swap partitions??  I can only assume that this is all residue from trying to install three times over a Fedora install.

So, here are the pertitions in order of sda3...
sda1 now mounted at /media/Storage
sda3 mounted at /
sda2 extended, sda6 swap, and sda5 swap

obviously the smaller swap partition is being used.  I assume that sda 2 is 2.35 GB because when I first tried to install Ubuntu using a manual partition scheme, I create a 2GB swap partition... ?

My fstab is now...
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1e91ffc7-e072-4c16-a08a-d62a25bb3f69 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=07459a42-4b56-4205-bbae-0c846e302357 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/hde1
/dev/hde1   /media/Files   ext3   defaults   0   1
# /dev/sda1
/dev/sda1   /media/Storage   ext3   defaults   0   1

So, sorry for the long story, but here it is.. in all it's glory.
1. Why did I first boot into "grub>" on install attempts 1 and 2?
2. Was it ok to partition sda1? (I would say yes since Ubuntu so far has been running great)
3. Why is my partition layout so crazy on my main drive and is it ok?

Thanks for your help in advance... I appreciate it!

Regards,
Eric

---

### Post by Hospadar on 2008-01-23
could you clarify what exactly your hardware hard drive setup is? are the drives sata or IDE, raid or regular, master/slave etc.  Also, where exactly do you want everything to end up? (home partition root partition etc.)

I'd guess at the moment:
1) the boot loader was installed in the wrong place, or perhaps the old boot loader was still booting, and as such of course not finding the ubuntu kernel
2) I think so, although I'm still a little unclear on your exact hard drive partition scheme.  I *think* that was the partition you previously selected as your /home, but for whatever reason it didn't actually end up that way, so as it is, if things work, maybe they arn't set up quite how you want, but they are OK
3) probably you just didn't properly clean out the drive after your previous install.  I would suggest using something like a gparted livecd (or you can use gparted off the ubuntu livecd for that matter) and first clean out all the partitions from your drive, I think you can just plain delete them.  then do your install.  use the manual partitioner also to make sure things are how you want them.

Also, if you have two drives, and you want, let's say, your root partition, swap, and /home on one drive, and you want the other drive to be just data, I'd just remove the other drive during the install, and then when you put it back in, make sure the drive you installed to is in the master channel on your IDE cable and that the jumpers are set correctly on both drives (if they are IDE drives), make sure the boot order is correctly booting of the drive you installed to, and then worry about where you want to mount the data drive and how you format it.

---

### Post by logos34 on 2008-01-23
I think Hospadar is right on 1)...Sounds like the issue here is that grub couldn't find menu.lst.  If the IBM drive is indeed IDE, maybe the raid controller on the other drive confused grub and/or ubiquity at installation time as to what the Bios boot drive was, with the result that it got the 'root' wrong.  If, OTH, the IBM drive is in fact SATA (not always apparent these days since ubuntu switched to the libata scsi storage driver), then it would make perfect since that grub got the boot drive wrong--it almost always assumes that the first IDE disk is the boot drive regardless of the actual order of sata and ide drives.

I agree--reinstall without the maxtor connected to clean things up.

---

### Post by icceric on 2008-01-23
Hi and thanks for your replies!

Yes, all drives are parallel ata.  My initial intentions were to install everything on the IBM drive which is connected to the first PATA port on the motherboard within several partitions, making /home on a separate partition.  So the first partition would be / (wise to create separate boot partition?), then have /home, then swap.  Is this a good scheme... you don't have to answer that, I can research it...  But then the maxtor, which is connected to the HPT ide pata port, for files.  None of the drives are setup as a raid.

But I would say everything you guys said makes perfect sense.  I wasn't aware I could use gparted from the ubuntu live cd, I suppose I need to boot into terminal for that, or run it from the live cd desktop?  Anyway, I will reinstall in order to get everything a bit neater.

I basically just want to use the machine for a file server / Subversion or CVS repository for when I am working on websites via Eclipse on two different Macs in the house.. and to learn some cool stuff in Linux (installing a local server to test php sites etc)

Thank you for the replies.

Regards,
Eric

---

### Post by logos34 on 2008-01-23
You don't need a separate /boot.  But I know that a lot of server setups put /var, /usr, and /tmp (and of course /home) on separate partitions.  So that's something to look into.  A good way to go would be to make / a primary partition, then create an extended out of the remaining disk space and throw the rest inside.

On the ubuntu live cd Gparted is tucked away in System>admin>'Gnome partition editor' (or maybe it's changed to just 'Partitioner;).  Or you can just run **gksudo gparted** in terminal

---

### Post by icceric on 2008-01-23
Thank You, logos34 and Thank You, Hospadar. For one reason or another I used the gparted from the Ubuntu live cd and it crashed... twice.  So I ended up downloading the gparted live cd, booted to it, deleted all partitions and installed Ubuntu, by default it choose "guided, use entire disk" since I had no partitions on there.  Worked like a charm.  Booted to my Ubuntu install, ran updates, ran apt-get to download and install gparted to check out what partitions were made and it created a 37 GB part for / and the rest for swap... very happy now.  Now I'm off to add my second hdd and then to some productivity.

Thank You!!

Eric

---

### Post by logos34 on 2008-01-23
ok, super.

Mark as 'solved' (>thread tools)

enjoy

---

### Post by icceric on 2008-01-24
> **logos34 said:**
> ok, super.

Mark as 'solved' (>thread tools)

enjoy

Thanks, I was wondering how people did that.

---

