---
title: "Guide: How to install Windows 7"
date: 2012-05-26
forum: Any Other OS
---

### Post by usernamoftheubuforums on 2012-05-26
This is a guide on how to install Windows 7 after having Ubuntu installed on your computer.

I'm creating this guide because it was not a simple process for me, and it took much much longer than it should have.  I personally am planning to install another linux distro as dual-boot, but I'll leave that part out of the guide.

**1)** **Format your hard drive to NTFS** **and Edit flags as "Bootable"**
      If you do not do this, there's a good chance the GRUB loader will get in your way. There are a few ways of doing this, one way is using GParted. GParted didn't work for me, so I'll explain using another method.
     The easiest way I found was to boot up from the Ubuntu disk. When you are given the choice between "Just Trying" and "Install Ubuntu", choose "Just Trying". This will allow you to manipulate your drive with the Disk Utility.     Now open the Disk Utility in Ubuntu. (Press Super key and  type in "Disk Utility" and it'll pop up).  Select the drive that you want to format. Click Format drive at the top, and select Master Boot Record for partition type. Now click Format Volume and select NTFS. **Important: Now click "Edit Partition" and click the box that says "Bootable". If you do not do this the hard drive will not recognize the Windows boot disk.**
Your drive should now be ready, you can shut down the system and install Windows.



**2) Installation for 64-bit Windows**

Now, for some mysterious reason, my system would not recognize any of my Windows 7 64-bit disks, while it would recognize my 32 bit disk. 
If you are having this problem, then find a USB drive to boot off of. It should be 4 GB or larger.
You'll need a program that will put the appropriate files on your USB, (not just the .iso).
I used **"Windows 7 USB/DVD Download Tool" **from Cnet.com.  You'll simply select your iso and USB and the tool will do the rest of the work.

**Important: You will have to modify your BIOS settings to boot off a USB.** 
Unplug all of your USB devices except for your USB with the bootable iso. Plug this into a USB 3.0 port or the install will be extremely slow.  (I haven't tried a 2.0, so check elsewhere before trying)
USB 3.0 ports should be **[COLOR=Blue]Blue[/COLOR]**. Now start up your system and access your BIOS. (for my Motherboard, I press Delete on startup). 
In the BIOS, navigate to Hard Disk Drives. Select a drive, and your USB should be available to select. If it is not, you'll have to restart and try again. Now, navigate to "Boot Sequence" and select your USB drive to be first in the boot sequence.

You should now be able to install windows.
Good Luck!

[B][SIZE=2]
[/SIZE][/B]

---

### Post by SageO on 2012-06-07
I'm most likely going down this route within the next few days.
Any way to keep my current Ubuntu setup and install Win7 side by side?

---

### Post by wilee-nilee on 2012-06-07
> **SageO said:**
> I'm most likely going down this route within the next few days.
Any way to keep my current Ubuntu setup and install Win7 side by side?

Yes but don't follow this thread it is poorly put together and specific to a users experience, which shows the lack of in general.

Start your own thread if you need help.

---

