---
title: "Installing ubuntu onto Computer without a CD"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by madmatrixz3000 on 2007-11-13
Ok so my dell laptop has no cd drive, and bios does not recognize usb drives as bootable.

I found this thread [http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

but I cannot find a partitioner that will reformat and shrink my current NTFS partition to accomedate for the 1GB of space I need for the iso and the other boot files.  I need the windows install to move the ISO from a usb stick to the new partition I need to make.

So my questions are.  What is a simple partitioning program that I can use multiple times from a floppy that can resize my Windows Partition?

Are there any GUI Live Floppy disks of easy to use OSs so that I could just repartition the harddrive from scratch?

---

### Post by madmatrixz3000 on 2007-11-13
Sorry about being impatient, but can anyone answer me?

---

### Post by aysiu on 2007-11-13
I would recommend PCLinuxOS's DiskDrake for partitioning.

---

### Post by shad0w_walker on 2007-11-13
The forum regulars are busy on spam patrol ATM so answers will be slow I'm afraid. 

Do not run any thing using the rm command check out the top sticky in the newbies section. Unfortunately a floppy is a little small for a GUI of any really useful nature. Not sure what to suggest.

---

### Post by madmatrixz3000 on 2007-11-13
will wakepup work on finding the Ubuntu Iso or just the puppylinux iso?

Actually I could install puppy to replace what I would use windows for in this process, correct?

---

### Post by madmatrixz3000 on 2007-11-13
Does anyone know how to use wakepup/ what distro of puppy to download?

---

### Post by mike555 on 2007-11-14
You might want to try the latest version of Puppy Linux , wake pup just tells your computer to start puppy when the floppy is in during startup, if the floppy is not in the computer it just starts normally .......

---

### Post by madmatrixz3000 on 2007-11-15
I installed puppy to the harddrive, but I am having problems with the grub file it gives me an error that the root file is invalid or something.  Does someone know what the grub entry should be for a normal install of puppy on the second partition of hd0?

---

### Post by mike555 on 2007-11-15
More info is needed , how did you install Puppy onto your harddrive without a CD player? etc.

---

### Post by Duck2006 on 2007-11-15
> **madmatrixz3000 said:**
> I installed puppy to the harddrive, but I am having problems with the grub file it gives me an error that the root file is invalid or something.  Does someone know what the grub entry should be for a normal install of puppy on the second partition of hd0?

Not sure what you want but the partition will be (hd0,1)

---

### Post by madmatrixz3000 on 2007-11-15
I figured out the stuff with puppy, and have made a live usb.  I am just having problems with booting from usb on the old computer.

I will fill you guys in when I have time, cause I'm sick and need my sleep and thinking it all over and recapping will take alot of time and energy as it took me almost a whole week of research and experimenting.

---

### Post by madmatrixz3000 on 2007-11-16
My computer just gave me a BusyBox command line what do I do here?

---

