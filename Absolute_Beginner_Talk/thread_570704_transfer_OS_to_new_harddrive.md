---
title: "transfer OS to new harddrive"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by FITorion on 2007-10-08
The hard drive the OS is on is dieing.

I'm running software raid. I don't want to lose my settings and thus my data.  Is there a way to migrate the OS over to a new hard drive?

I'm running 64 bit edgy eft 6.10

---

### Post by psusi on 2007-10-08
Mount the new drive somewhere, say /mnt, and then sudo cp -ax / /mnt.  This will copy all files on your root partition to the new drive.  Then you'll have to install grub on the new drive so it will boot.

---

### Post by FITorion on 2007-10-10
ok after much trial and tribulation I have formated, made a filesystem and mounted the new hard drive.

at mnt/new

I then did:

sudo cp -ax / /mnt/new

now it's thinking

how do I install grub to the new drive without over writing? once that's done can I just remove the old drive and plug the new drive in it's place?

---

