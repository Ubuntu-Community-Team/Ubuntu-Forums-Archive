---
title: "My slave HDD isn't recognised by Ubuntu..."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by groovestix on 2007-08-18
... but it's recognised by BIOS.

I have the latest Ubuntu, and I am unsure what other details I should share... Please help!

---

### Post by taurus on 2007-08-18
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
That wold be lower case letter l as in larry.  And just so you know, you need to mount your second harddrive before you can access it.

---

### Post by groovestix on 2007-08-18
Disk /dev/hda: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4798    38539903+  83  Linux
/dev/hda2            4799        4867      554242+   5  Extended
/dev/hda5            4799        4867      554211   82  Linux swap / Solaris



Wow, that was super-quick!

P.S. How do I mount?

---

### Post by taurus on 2007-08-18
What type of harddrive it is, EIDE or SATA, because Ubuntu doesn't recognize it?

Are you sure the BIOS reports there are two drives?

---

### Post by groovestix on 2007-08-18
Yes, I can see it in BIOS. I can actually see it in Ubuntu. Here are some screenshots.

[IMG]http://groovestix.googlepages.com/Screenshot-DeviceManager1.png[/IMG]

[IMG]http://groovestix.googlepages.com/Screenshot-DeviceManager2.png[/IMG]

P.S. I think that there's Windows installed on the slave drive, does that make a difference?

---

### Post by groovestix on 2007-08-18
Sorry for the huge sized screenshots, 
I think the drive is "IDE" from what I can read from some of its stickers.

---

### Post by taurus on 2007-08-18
What exactly do you plan to do with that second harddrive?  Do you want to format it to use in Ubuntu or so you want to read something off the drive, since you said that it has Windows on it?  

If you don't have gparted, System -> Administration, install it.  Otherwise, see if gparted would detect your second harddrive.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install gparted
```

---

### Post by groovestix on 2007-08-18
I just want to backup some of the data and possibly format it. I don't plan to use it with Ubuntu on this machine.
Would gparted work for this?

---

### Post by taurus on 2007-08-18
> **groovestix said:**
> 
Would gparted work for this?

Can't tell you unless you run it.

---

### Post by crispy_420 on 2007-08-18
Partitioned at NTFS?

---

### Post by groovestix on 2007-08-18
Wow, this is the best message board I've ever used! Thanks a lot, I'll be back with some feedback after I finish installing.

[edit] crispy_420, I am unsure, but pretty sure that it's NTFS. :)

---

### Post by taurus on 2007-08-18
> **crispy_420 said:**
> Partitioned at NTFS?

Even if it's ntfs, shouldn't it show up on "sudo fdisk -l" as something like /dev/hdb1?

---

### Post by groovestix on 2007-08-18
Okay, after installing GParted, I see it as a unallocated partition with unallocated filesystem. This means that it's empty right?

---

### Post by taurus on 2007-08-18
It means that you need to create a filesystem on it before you can use it.  Now, you can either format it, /dev/hdb1, to ntfs or ext3.

It also means there is nothing on it as you thought there's Windows on it.

Post a screenshot of gparted, pointing to /dev/hdb, if you wish.

---

### Post by groovestix on 2007-08-18
I see. How can I format it to NTFS partition?

---

### Post by taurus on 2007-08-18
There is an option in gparted that would allow you to format the drive to whatever filesystem you want, [http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php).

---

### Post by groovestix on 2007-08-18
Zesty! Thank you! I will read through, and hopefully not get lazy to ask 666 questions again.

---

