---
title: "Removing windows from my computer"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by Danikar on 2008-04-18
Ok so I installed linux on a second partition on my hard drive.

```
/dev/sda
    /dev/sda1 (NTFS Windows)   /media/sda1
    /dev/sda2 (ext3 Ubuntu)    /
    /dev/sda3 (swap)
```

Now I want to remove windows.

Is there a way I can remove windows and make it set up like so

```
/dev/sda
    /dev/sda1 (ext3 Ubuntu)   /
    /dev/sda2 (swap)
```

Without destroying my Ubuntu installation?

---

### Post by seepage87 on 2008-04-18
I'm pretty sure you can just delete the windows partition and use parted to resize you linux partition to absorb the now-free space.

---

### Post by forrestcupp on 2008-04-18
> **seepage87 said:**
> I'm pretty sure you can just delete the windows partition and use parted to resize you linux partition to absorb the now-free space.

That's exactly what I would do.  I would use the [GParted LiveCD](http://gparted-livecd.tuxfamily.org/) to do that because you won't have to worry about any drives being mounted.

---

### Post by Danikar on 2008-04-18
Well yeah that is what I was thinking.

I wonder if GRUB will have any issues with that though.

My grub file looks like this right now

Windows Vista
root (hd0, 0)
makeactive
chainloader +1

Ubuntu 
root(hd0, 1)
kernal /blahblah/kernal some arguments
initrd /blahblah/initrdfile

Will my MBR still be able to find my /boot directory which is on hd0,1 currently? Would hd0,0 disappear or would the ubuntu partition become it.

---

### Post by Danikar on 2008-04-18
> **forrestcupp said:**
> That's exactly what I would do.  I would use the [GParted LiveCD](http://gparted-livecd.tuxfamily.org/) to do that because you won't have to worry about any drives being mounted.

Ok i might check this out then.

---

### Post by Oldsoldier2003 on 2008-04-18
here is a quick tutorial on how to remove windows from a dual boot system. It works for Vista the same way as it does for XP.

[http://ubuntujourney.wordpress.com/2008/04/12/remove-xp/](http://ubuntujourney.wordpress.com/2008/04/12/remove-xp/)

---

### Post by damis648 on 2008-04-18
i would not worry about the grub file, however if it does get confused just boot up with the livecd and change the partitions numbers

---

### Post by mister_pink on 2008-04-18
Grub will get confused, guaranteed. You'll want to boot into the ubuntu live CD and use gparted from there, deleting the ntfs partition then expanding your ubuntu one. Then follow the rest of the instructions on that link that Oldsoldier2003 posted, from 3. Do be careful, grub will now consider that hd0,0 but it will most likely still be called sda2 by ubuntu.

---

