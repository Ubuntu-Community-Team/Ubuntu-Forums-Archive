---
title: "Ipod Mounted as Read-Only Disc"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by Iandefor on 2006-01-08
I figured this would be an appropriate place to post this since, when it comes to permissions and disc-mounting, I have little to no experience.

So, if I plug in my Ipod, it mounts without issue. I can open it up and browse the filesystem, no problem. However, at any point when I attempt to make changes to the filesystem (IE, add, move, delete a file) a message pops up claiming that I don't have permissions to change the filesystem.
The funny thing is, it claims that my username is the owner. I opened up /etc/fstab and /etc/mtab and examined them. My Ipod isn't listed in /etc/fstab, but /etc/mtab corroborates that I am the owner. I'll list the contents of both files here.
[B]
fstab:[/B]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
[B]
mtab:[/B]
/dev/hdc1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
/dev/sda3 /media/ipod hfsplus rw,noexec,nosuid,nodev,uid=1000,gid=1000 0 0

Running Nautilus using sudo and attempting to make a change to the filesystem simply results in an error message claiming that the filesystem is mounted as read-only.

Any help would be appreciated. Thank you!

---

### Post by Iandefor on 2006-01-08
this is getting worrisomely low on the forums... *bump*!

---

### Post by Iandefor on 2006-01-08
Gaaah! This is the last time I'm bumping this. Answer, someone!

---

### Post by mcmillan on 2006-01-08
That you're saying it's showing you as the owner but not letting you write I think is a bit odd. I thought mounting something not in fstab has to be with sudo which I think would be making it the root owner, but I'm not sure. I don't know if it helps at all, but below is my fstab line that I use to mount my mp3 player (not an ipod but I think it should work more or less the same)

/dev/sda1       /media/usbdrive vfat    rw,user,noauto  0       0

---

### Post by dcast on 2006-01-08
try chown or chmod?

---

### Post by Iandefor on 2006-01-08
Ah, responses. Thanks!

@mcmillan: I wasn't aware you could use fstab for removable filesystems?

EDIT: Adding my ipod to fstab didn't do anything. Here's the line I used (it's formatted as an HFS volume)

/dev/sda3       /media/ipod     hfsplus rw,user,noauto  0        0

---

### Post by shadesfox on 2006-01-08
Well, if you want to put songs on the iPod you will need to use gtkpod rather then go through the iPod when mounted.  It is in the universe repository.  If you just put a song on the iPod hard disk then it won't show up on the iPod's database and you won't be able to play it.  Hope that helps.

---

### Post by jleigh on 2006-06-23
There seems to be some issue with journal hfs+ and 2.6.15 kernels (shipped in Dapper).
[http://www.ussg.iu.edu/hypermail/linux/kernel/0511.0/0941.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0511.0/0941.html)

You have to disable the journal on your ipod for the kernel to mount it read/write.  To do this I plugged my ipod into a mac and ran 
      diskutil disableJournal /Volumes/iPod

The instructions I followed are here:
[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

### Post by LinLenLap on 2006-08-27
I just wanted to say that I've got the same problem. I've gone through the forums here and elsewhere with a fine tooth comb and can't find anyway to make it work. My best guess is that it's a bug.

I opened /mnt as root, throught nautilus and elsewhere, and tried to change the ownerships. Gnome politely told me to shove it, since I didn't have enough privelages. What? Is there anyone more privelaged than me, the root?

I think this is the "patch" to fix it, but I'm not sure, since it's way beyond me and my "one sip of ubuntu" status.

[http://www.kernel.org/git/?p=linux/kernel/git/gregkh/linux-2.6.15.y.git;a=commit;h=b0b623c3b22d57d6941b200321779d56c4e79e6b]("http://www.kernel.org/git/?p=linux/kernel/git/gregkh/linux-2.6.15.y.git;a=commit;h=b0b623c3b22d57d6941b200321779d56c4e79e6b")


Here's to an understandable solution soon.

Best,
LLL

---

### Post by jonger on 2006-08-28
thanks a bunch,
this helped me
this being the nfs+ and gtkpod problem. i took ipod to the mac and diable the journaling and it works now. thank you

---

### Post by paul20111 on 2006-08-28
Hi everyone,

I had a similar problem with my FAT-formatted iPod Nano so I thought I'd post my solution in here in the hope it might help people.  I too was getting read-only problems when attempting to use my iPod with Ubuntu.  A quick inspection using 'dmesg' showed that there were errors in the FAT filesystem.  I fixed these using:

$ sudo dosfsck -a /dev/sda2

(change /dev/sda2 for the relevant /dev node for your ipod)

This automatically corrects errors in the filesytem and is non-destructive - all my data remained intact.  It took a while (half an hour or so) to fix my 4GB Nano but once it finished, I could mount my iPod and write to it, as well as sync it with Gtkpod.

Hope this helps!

---

### Post by LinLenLap on 2006-11-30
I just want to add, or update rather, that upgrading to Edgy Eft completely removed the problem. Ipod shuffle automounts and opens within Amarok without issue.

Interestingly, if I removed mounted volumes from desktop through gnome-config, Amarok will no longer connect to it properly, even when manually mounted.

Just FYI if anyone is still interested in this thread.

L.

---

### Post by PrairieShaman on 2007-02-21
Im having this problem and no solutions that work for anyone else work for me. :mad:

---

### Post by igknighted on 2007-02-21
> **PrairieShaman said:**
> Im having this problem and no solutions that work for anyone else work for me. :mad:

Try formatting your iPod with a windows format and not the mac format.  The windows format plays much nicer, as HFS+ is a huge pain in the arse.

---

### Post by PrairieShaman on 2007-02-22
how do I know if its the mac or windows formatting on my ipod?

---

