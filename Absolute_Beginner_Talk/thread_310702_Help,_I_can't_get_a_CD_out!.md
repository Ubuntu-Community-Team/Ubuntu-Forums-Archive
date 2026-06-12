---
title: "Help, I can't get a CD out!"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by The Iron Curtain on 2006-12-01
God, I must be the newbiest noob evar. 

I put in a CD into my CD drive. And now I can't get it out. I keep pressing the button that's supposed to open it, but nothing happens. I got to /media/cdrom and it reads the cd, but I can't get it out of my drive.](*,) 

I'm running Ubuntu 6.06 on a Compaq Preario 700 Laptop

Help!

---

### Post by hardyn on 2006-12-01
yeah... it does that, right click on the CD icon and "eject".

---

### Post by tbg58 on 2006-12-01
On most CD drives, there is a small (about 1mm in diameter) hole below (for horizontally mounted drives) or beside (for vertically mounted ones) which is for opening the drive even when no power is applied.
Take a large paperclip, straighten the end, insert into this hole, and the CD drawer should open.

I hope your drive has the power out open access hole.

Kindest regards,

Rob

---

### Post by Beernut on 2006-12-01
If you can see the drive mounted on the desktop right click on it and click eject.  If the disc is stuck in the drive like the door didn't shut right or something you can take a paperclip straighten it out and on the CD drive door there is a little hole push the paper clip in and that will release the door.

---

### Post by LLRNR on 2006-12-01
Fast eject mode:```
eject -n
```to see the device set to be ejected (in case you have more than 1 cdrom/cdrw/dvdrom/dvdrw). If that is the one you want to eject, do ```
eject -v
```If it's not the one you want to eject, then use```
eject -v /dev/hd**x**
```where **x** stands for the device you actually want to eject... Cool tip: you can even *close* the tray !! ```
eject -t
```

LLRNR

---

### Post by The Iron Curtain on 2006-12-01
I found the CD Icon on the desktop and I R-Clicked and hit Eject . I got  a message that said it failed. THis is wha tit said:

```

umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
eject: unmount of `/media/cdrom0' failed

```

I'll look for a pin/paperclip

---

### Post by The Iron Curtain on 2006-12-01
okay, found a paperclip and I found the hole. It fit, but it still wouldn't open. i'll try that method from the command line

---

### Post by Tipo on 2006-12-01
I guess there is always 'sudo eject' too...

---

### Post by The Iron Curtain on 2006-12-01
Huzzah! It worked! Thanks LLRNR! :)

---

### Post by ocertain on 2006-12-01
If your computer is a desktop or tower there is a pin-hole on the CD drive. You can unfold a paper clip and insert in in the pinhole to open the drive.

A better way (and if you're using a notebook, the only way I know...) you can unmount the cd drive and remount it. If you don't know how to do that then try restarting Ubuntu.

hth,
Olice

---

### Post by steve.horsley on 2006-12-01
The usual reason you can't eject a CD is that you have a command-prompt open with the CD as its working directory, or a file  browser like nautilus open looking at a directory on the CD. That's what makes it "busy". Close all yor file manager windows and terminal windows. Then both the eject command and the button on the drive should work.

---

### Post by LLRNR on 2006-12-01
> **ocertain said:**
> you can unmount the cd drive and remount it. If you don't know how to do that then try restarting Ubuntu.

How rude !!! :D
To unmount your cdrom:```
sudo umount -v /dev/hd**x**
```(you know what x stands for...)
To remount your cdrom:```
cat /etc/fstab
```and look for the mount point of your cdrom (in my case, it is in */media/cdrom0*) and then```
sudo mount -v /place/to/mount (for example, in my case: /media/cdrom0
```

LLRNR

---

