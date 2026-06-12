---
title: "USB disk does not always automount on startup"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2007-08-31
Hi,

I have 2 usb harddisks, both ext3 formatted. When I boot up the computer, the large one (500GB) does not always mount under gnome's mounting system. I can mount it normally under fstab, but this is no good as the device /dev/sdd & /sdc would change if one disk was switched off. My smaller 250Gb disk gets detected every time. But the only way to detect the other one (if it doesnt pick it up automatically) is to unplug its power cable and plug it back in.

Is there a way of asking gnome/nautilus or whatever to 'search new hardware' kind of like you have a 'search new devices' in windows's hardware manager, so i dont have to keep powering off and switching on the device??

As i say, i dont want them to mount under fstab as the device name is not fixed.

While im at it, another question, what s the equivalent of chkdisk as i am woried the drive may have problems of some kind.

---

### Post by dgrafix on 2007-08-31
. oops wrong thread.

---

### Post by schorsch on 2007-08-31
> **dgrafix said:**
> As i say, i dont want them to mount under fstab as the device name is not fixed.
Why not use fixed device names? Instead of using "/dev/sdc" you could use "UUID=095ee613-189c-41e1-a52d-02b7d50ff6c4" (just an example!) as an identifier in /etc/fstab. You get the actual UUIDs for your drives via:
```
blkid -s UUID /dev/sdc
```
These will change if you change anything on your device! And yes, it works for partitions, too .....

---

### Post by dgrafix on 2007-08-31
Great idea!
:lolflag:

---

### Post by Inxsible on 2007-08-31
Or simply use pmount to mount external drives. That way you dont need any entries in the fstab which keeps the fstab cleaner since only my internal drives are listed there and they do not change.

Look at my signature on how to use pmount.

---

### Post by Inxsible on 2007-08-31
> **dgrafix said:**
>  While im at it, another question, what s the equivalent of chkdisk as i am woried the drive may have problems of some kind.

```
fsck /dev/<drive name>
```

---

### Post by dgrafix on 2007-09-02
I mounted all my USB drives now using UUIDs problem is, one of them is mounting as read only(no its not ntfs). Weird thing is, if i try and unmount any disk it says it disagrees with fstab. To unmount, i have to comment out the line in fstab, unmount it, uncomment the ine again in fstab and  then call a mount -a again. Once i do this the drives unmount with no problems.
Its almost as if another program is getting there first before the fstab whenever i reboot.

I noticed a file called mtab which mentions the drives with their device ids (not uuid) could this be causing the problem?

What exactly is the difference between fstab and mtab?

---

