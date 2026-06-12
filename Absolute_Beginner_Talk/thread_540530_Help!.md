---
title: "Help!"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by jasonhr on 2007-09-01
I am a complete newbie here and I put a new hard disk on my feisty setup but I couldn't write to it.

I saw a post telling me to try the following:

 /dev/Data /wind vfat user,exec,auto,defaults,quiet,umask=0,rw 0 0

I still can't write to the disk and now I can't see any other computers on the network either...

If anyone can tell me what I did wrong I would be most appreciative!

---

### Post by taurus on 2007-09-01
What drive/partition are you wanting to mount anyway?

```
sudo fdisk -l
```

---

### Post by jasonhr on 2007-09-01
Well that is the other thing, I have formatted the disk on a windows machine with NTFS then just plugged it in. I can see it but can't write to it and am not sure how to identify it...

Sorry fofr sounding so dumb but I have literally started using linux tonight!

Ah! Sorry, just re read your post and did the fdisk thing, it is hdb1 I think...

---

### Post by taurus on 2007-09-01
If you want to write to ntfs filesystem, then you need to install and use ntfs-3g, not vfat.  Vfat is for fat32 filesystem.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by jasonhr on 2007-09-01
OK, how do I format it linux style?

---

### Post by taurus on 2007-09-01
> **jasonhr said:**
> OK, how do I format it linux style?

Do you mean convert it to ext3 filesystem?

Applications -> Accessories -> Terminal
```
sudo mke2fs -j /dev/hdb1
```
_Make sure_ it is /dev/hdb1 and there is nothing important that you need to backup first or you can kiss your data on it good bye.

---

### Post by jasonhr on 2007-09-01
Heh! Is a blank disk:)

Really appreciate your help here.

While that is re-formatting, any ideas on how to get my network back? I had a single shared file on samba set up and have been using it as a mapped drive from my wi***ws machines as back up for my work stuff but now I can't see it from my other machines. Any idea how I can restore that connection?

---

### Post by jasonhr on 2007-09-01
Also, the disk is now formatted and is giving this in Fdisk:

/dev/hdb1   *           1       48641   390708801    6  FAT16

I can no longer mount it either and can't see it anywhere....  

How do I access it now?

---

### Post by taurus on 2007-09-01
Why don't you reboot and post the output of this command after you've logged in again.

```
sudo fdisk -l
```
That's a lower case letter L.

---

### Post by jasonhr on 2007-09-01
Power pack just keeled over on the linux machine....  :(

Can I get back to you?

---

