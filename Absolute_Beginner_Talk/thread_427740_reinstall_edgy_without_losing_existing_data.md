---
title: "reinstall edgy without losing existing data"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-04-29
Ok, I tried the Feisty upgrade, but it has 2 major flaws. It will not boot up, unless you select generic, in which case it does but it just gives me a white screen. So much for it being the new user freindly version, it was about as big a disiater as it could have been.
I keep a tar backup of my edgy setup, but when I restored this it gets errors, presumably cus there are feisty files lying around. Now, can I reinstall edgy without it deleting the existing data? I have 3 partitions


/dev/sda1 ext3  (the main one with lots of space)
/dev/sda2 extended
/dev/sda5 linux-swap

If I reinstall from live cd, setting the partitons not to reformat, wil it keep the original data e.g. documents, music files that are in the home folder? Thanks.

---

### Post by Pobega on 2007-04-29
If you reinstall and then tell the installer to not format the drives that would be pointless, as the installer (As far as I know) really wouldn't do anything.

I suggest you backup the data you need onto a USB flash drive using the LiveCD, and do a fresh reinstall.

---

### Post by luvinit on 2007-04-29
The livecd doesn't recogise any of the drives i.e. they are not mounted. How do you mount a drive in live cd?

---

### Post by LaurelLynn on 2007-04-29
Dear luvinit,

Yes...and No.

The installer can install without reformatting, gparted with try to, but you can untoggle the button.

Several things can go wrong it you reinstall over the existing os (as you have found).  The user files should not be overwritten, but configuration files (such as those for your Desktop) will be overwritten. Also there is an off chance that the new install my give your user a different id number (ownership is by number not name). Then everything may be in your home directory, but  you may not own them anymore (can be fixed with chmod and chgrp).

Last time I upgraded a system it was Breezy->Daper. I had home as a separate partition, and made a new partition for the new os. Installed to that with a new username using the same home partition. Then I moved the files to the new account and changed the ownership.

That is the paranoid way to do it. The advantage is your current install is uneffected by the new install, but both versions share the /home folder. You can boot either, and still read all the file. So then I can make sure everything is working and to my liking, before making the final move over. At which point I use the old partition as a backup for the new os (in case I screw something up) and it is still there for the next upgrade.

---

### Post by luvinit on 2007-04-29
Thanks Laurel,
I almost understand that. :lolflag:  I will have to do a bit of reading of exactly how the partition system works before I do it. I am assuming that /home is on sda 1 , as it is the biggest, and I assume sd5 is the OS partion, but I will have to do some research.  I thought the tar backup protrcted me, but not really. If I could mount it in live cd I could try extracting it after deleting lots of the feisty system files which are probably casing the trouble, but I don't know how to do that either!

---

### Post by LaurelLynn on 2007-04-29
The file: /etc/fstab

Holds the mapping of disk partitions, each line has the device name and the mount point listed.  So that should help to figure out the correct names. If you post it's contents I can tell you what is what and how to use dd to backup all the partitions to an external drive if you have one large enough.

---

### Post by luvinit on 2007-04-29
I mounted the sda1 drive in livecd, tried to restore my backup but it says there is no space, even though there is a spare 12gb. I suspect this is to do with the partitioning thing?

here is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4c7f7754-f693-43ec-8c08-6c8d0757c68d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=76e2351b-f246-4d3c-890a-f4d4fb38b980 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1       /home/mark/windows ntfs nls=utf8,umask=0222 0 0

only sda1 and sda5 seem to be mentioned, not sda2, as gparted says.

 Thanks a lot, laurel. Backing up to another drive isn't going to be feasible cus I just don't have it available. I am going to go to bed now, it is late here. :)

---

### Post by LaurelLynn on 2007-04-29
From the Live CD you can reinstall to the 12GB  of free space in the extended partition using the manual partitioning option.

The extended partition is a holder for other partitions so if it is sda2, that partition won't be mountable, only the partitions you make inside of it.  For those you have to make yet another partition using the free space in the extended partition.

Select the new partition for /  reformatting only it.

By installing a fresh copy there you will not destory any data on the original partition. In fact, you can select a mount point for the old system at the same time. Placing it somewhere like /oldroot. Then when you boot the new os, all your old files will be avaliable. For example, if your old home folder was  /home/luvinit, all its old files would be at  /oldroot/home/luvinit.

At that point you can move/copy files to more convinent locations (you may need to change their ownership with chmod too), delete the old os directories completely to make space....  You could even move /home to the old partion, but that is a little more difficult.

---

### Post by luvinit on 2007-04-30
Hi laurel,
Well, I followed your instructions, and it seems to have worked perfectly. That partition manager is a very useful tool for saving your data. It's amazing what you can learn by completely messing up your computer. I will stick with edgy, the oldies are the best!

Thanks a lot. :) 

Mark

---

### Post by LaurelLynn on 2007-04-30
Glad to hear it!  :)

Now I do feel ancient, I'm still using Dapper :(

Take care, and have fun.):P

---

