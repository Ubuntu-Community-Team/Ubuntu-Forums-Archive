---
title: "i mounted a file system not a disk"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-12-05
i've bee trying really hard to mount a stupid HDD (/dev/hdb1) and i tried reading something someone gave a link to me.  So dont tell me to go another website and read something because chances are i wont understand it.  I want this second HDD to show up like my usbstick in thunar(btw im running Xubuntu)
im going insane trying to modify the fstab in /etc/fstab and it wont work.  i dont undersatnd mounting points.  and i wanted to mount a HDD not a file system.

---

### Post by bodhi.zazen on 2006-12-05
> **lordvolo said:**
> i've bee trying really hard to mount a stupid HDD (/dev/hdb1) and i tried reading something someone gave a link to me.  So dont tell me to go another website and read something because chances are i wont understand it.  I want this second HDD to show up like my usbstick in thunar(btw im running Xubuntu)
im going insane trying to modify the fstab in /etc/fstab and it wont work.  i dont undersatnd mounting points.  and i wanted to mount a HDD not a file system.

LOL lordvolo !

```
sudo mkdir /media/hdb1
sudo mount /dev/hdb1 /media/hdb1
```

FYI: You mount a device by mounting a file system on the device.

---

### Post by lordvolo on 2006-12-05
it worked sort of.  i want to have like a little icon off to the side like my file system (/)

---

### Post by mahy on 2006-12-05
> **lordvolo said:**
> i've bee trying really hard to mount a stupid HDD (/dev/hdb1) and i tried reading something someone gave a link to me.  So dont tell me to go another website and read something because chances are i wont understand it.  I want this second HDD to show up like my usbstick in thunar(btw im running Xubuntu)
im going insane trying to modify the fstab in /etc/fstab and it wont work.  i dont undersatnd mounting points.  and i wanted to mount a HDD not a file system.

You never really mount a disk, always a file system, even if it's USB stick or a CD. Those removable drives show up in Thunar, hard drives do not. Period. You have to mount a file system. 

mount -t <filesystem_type> /dev/hdb1 /mnt/something

or put it into /etc/fstab. There's no other (easy) way to do it. That's the way things work in Unix-like systems.

---

### Post by steve.horsley on 2006-12-05
That's not fair - 3 other answers while I'm typing mine! Especially when the others are better than mine. Boo Hoo.

---

### Post by bodhi.zazen on 2006-12-05
> **lordvolo said:**
> it worked sort of.  i want to have like a little icon off to the side like my file system (/)

Details, details.

I am not familiar with icons in xfce, can you not just change them ?

Follow up: do you also need help with an entry in fstab or permissions? If so, what file system are we talk'n ? FAT, ext3, ???

---

### Post by lordvolo on 2006-12-05
Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4110    33013543+   c  W95 FAT32 (LBA)

---

### Post by bodhi.zazen on 2006-12-05
> **steve.horsley said:**
> That's not fair - 3 other answers while I'm typing mine! Especially when the others are better than mine. Boo Hoo.

Hi steve, nice to see you. Thanks a lot by the way, now I have to clean the coffee off my monitor :p :lol:

---

### Post by bodhi.zazen on 2006-12-05
> **lordvolo said:**
> Disk /dev/hdb: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4110    33013543+   c  W95 FAT32 (LBA)

Add this in /etc/fstab:> /dev/hdb1 /media/hdb1 auto auto,users,umask=000 0 0

Oh and you can re-name the mount point if you like.

Also see this: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by lordvolo on 2006-12-05
i cant modify the fstab i try and then it says:

can't open file to write

---

### Post by bodhi.zazen on 2006-12-05
> **lordvolo said:**
> i cant modify the fstab i try and then it says:

can't open file to write

Open a terminal.

```
sudo nano /etc/fstab
```

Ctrl-X to exit

type "Y" to save....

---

### Post by lordvolo on 2006-12-05
the out come i put my hdb1 on the bottom how do i save and did i do it right?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/hdb1     auto auto,users,umask=000 0       0












^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

---

### Post by bodhi.zazen on 2006-12-05
> **lordvolo said:**
> the out come i put my hdb1 on the bottom how do i save and did i do it right?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/hdb1     auto auto,users,umask=000 0       0












^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

Hey that looks good !

the ^ = control key.

To exit (and save)

Control X, type y

---

### Post by lordvolo on 2006-12-05
how do i use the " ^ " key i press it and it just types it in

---

### Post by CatKiller on 2006-12-05
That refers to the "Ctrl" key.

---

### Post by bodhi.zazen on 2006-12-05
> **lordvolo said:**
> how do i use the " ^ " key i press it and it just types it in

LOL That is the control key, by your shift key, not the ^ key :p

---

### Post by bodhi.zazen on 2006-12-05
> **CatKiller said:**
> That refers to the "Ctrl" key.

Hey cat, did you ever get that vi thing sorted out ?

---

### Post by lordvolo on 2006-12-05
now just use the mount command to mount the disk?

---

### Post by CatKiller on 2006-12-05
> **bodhi.zazen said:**
> Hey cat, did you ever get that vi thing sorted out ?

I've not learned how to use it since you posted the links, no. :)  And now I'm off to bed. But I will probably achieve some passing familiarity with it soon.

I'm OK with nano in the meantime though.

---

### Post by bodhi.zazen on 2006-12-05
> **lordvolo said:**
> now just use the mount command to mount the disk?

Hey, glad to see you found that control key :p

yep. You should not need sudo.```
mount /media/hdb1
```

Of course it is likely still mounted from before. Unmount and re-mount:```
umount /media/hdb1
mount media/hdb1
```

Now ls -l /media to see your permissions.....

And it should mount automatically at boot as well :p

Enjoy !

---

### Post by CatKiller on 2006-12-05
> **lordvolo said:**
> now just use the mount command to mount the disk?

**sudo mount -a** will mount all of the filesystems listed in /etc/fstab, except for the ones with **noauto** as an option.

---

### Post by lordvolo on 2006-12-05
im still lost ](*,). i want a drive icon to the side of thunar like my / and usbstick.  How do i do this, if i take the file and drag it over theres a line that seperates from the rest.  i tryed to change the icon in the properties but theres no disk icon!

---

### Post by bodhi.zazen on 2006-12-05
I'm not sure. Log out and back in perhaps. Reboot perhaps.

---

### Post by kakalaky on 2006-12-05
I don't use Xubuntu, but you made me curious.  This was immediately followed by an apt-get install xubuntu-desktop, so I guess I'll figure it out shortly.

---

### Post by kakalaky on 2006-12-05
Just go to the mount point you created and drag it to the left.

---

### Post by steve.horsley on 2006-12-06
I haven't tried XFCE (yes, I know I ought to), but I read in another thread recently that thunar simply doesn't create icons for hard disk partitions and there's nothing you can do about it.

---

