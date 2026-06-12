---
title: "installing new 2nd hard drive"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by evilc on 2006-10-24
I have totally mucked up... I have installed a 2nd hd and tried to get Ubuntu to see it (followed wiki but can't find the page again). When I put it in fstab I named it drive2 but was unable to see it in Nautilus except under /media/drive2, I wanted it under places in Nautilus.

Can't remember what I did altogether but now I have a folder called backup on desktop and under places (Nautilus) and now can't get into drive2?

How can I remove everything associated with this drive and restart again?, help on installing wuold be appreciated as well.

TIA

---

### Post by Episteme on 2006-10-24
Hi Evilc,

I believe I can help. Can you post your fstab so that I can take a look at how you're mounting the drive? Also, what version of Ubuntu are you using?

Epi.

---

### Post by evilc on 2006-10-24
> **Episteme said:**
> Hi Evilc,

I believe I can help. Can you post your fstab so that I can take a look at how you're mounting the drive? Also, what version of Ubuntu are you using?

Epi.

Thanks I'm using version 6.06 my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sdb1       /media/drive2  vfat    iocharset=utf8,umask=000   0       0

---

### Post by Episteme on 2006-10-24
Yeah, I had a similar problem.

In the end, I opted to mount my secondary drives under the /mnt folder rather than /mount

So, that would make the fstab line

/dev/sdb1 [COLOR="Red"]/mnt/[/COLOR]drive2 vfat iocharset=utf8,umask=000 0 0

sudo gedit /etc/fstab and change the mount point.

to make the mount point you just referenced in fstab: sudo mkdir /mnt/drive2
then change the properties to: sudo chmod -R 755 /mnt/drive2
and to give yourself ownerships: sudo chown -hR user:user /mnt/drive2
replacing 'user' with your user name.

Once that is done, reboot and open nautilus to /mnt and drag the drive2 folder to the left and drop it under [places] to make a link under your [places] shortcuts (open nautilus and you'll see what I mean).  You can do that with any folder.

Let me know how that works for you.

Good luck!

Epi

---

### Post by evilc on 2006-10-25
> **Episteme said:**
> Yeah, I had a similar problem.

In the end, I opted to mount my secondary drives under the /mnt folder rather than /mount

So, that would make the fstab line

/dev/sdb1 [COLOR="Red"]/mnt/[/COLOR]drive2 vfat iocharset=utf8,umask=000 0 0

sudo gedit /etc/fstab and change the mount point.

to make the mount point you just referenced in fstab: sudo mkdir /mnt/drive2
then change the properties to: sudo chmod -R 755 /mnt/drive2
and to give yourself ownerships: sudo chown -hR user:user /mnt/drive2
replacing 'user' with your user name.

Once that is done, reboot and open nautilus to /mnt and drag the drive2 folder to the left and drop it under [places] to make a link under your [places] shortcuts (open nautilus and you'll see what I mean).  You can do that with any folder.

Let me know how that works for you.

Good luck!

Epi

Thanks Episteme that worked, by the way I noticed I have drive2 showing in both /media and /mnt the one in /media shows the files I put in but not in /mnt I will tranfer them and delete the /media one.

---

### Post by CatKiller on 2006-10-25
(In Nautilus) Bookmarks -> Add Bookmark to add a folder to the Places menu.

---

