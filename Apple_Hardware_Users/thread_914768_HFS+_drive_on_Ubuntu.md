---
title: "HFS+ drive on Ubuntu"
date: 2008-09-09
forum: Apple Hardware Users
---

### Post by super_czar on 2008-09-09
I am planning to attach a new 1TB HDD to my existing Ubuntu server that acts as the media repository, NAS and a webserver

The primary use of the HDD will be o provide aditional storage for my media files (which will be accessed from multiple computers, 3 on Windows and 1 Macbook on Leopard)

However, In adition, I also hope to use the new HDD as the backup drive for Time Machine for the Macbook

Now from what I have read so far, Time machine can be enabled to backup to a networked storage device but it needs to be a HFS+ (with journaling enabled ) drive

How will Ubuntu (i have gutsy gibbon) play with this volume?

---

### Post by schauerlich on 2008-09-09
I would partition the drive into one volume for Time Machine (HFS+) and  then make another partition formatted as ntfs. See [this]("http://www.tuaw.com/2007/11/19/ntfs-on-your-mac-two-ways/") page to enable OS X to read/write to an ntfs partition. Ubuntu should be able to read/write to ntfs in Gutsy, but if you find you can't, try installing the ntfs-3g driver with

```

sudo apt-get install ntfs-3g

```

and reboot. You should be able to read/write to your ntfs partition now.

---

### Post by cyberdork33 on 2008-09-09
working with a network filesystem, it doesn't matter what the physical disk's filesystem is since the server is the only thing that needs to read/write the disk. so NTFS is not neccessary unless you plan to connect the drive directly to the machine you are using to access the data.

In other words, just use ext3 or some other linux native system and setup samba, AFP, or NFS... whatever is suitable for you.

I think that Time Machine requires a AFP share (not a HFS+ filesystem). Checkout netatalk.

---

### Post by dai_vernon on 2008-09-10
I had a similar issue with HFS+ nightmates in linux - the HFS+ suppport in linux is a shaky read-only at best.  I can verify that your best bet is to wait until the new HD comes for the mac and hooking up the hotswap enclosure to your newly working mac.  Trying to use GNU tools to mess with HFS+ is basically nothing but a giant headache.

---

