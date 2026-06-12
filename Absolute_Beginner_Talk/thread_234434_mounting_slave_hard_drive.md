---
title: "mounting slave hard drive"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by firebird45331 on 2006-08-11
I created a mounting point and successfully mounted my 300 GB slave drive, but then when I shut down my computer and restart it I have to remount it manually.  How do I make it permanent?

---

### Post by xpod on 2006-08-11
you neec to create a mount point then make an entry for it in your fstab.
Theres plenty threads on it.

New myself so wont go giving any commands but its easy stuff

---

### Post by firebird45331 on 2006-08-11
first what's a fstab and then how do I change it?

---

### Post by xpod on 2006-08-11
Oh GOD....i was scared you`d ask...lol

Your fstab is your "filesystem table"and it lists all the filesystems you`ve previously mounted.

Creating the mount point as you have only makes it show up until you reboot cause it`s NOT yet listed...

Hope ive got that right....I`ll have a quick look for the right commands but somebody will have no doubt gave you them before i get back..

Slower than a week in the jail me

---

### Post by firebird45331 on 2006-08-11
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

That's what my fstab looks like, what do I put in to get my slave mounted?

---

### Post by xpod on 2006-08-11
first you need to
```
sudo fdisk -l
```

that will tell you what that hd(partition)is called.../dev/hdb???

then you have to mount it
```
sudo mkdir /media/fat32
```

replacing fat32 with whatever yours is

```
sudo mount /dev/hda2 -t vfat /media/fat32
```

Thats what i did to get my slave mounted and my XP is fat32 fs so you might be different if your nfts

---

### Post by xpod on 2006-08-11
theres what my fstab looks like WITH my slave hdb and my fat32(xp) mounted too

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1   /media/windows   vfat     iocharset=utf8,umask=0000   0 0


PS save your old fstab before altering it ..as with anything

PPS i cant see your slave there?

---

### Post by xpod on 2006-08-11
Somebody who knows what their doing really needs to be helping you here.

Im already getting confused with things...

i know it would`nt have been a ntfs if it was just a new hd(windows on the brain)...

it`s a pretty straight forward task WHEN you have done it a dozen times and i have only had to mount hd`s a couple of times so dont have the confidendence to do it myself let alone tell others how to go about it.

I just know what it`s like when your waiting for an answer and are  so close to getting everything up and running.....Ready to pounce on the thing

Type mount slave hd in the search....theres dozens of walk throughs

---

### Post by firebird45331 on 2006-08-11
i appreciate your help.  I can manually mount it by typing

sudo mount -t ntfs -o umask=0222 /dev/hdb1 /mnt/windows

so I try putting that into my fstab and it still doesn't work.  I don't know I'm sure I'm doing something wrong

---

### Post by xpod on 2006-08-11
What did you put in your fstab....THAT whole line???

Dont go getting grateful on me cause you`ll probably need MORE help by time yoou get done...](*,) :grin: 

My ubunto was installed automatically on the slave from the live cd.

The only actual mounting ive done on this pc is getting the main hd with xp mounted..i initially had it coming on till reboot too till i got help

This was it`s line
/dev/hda1   /media/windows   vfat     iocharset=utf8,umask=0000   0 0

Have you created the mount point to keep it in with the mkdr command??

---

### Post by firebird45331 on 2006-08-11
yeah I made my mount point /mnt/windows

---

### Post by xpod on 2006-08-11
I dont know who should celebrate more...YOU for getting it done OR me for helping you WITHOUT making matters worse...lol

You would`nt believe some of the simple issues i have trouble getting my head round..........It took me all my time to remember the differences between my DLL`s and my LOL`s in the few months i was with xp.

Have fun my friend....

---

### Post by firebird45331 on 2006-08-11
that's what I type to get it to mount, but on rebooting it's not permanent.  I still need to get it to mount automatically

---

### Post by xpod on 2006-08-11
Sorry i thought you wre "YYYYEEEAAHHHing"   haha

Have you looked back in the fstab and its definetly there?

If you created the mount point ok and saved the right info in the fstab it should show up.

Sorry im not an expert but i cant see what would be wrong as thats all step for step what i did .

It`ll be something silly as it always is eh

---

