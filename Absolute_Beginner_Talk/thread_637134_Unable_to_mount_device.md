---
title: "Unable to mount device"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-12-10
I am running IceWM with PcManFM, and I plug in my USB flash drive, launch PcManFM, and try mounting the drive (on the left side, like in Nautilus), but it tells me:
```
Unable to mount device
```

It works perfectly if I am in gnome. How can I get it to work in IceWM ?
It also does this for CD ROMs too, so it has something to do with automounting, but I don't know what.

Any thoughts or suggestions ?

Dr Small

---

### Post by skymera on 2007-12-10
try:

sudo mount -a

---

### Post by Dr Small on 2007-12-10
It didn't help.
Ok, so let me ask it a little differnetly this time, so it should be easier.

How can I find out what the name of my USB is, and then mount it via the command line?
Like, ```
mount /dev/hdc /media/CORSAIR
``` Only, it isn't named hdc. So how would I find out what it was called ?

Dr Small

---

### Post by Dr Small on 2007-12-10
Solved. I figured it out from reading another thread:
```
sudo fdisk -l
sudo mount /dev/sdc1 /media/CORSAIR
```

Now all I have to do, is make an alias to make that shorter :D

---

### Post by crjackson on 2007-12-10
> **Dr Small said:**
> It didn't help.
Ok, so let me ask it a little differnetly this time, so it should be easier.

How can I find out what the name of my USB is, and then mount it via the command line?
Like, ```
mount /dev/hdc /media/CORSAIR
``` Only, it isn't named hdc. So how would I find out what it was called ?

Dr Small

Never mind, you were too quick on the post :)

---

### Post by Dr Small on 2007-12-10
Hmm. Well now my CD ROM isn't mounting while in Gnome... It should at least auto mount or have an entry in Nautilus (and even show on the desktop), but it isn't doing any of that, yet my USB still works...

Now I can't access any CD ROMS!

Dr Small

---

