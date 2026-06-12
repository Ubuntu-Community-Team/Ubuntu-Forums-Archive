---
title: "disadvantage of USB boot"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by gitwick on 2008-04-02
what are disadvantages if i install and boot linux from an external usb hard disk

---

### Post by LowSky on 2008-04-02
USB is slower ( wont realy notice) than internally installed hard drive

---

### Post by Diabolis on 2008-04-02
Disk space could be a issue also.

---

### Post by spyder99 on 2008-04-02
I have had trouble getting other usb devices to work while running on a usb install.

---

### Post by gitwick on 2008-04-02
hey 
THANK YOU!!!

but the poblem is that i want dual boot vista and linux
the vista partioner doesnt give give enough space when i use the shrink drive tool
even though there is around 25 gb free space i cant get more than 4 gb free space is there a way to get more space


:confused::confused::confused::confused:

---

### Post by Diabolis on 2008-04-02
Use gparted through a live-cd. It will let you resize any partition.

---

### Post by Calash on 2008-04-02
If your swap space is on the USB key this could eventually lead to a failure.

> 
Like all flash memory devices, flash drives can sustain only a limited number of write and erase cycles before failure. Mid-range flash drives under normal conditions will support several hundred thousand cycles, although write operations will gradually slow as the device ages. This should be a consideration when using a flash drive to run application software or an operating system. To address this, as well as space limitations, some developers have produced special versions of operating systems (such as Linux in LiveUSB) [17] or commonplace applications (such as Mozilla Firefox) designed to run from flash drives. These are typically optimized for size and configured to place temporary or intermediate files in the computer's main RAM rather than store them temporarily on the flash drive.


I have not tried the USB linux setups yet, so I am not sure if it will be a problem, but it is something to be aware of for long-term use.


Edit:  I am an idiot today...misread USB harddrive for USB flashdrive.  Ignore the above, it does not apply to your situation.

---

### Post by JustAboutRealJAR on 2008-04-02
> **Diabolis said:**
> Use gparted through a live-cd. It will let you resize any partition.

Last time I checked, GParted couldn't resize NTFS partitions

---

