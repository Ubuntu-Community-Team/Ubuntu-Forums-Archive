---
title: "ntfs resize...How long?"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by 8vforever on 2006-09-10
Hi,

I'm in the middle of an Ubuntu install where I decided to install it on my usb disk. I was expecting some troubles during the bootup sequence of my system and upfront printed a guide how to load the usb drivers in the ramdisk.

Unfortunately I haven't gotten that far yet. In order to install an ext3 fs I had to resize my 250GB ntfs partition to 200GB instead. How long is this supposed to take? Currently it's been running 8 hours. Is that expected? I was hoping it would go a bit quicker.

Unfortunately I can't really use my desktop for anything besides using the contents on the LIVE DVD:(

Thanks

/Lars

---

### Post by jordanmthomas on 2006-09-10
It usually takes my computer about 35 minutes to knock off 30 gigs.

8 hours?  Jeez, sounds like something is not going right.

---

### Post by 8vforever on 2006-09-10
Yeah I was afraid that something might have messed up and don't want to interrupt the process if it has messed up the NTFS.

---

### Post by jordanmthomas on 2006-09-10
I don't know what you should do about it though.  Chances are, you'll just have to try and cancel it.  I have had to do it when resizing ext3 drives and usually they survive.  I'm not going to suggest you do anything because I have no idea what you should do.
Sorry and good luck.

---

### Post by Abstract on 2006-09-10
When I used my GParted CD to resize NTFS it had been running for 30 minutes before I stopped it. When I stopped it my whole drive and every partition on it was unbootable. The data was expendible but I wouldn't recommend stopping it.

Also i've been told over IRC that NTFS is not resizable.

Edit: I just noticed the above means it could go on for ever, so I dunno :/

---

### Post by jordanmthomas on 2006-09-10
NTFS is resizable (I've done it many times), but it's really picky and can go wrong easily.

---

### Post by Abstract on 2006-09-10
> **jordanmthomas said:**
> NTFS is resizable (I've done it many times), but it's really picky and can go wrong easily.

Yeah I have done it once successfully using the extremely expensive PartitionMagic but I've tried three times with Linux and its never worked. I guess I'm just unlucky.

---

### Post by 8vforever on 2006-09-10
I just aborted the process.
All my data seems to be intact and the NTFS partition is the same size. I should get one of my 300GB disks back tomorrow so I'll probably load the data on to that and try installing Ubuntu again when I get time for it.

/Lars

---

