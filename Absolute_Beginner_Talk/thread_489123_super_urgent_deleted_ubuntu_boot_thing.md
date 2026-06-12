---
title: "super urgent deleted ubuntu boot thing"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-07-01
super urgent deleted ubuntu boot thing
what should i do i want to recover the files i have installed

---

### Post by zerobinary on 2007-07-01
plz help the data is super important to me  plz i need ur dear help

---

### Post by Alterax on 2007-07-01
First thing is to boot up with your liveCD.  Do that and do a search for how to repair the grub bootloader.  Will grab more info and get back with you on this.  Your data is more than likely still on the drive, as long as you don't reformat it it should be fine for now.

--Alterax

---

### Post by zerobinary on 2007-07-01
ok now i will restart and grab and live cd and wait for u 
thx for the help u have offer me keep up the good work

---

### Post by Alterax on 2007-07-01
1.  Boot your computer with Ubuntu CD.
   2. Go through the install process until you reach "[!!!] Disk Partition."
   3. Select Manually Partition.
   4. Mount the appropriate linux partions:
      /
      /boot
      swap
     ____ DO NOT ALLOW IT TO FORMAT THEM!!!!______
   5. Finish the manual partitioning.
   6. Select "yes" when it asks you to save the changes.
   7. It will give you errors saying that "The system couldn't install ....." after that; ignore them. Proceed with selecting "continue" until you get back to the Ubuntu installation menu.
   8. Jump to "Install GRUB."
   9. Once it is finished, simply restart your computer. 


Courtesy of [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Let me know if this works out for you.

--Alterax

---

### Post by zerobinary on 2007-07-01
the problem is how do i mount it i can't check the thing in order to mount it
```
No root file system is defined.

Please correct this from the partitioning menu.
```
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-3.png[/IMG]

---

### Post by zerobinary on 2007-07-01
i only format the the first two one in the pic the 200 something mb and the swap thing which is the boot thing in window 15 min ago and i can't mount it what should i do
can't mount swap

---

### Post by Computer-Geek on 2007-07-01
Sorry!
         But SWAP is automatically mounted by Linux. U can try to backup the DATA on HDD and reinstall the linux if u dont find anyother suggestions.
Thanks!!

---

### Post by zerobinary on 2007-07-01
can't the data is super important to me i have to recover it 
u know or my boss .....

---

### Post by Alterax on 2007-07-01
Got it!

On the LiveCD open a terminal window.  Do this using sudo fdisk /dev/sda
press p for the partition table.  That'll give you a master printout.  Look for the partition number with the biggest size and note that number

press t Toggle the filesystem type and give it the partition number you found above.  
It'll ask for the hex code for it.  If you used the standard install, it is type 83.
press w to write this to disk and exit

then Quit.  This may be enough to repair the grub loader as well, but if it doesn't, use the method I described above.

Sorry it took so long on this; I had to do this twice before, but it has been about a year ago.

--Alterax

---

### Post by zerobinary on 2007-07-01
```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 9039.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              32        9039    72356760    5  Extended
/dev/sda5              32         219     1510078+   6  FAT16
/dev/sda6             220        9039    70846618+  8e  Linux LVM

Command (m for help): t
Partition number (1-6): 6

```

---

### Post by pardesi on 2007-07-01
do u dual boot

---

### Post by zerobinary on 2007-07-01
no
```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

---

### Post by pardesi on 2007-07-01
can u explain in detail what u have done...(i may not have done exactly this before but let's try hope we can make it)

---

### Post by pardesi on 2007-07-01
were u using ubuntu before thsi problem happened or it was a  fresh install that went wrong

---

### Post by zerobinary on 2007-07-01
i install it like a year ago and it works fine until yesterday i delete the boot thing
[IMG]http://i183.photobucket.com/albums/x196/zerobinary/Screenshot-4.png[/IMG]

---

