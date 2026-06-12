---
title: "Nautilus places problem Edgy..."
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by eiraku on 2006-11-03
Hey there guys, I dunno if this problem has ever cropped up before (a painfully long google search suggests otherwise, but I might have overlooked something), but I'm having a little problem with my nautilus places sidebar...

They say a picture's worth a thousand words, so here we go:

[IMG]http://img243.imageshack.us/img243/1565/mountprobcm6.png[/IMG]

Every time i click on it, i get a "Unable to mount the selected floppy drive - mount: mount point /media/floppy0 does not exist" error

I tried deleting its entry in the media folder, but its still there in Places... ](*,) 

Anybody with any idea on how I can get rid of that useless floppy mount point? The one below it is working fine, though... :-#

My specs:

Fujitsu C2220 Laptop running Ubuntu 6.10 (686 kernel - supposedly)
Pentium 4M 2.40GHz (due to a problem with speedstep, its running at 1.8 now)
768MB RAM, ATI RADEON IGP R200 (with 128MB from RAM)

---

### Post by po0f on 2006-11-03
eiraku,

Edit /etc/fstab as root and delete the redundant floppy entry there.
```
$ gksu gedit /etc/fstab
```

---

### Post by eiraku on 2006-11-03
That did it, thanks!

---

### Post by Cariboo1938 on 2006-11-04
> **po0f said:**
> eiraku,
Edit /etc/fstab as root and delete the redundant floppy entry there.
```
$ gksu gedit /etc/fstab
```
I have the same "Floppy 1 non working mount point" thing (See Attachment).
 And this is my /etc/fstab:> # /etc/fstab: static file system information.
# <file system> <mount point>   <type>  	<options>       	     <dump> <pass>
proc            /proc           proc    	defaults        		0      0
 
/dev/sda1	/boot           ext3    	defaults        		0      2
/dev/sda2  	/               ext3    	defaults,errors=remount-ro 	0      1
/dev/sda8	none            swap    	sw              		0      0

/dev/hda        /media/cdrom0   udf,iso9660 	rw,user,noauto     		0      0
/dev/hdb        /media/cdrom1   udf,iso9660 	rw,user,noauto     		0      0
/dev/           /media/floppy0  auto        	rw,user,noauto  		0      0
There is only one entry for Floppy. Can I delete this?

---

### Post by towsonu2003 on 2006-11-04
> **Cariboo1938 said:**
> I have the same "Floppy 1 non working mount point" thing (See Attachment).
 And this is my /etc/fstab:
There is only one entry for Floppy. Can I delete this?

Do you have a floppy? You could try deleting it anyway... the way to go would be:
```

sudo cp /etc/fstab /etc/fstab.bckp123
gksu gedit /etc/fstab

``` and edit the file. I would try to change that entry so it looks like: 
```

# /etc/fstab: static file system information.
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0

/dev/sda1 /boot ext3 defaults 0 2
/dev/sda2 / ext3 defaults,errors=remount-ro 0 1
/dev/sda8 none swap sw 0 0

/dev/hda /media/cdrom0 udf,iso9660 rw,user,noauto 0 0
/dev/hdb /media/cdrom1 udf,iso9660 rw,user,noauto 0 0
/dev/**fd0** /media/floppy0 auto rw,user,noauto 0 0 
``` and restart X (I guess... maybe it's redundant to restart X?)
if that doesn't work, delete the entry. If that doesn't work either for you, you can always recover your backup fstab with
```

sudo cp /etc/fstab.bckp123 /etc/fstab
```
**[COLOR="Red"]pls oh pls don't make a typo[/COLOR]**

---

### Post by Cariboo1938 on 2006-11-04
> **towsonu2003 said:**
> Do you have a floppy?  Hello and Yes I do have a floppy! 
I changed fstab as you said ...and "Floppy 1" disappeared from 
Computer Place!> ...and restart X (I guess... maybe it's redundant to restart X?) ..yes it is irrelevant to restart! Thank you so much for your time and help!
Juergen:)

---

### Post by po0f on 2006-11-04
Another option to deleting the line (and a little bit more recoverable in case of mistake) would be to simply comment the line out.  Just for future reference.  :)

---

### Post by Cariboo1938 on 2006-11-04
> **po0f said:**
> Another option to deleting the line (and a little bit more recoverable in case of mistake) would be to simply comment the line out.  Just for future reference.  :)But doesn't one need the line if he has a flppy drive???

---

### Post by po0f on 2006-11-04
Cariboo1938,

You can still manually mount the floppy through the terminal:
```
$ sudo mount -t blar /dev/fd0 /mnt/floppy
```

---

### Post by towsonu2003 on 2006-11-05
> **po0f said:**
> Another option to deleting the line (and a little bit more recoverable in case of mistake) would be to simply comment the line out.  Just for future reference.  :)

we didn't delete the line :) we changed it from /dev to /dev/fd0 ;)

---

### Post by po0f on 2006-11-05
towsonu2003,

I didn't even notice the second person's fstab, sorry.  It was a case of "post before you look".  ;)

I still stand by my tip.  :)

---

### Post by DeathOnJuice on 2006-11-06
Hmm, this is interesting. I has this problem, and I was also getting an error with the Totem Firefox plugin (when I tried to play some sound a video files, I got an error something like fd0 not a valid device, which really makes no sense; I can't remember the exact error, but it involved fd0), and occasionally Firefox would crash. The file would never play.

Anyway, I applied this fix after a little Googling and both very bizarre problems are gone now.

---

