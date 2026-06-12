---
title: "Some advice on dual installation of XP and Linux"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by RedRat on 2008-02-29
Need some advice on the better way to go here. I have a good computer running an AMD 64 processor and would like to install Ubuntu on it. However, the hard disk is sort of full. I know that you can use stuff like Partition Magic to free up some space and then go through the dual boot process by formatting the new space. Of course I have heard the horror stories about GRUB and MBR etc. 

In order to minimize boot problems and possible loss of data, here is what I am thinking:  buy a second hard drive since they are relatively cheap and installing that in the machine then installing Ubuntu on that drive. 

Any advice or ideas when I do this?? What should I look out for?

---

### Post by glennric on 2008-02-29
The real horror story is the possibility of Partition Magic messing up when it resizes the partition and losing all of your data (if it is not backed up).  If you have XP installed and install Ubuntu after that then you should have no problem with grub.  Whether you install Ubuntu on the same drive or on another driver, grub will be installed on the MBR of the first hard drive.

---

### Post by dstew on 2008-02-29
Yes, get another drive, install Ubuntu on it, and install grub into the MBR of the first drive. The MBR is on track 0 of that drive, which is not part of any partition, and it won't hurt your Windows install.

---

### Post by gpilkay on 2008-02-29
Yes, I've done that myself.  What I did with two IDE drives is I mounted the new one as Master, with the existing XP drive as Slave (making sure to change the dip switch settings appropriately) then I started from a Live-CD, going from there.  The XP MBR was untouched and Grub got loaded on the Ubuntu drive to handle all the duel-booting.  As such, I can just change a switch and cable and XP goes right back to how it was.

If you have a different kind of drive, you may have to adjust the procedure a bit, but I'm sure you can find detailed versions on-line.

Edit:  I should note that set this way, while I can access the XP drive from Ubuntu, Windows has no idea Linux exists on this machine.  Just one potential warning.

---

### Post by glennric on 2008-02-29
> **gpilkay said:**
> Edit:  I should note that set this way, while I can access the XP drive from Ubuntu, Windows has no idea Linux exists on this machine.  Just one potential warning.

This is not true.  Windows knows the drive is there.  If you look closely at the management of storage devices the drives will show up.  If you install ext2fsd or ext2ifs you will be able to access the linux partitions from windows.

---

### Post by Duck2006 on 2008-02-29
With the price of hard drives these days if would be the way to go.

---

### Post by jipetoe on 2008-02-29
i am fairly new to linux but i have been using ubuntu ,booting off of a flash drive but i would like to create a dual boot with my xp is it possible to do this with an external drive via the usb?

---

