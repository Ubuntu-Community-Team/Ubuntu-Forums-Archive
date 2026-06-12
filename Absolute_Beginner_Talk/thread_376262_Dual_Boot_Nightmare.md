---
title: "Dual Boot Nightmare"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by GuyJam on 2007-03-04
Hey chaps,
I had a Ubuntu\XP dual boot nightmare on the weekend. I was trying to install Ubuntu 6.10 from the boot CD.
The installation kept on hanging. I ran the 'check disk' utility and all was apparently fine. I tried again and almost made it all the way through the installation, but it ended up hanging during the set-up of the GRUB, so i lost my XP MBR. I know I could of saved it, but I didn't care too much, as I was due for a XP re-install, and i was a good boy and backed everything important up on another physical drive in my machine.

Now for the clencher...
I installed XP on my first drive, and that drive that I backed everything up on(320gb), now is only 10.1mb with a couple of weird files with no names. Hence, all my backups are gone too. ouch.
I really can't figure out what happened, or how to get my info back.
Anyone got any clues? It would be nice get get my drive back.

Thanks lots

GuY

---

### Post by aysiu on 2007-03-04
You may not be able to get your info back, but if you can... the Ubuntu Desktop CD may help. It is the Desktop CD you have, right? Not the Alternate CD?

If you can successfully boot the Desktop CD, please go to [the terminal](http://www.psychocats.net/ubuntu/terminal) and paste in this command: ```
sudo fdisk -l
``` and then post back the output in this thread.

---

### Post by GuyJam on 2007-03-04
Will do. I'll do it when i get home tonight. Fingers crossed...

Thanks so much for your help (grovel grovel)

Guy

---

### Post by GuyJam on 2007-03-05
got it:

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start      End      Blocks          Id  System
/dev/hdb1   *     1          38913   312568641    7  HPFS/NTFS

cheers

GuY

---

### Post by aysiu on 2007-03-05
Okay.

Try pasting these commands in in this order: ```
sudo mkdir /media/windows
sudo mount /dev/hdb1 /media/windows -t ntfs -o nls=utf8,umask=0222
``` Then, in your file browser, press Control-L and type /media/windows

You should see all your Windows files... whatever's still there.

---

### Post by GuyJam on 2007-03-05
Typed in this:

sudo mount /dev/hdb1 /media/windows -t ntfs -o nls=utf8,umask=0222

Got this:

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So I type in this:

dmesg | tail

Got this:

[17179745.788000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180209.972000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17180209.988000] NTFS-fs warning (device hdb1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17180209.988000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180209.988000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180209.988000] NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.
[17180571.396000] NTFS-fs warning (device hdb1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17180571.396000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17180571.396000] NTFS-fs error (device hdb1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17180571.396000] NTFS-fs error (device hdb1): ntfs_fill_super(): Not an NTFS volume.

Not sure, but looks bad ??

Guy

---

### Post by lamalex on 2007-03-05
download knoppix. will be a bit better than ubuntu for data recovery. i've had VERY good luck with it.

---

### Post by aysiu on 2007-03-05
That looks weird. *sudo fdisk -l* seems to indicate the drive is NTFS, but *dmesg | tail* says it's a FAT filesystem.

Iamalex is right--Knoppix is better for recovery purposes, but Ubuntu can be used, too. Ubuntu just isn't *designed* for recovery.

I'm guessing that your partition table is damaged somehow, and you'll probably have to use [GPart](http://www.stud.uni-hannover.de/user/76201/gpart/) to fix it (GPart is different from GParted, just so you know). Unfortunately, I don't know exactly how to use GPart. This may be a good place to start to find info on GPart:
[http://geekblog.oneandoneis2.org/index.php/2006/02/05/triumph_aamp_tragedy](http://geekblog.oneandoneis2.org/index.php/2006/02/05/triumph_aamp_tragedy)

---

### Post by GuyJam on 2007-03-05
I actually tried to load knoppix, but the cd would hang at the 'detecting system components' part. I think I'll give it another try though.
But, after reading that article on GPart, I think that's my best answer at the moment.

Thanks again, I'll let ya know how i go.

---

### Post by GuyJam on 2007-03-10
Just as a finisher, I didn't have much luck with GPart. It couldn't recognise any partition at all.
So, as a last resort, I've dropped the drive down at a data recovery place. Hopefully they'll have better luck.
Thanks lots for your time guys

GuY

---

### Post by wj32 on 2007-03-10
Use testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

