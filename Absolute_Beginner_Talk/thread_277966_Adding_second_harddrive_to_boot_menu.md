---
title: "Adding second harddrive to boot menu?"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Qwertinsky on 2006-10-15
My Windows XP drive is a SATA and I installed a second harddrive (PATA) for linux

When I installed Ubuntu, just to be safe I disabled the SATA drive in the CMOS so Ubuntu would only see one harddrive. I figured I could not mess up Windows that way and I can change the boot order in the CMOS to switch between Linux and Windows.

That works fine but now I would like to add the Windows drive to the boot menu (Grub?) and just have the CMOS set to always boot from the Linux drive first, as now I find myself using Windows less and less, and it's more of a pain in the butt to go into the CMOS everytime to boot into Windows or Linux. Specailly when I am trasfering files back and forth on a USB drive.

---

### Post by anaconda on 2006-10-15
This is a bit complicated, because windows wants to be in primary hd.. 
but it is easy to make windows believe that it is in primary hd.

just add this to the end of yout /boot/grub/menu.lst -file

```

title		Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader	+1
```

to edit you need to be superuser, edit eg. with command:
sudo nano /boot/grub/menu.lst

to transfer files between windows and linux you need to mount your windows partition to some directory in linux. 

To do that in terminal type:

sudo mkdir /windows
sudo mount -t ntfs /dev/sda1 /windows
and then you can access your windows partition from /windows -folder..

---

