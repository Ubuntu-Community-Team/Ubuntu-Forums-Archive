---
title: "ok! one last thing (hard drives)"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by johnlee on 2006-12-24
ok, thank you for the little bit of info for playing mp3s it seems i have one more thing to go through
when i installed xubuntu, i had a cdrom on one ide and a hard drive on the other,
i switched the cd rom to another hd and now need to install it
i downloaded qtparted to partition it,(i cant see it in any of my file folders currently)
but its talking about root
how do i see and partition it?
thank you
john
(ps im so in love with the general ease of use of ubuntu, its like windows simplified
i love the panes synaptic and all this, i think it will return me to a land where computers are tools, not hobbies)

---

### Post by MkfIbK7a on 2006-12-24
**QUOTE:**but its talking about root

what do you mean by this?

---

### Post by johnlee on 2006-12-24
:no device found. maybe you are not using root user?

sorry for not being clear.
thanks

---

### Post by MkfIbK7a on 2006-12-24
did you do sudo qparted

---

### Post by johnlee on 2006-12-24
i do not know how to do this sudo qtparted

---

### Post by johnlee on 2006-12-24
ok, i loaded up terminal, pasted what you told me to and now i think qtparted sees the second hard drive

thank you.
is there anywhere i can read aabout terminal and basic command prompts in ubuntu?

---

### Post by MkfIbK7a on 2006-12-24
type it into the console

---

### Post by pseudonym on 2006-12-24
It's not quite clear exactly how you've got your drives connected. Can you respond with which drive is connected where?....

Better yet, open a terminal and type 'sudo fdisk -l' and reply with the output...

Edit - don't bother. looks like you got it going

---

### Post by MkfIbK7a on 2006-12-24
yes look in the help browser

---

### Post by johnlee on 2006-12-24
i just formatted the second hard drive
here is my fdisk paste


Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24701   198410751   83  Linux
/dev/hda2           24702       24792      730957+   5  Extended
/dev/hda5           24702       24792      730926   82  Linux swap / Solaris

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
15 heads, 63 sectors/track, 413462 cylinders
Units = cylinders of 945 * 512 = 483840 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1      413457   195358401    7  HPFS/NTFS
johnlee@johnlee-desktop:~$ 

now my file system shows 174.6 gb, same as before i formatted,
how do i get to see or use the other drive?
thanks

---

### Post by pseudonym on 2006-12-24
You need to add it to your /etc/fstab file.

First, make a mount point for it eg. /media/windows

In a terminal, sudo mkdir /media/windows

Now type sudo mousepad /etc/fstab (mousepad is the xubuntu text editor)

and add this line -

/dev/hdc1      /media/windows    ntfs    umask=022       0       0

make it so each column matches up with the other. save and exit.

now type sudo mount /dev/hdc1

you should now have access to the hard drive.

next reboot it will be automatically mounted.

---

### Post by johnlee on 2006-12-24
i recieved this after trying saving fstab and moving to the next step,

johnlee@johnlee-desktop:~$ sudo mount /dev/hdc1
[mntent]: warning: no final newline at the end of /etc/fstab
mount: wrong fs type, bad option, bad superblock on /dev/hdc1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

johnlee@johnlee-desktop:~$ 

heres is my fstab, whatd i do wrong?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=be6ca276-bfec-4d09-8df8-bc4e31826338 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=04026317-a608-4c55-b7c2-783c8c668b11 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1	/media/windows 	ntfs 	umask=022 	0 	0

---

### Post by pseudonym on 2006-12-24
It is still formatted as ntfs, right? Try a reboot to get the drive to mount automatically...

One more thing - instead of just 'ntfs' in /etc/fstab, make it 'nls=utf8,umask=022'

---

### Post by MkfIbK7a on 2006-12-24
one question did my advice help you any?

---

### Post by johnlee on 2006-12-24
yea wert, thanks for alerting me on how to get into qtparted with root

im still stuck however rebooted, added the extra code still nothing
funny thing though
qtparted regards the drive as ext3, fdisk as ntfs

---

### Post by pseudonym on 2006-12-24
are you sure the drive is jumpered correctly? if it's on hdc it should be set to master...

---

### Post by johnlee on 2006-12-24
eek! i remember that i was trying to get them on the same ide cable!
probably still on slave ill be back!
thanks

---

### Post by johnlee on 2006-12-24
nope, it is a master,

:|
 ive been playing around with fstab
what does this mean?
[mntent]: warning: no final newline at the end of /etc/fstab

---

### Post by johnlee on 2006-12-24
johnlee@johnlee-desktop:~$ sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       24701   198410751   83  Linux
/dev/hda2           24702       24792      730957+   5  Extended
/dev/hda5           24702       24792      730926   82  Linux swap / Solaris

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
15 heads, 63 sectors/track, 413462 cylinders
Units = cylinders of 945 * 512 = 483840 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1      413457   195358401    7  HPFS/NTFS

FDISK,

then... my fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=be6ca276-bfec-4d09-8df8-bc4e31826338 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=04026317-a608-4c55-b7c2-783c8c668b11 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc1 	/media/windows 	ntfs 	umask=022 	0 	0

i dont know whats going on. :|

---

### Post by pseudonym on 2006-12-24
Try hitting enter a couple of times at the end of your last fstab line, then saving the file. The error you're getting (or at least part of it) usually means bad syntax. Then type 'sudo mount -a'

If it still doesn't work try mounting it manually with - ```
sudo mount /dev/hdc1 /media/windows/ -t ntfs -o nls=utf8,umask=022
```
That's not a permanent solution but if it works you're at least making progress...

---

### Post by johnlee on 2006-12-24
it looks like i got it to mount, i just copied what hda said for file formal and the rest and it seems to have put it up
thanks psuedo!
i just got this box, im so happy, its now 400 gb large in a small form factor case, and seems to run oh so well.
again, thanks so much for being patient with me

---

### Post by pseudonym on 2006-12-24
You're welcome.

I learnt something myself, too. In the current Ubuntu release the drive naming scheme in /etc/fstab has changed (I'm only running Debian at the moment). You may find [this thread]("http://www.ubuntuforums.org/showthread.php?t=286758") instructive.

all the best.

---

### Post by MkfIbK7a on 2006-12-24
glad you got your hardrive to mount:D 

this is the benifit of the ubuntu forums!

---

