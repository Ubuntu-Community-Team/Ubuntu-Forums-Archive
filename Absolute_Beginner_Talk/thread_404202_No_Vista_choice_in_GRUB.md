---
title: "No Vista choice in GRUB"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by advil0 on 2007-04-08
I installed Ubuntu on another partition than Vista, when I reboot with Ubuntu, there is no choice for VIsta.  Any help?

---

### Post by zvacet on 2007-04-08
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub]("http://ubuntuforums.org/showthread.php?t=24113&highlight=grub")

---

### Post by advil0 on 2007-04-08
GRUB is not messed up, i need to add the listing for Vista, I don't know how to do it.

---

### Post by ajmorris on 2007-04-08
> **advil0 said:**
> GRUB is not messed up, i need to add the listing for Vista, I don't know how to do it.

**title		Windows Vista**
**root		(hd0,1)** (*put here what hard disk and partition windows is on. grub starts from 0 not 1 so hd0,1 is hard disk 1 partition 2. if you need help with this go into a command line and type "sudo fdisk -l" and post the ouput here and i will tell you what you need to put here.)
**savedefault**
[B]makeactive
chainloader	+1[/B]

EDIT: sorry i didn't tell you where to put it: edit /boot/grub/menu.lst and down the bottom of you other entries (such as your linux kernel entries) put the stuff i wrote above ^^

---

### Post by Famicommie on 2007-04-08
From a terminal, type ```
sudo fdisk -l
```
That should list all of the hard drives and partitions installed. Make a note of the location that linux assigns to the windows partition (if you are having trouble, it should be the line that contains NTFS). On my computer it's /dev/hda1

Now, from the terminal, type ```
sudo gedit /boot/grub/menu.lst
```
Grub works a little differently than fdisk does. For instance, instead of using letters (hda, hdb, hdc, ...) to indicate different drives, it uses numbers (hd0, hd1,hd2, ...). Also, notice that instead of starting at the number one, it starts its sequence with the number zero. So, in the example of my computer where Windows is located on /dev/hda1, grub would interpret that as (hd0,0). It sounds kind of confusing, but once you think it over it makes sense.

You are going to need to manually add the vista partition to your menu.lst file. My menu.lst file looks like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista RC1
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

The most important thing is the root part. That must point to your windows partition in grub format. So if it's the second partition on your third hard drive, it will be (hd1,2).

---

### Post by millyd03 on 2007-04-11
i had previously edited my menu.lst file to boot vista by default (moved it to the top).  when i installed the new updates for ubuntu today it overwrote vista in my menu file.  my vista partition is on /dev/sda2.  I tried the proceeding suggestion with root being (hd0, 1) and got an error 11: unrecognized device string when i tried to boot vista.  any ideas?

---

### Post by millyd03 on 2007-04-11
anybody?

---

### Post by confused57 on 2007-04-12
> **millyd03 said:**
> i had previously edited my menu.lst file to boot vista by default (moved it to the top).  when i installed the new updates for ubuntu today it overwrote vista in my menu file.  my vista partition is on /dev/sda2.  I tried the proceeding suggestion with root being (hd0, 1) and got an error 11: unrecognized device string when i tried to boot vista.  any ideas?
There's no space in your root entry:
```
root (hd0,1)
```

if you had (hd0, 1), it wouldn't work.

When there's a kernel update, update-grub is run and anything you added between ###BEGIN AUTOMATIC KERNELS LIST  and  ###END DEBIAN AUTOMAGIC KERNELS LIST will be deleted.

You Vista entry should be either at the very end of your menu.lst or just above the ###BEGIN AUTOMATIC...

---

