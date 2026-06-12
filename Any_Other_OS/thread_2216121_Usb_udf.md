---
title: "Usb udf"
date: 2014-04-10
forum: Any Other OS
---

### Post by zexd2 on 2014-04-10
Hello.

Last night, I wanted to install Win7 installation on my USB. What I did is execute dd which copied files from .iso to USB. It was recognized as UDF and after I did something in Disks, not recognized at all.
GParted says: unnalocated...

Thanks

---

### Post by zexd2 on 2014-04-10
I tried to install windows 7 installation on my USB last night. I did some stuff and now it is unallocated, as GParted says.
fdisk says: Disk /dev/sdb doesn't contain a valid partition table

How can I fix this?

Thanks.

---

### Post by slickymaster on 2014-04-10
Threads merged.

Please do not create duplicates, it dilutes community effort.

---

### Post by Kirboosy on 2014-04-10
OP, I have done this a few times on Windows and using the tool they provide made it really simple.

[Windows 7 USB/DVD Tool]("http://www.microsoftstore.com/store/msusa/html/pbPage.Help_Win7_usbdvd_dwnTool")

There are also manual methods using the command line that you can do it but I'm not sure how to do it off the top of my head.

---

### Post by slickymaster on 2014-04-10
Moved to Other OS/Distro Support.

---

### Post by zexd2 on 2014-04-10
I assumed there would be no confusion, since this is Ubuntu forum. I want to _create_ bootable Windows 7 USB _on Ubuntu_.

---

### Post by slickymaster on 2014-04-10
Here you go: [How to create a bootable Windows 7 USB Drive while using Ubuntu]("http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html")

---

### Post by sudodus on 2014-04-10
It is possible to install Windows from a USB drive, but ***it is not possible to install Windows to a USB drive*** (only the installer works from a USB drive). Maybe this restriction is made in order to make it harder to use the same license in many computers.

Anyway, that restriction does not apply to free software (linux). It works well to make a portable installed Ubuntu (or Ubuntu based) system in a USB drive.

-0-

If you intend to make a Windows install drive, then it should be possible to clone it or to use the tool suggested by *Caboose885* in post #4.

---

### Post by oldfred on 2014-04-10
When you used dd to copy to flash drive it created an image of the ISO like a DVD. That does not have partition table and the beginning of the drive where MBR & partition table normally would be has random data when seen from normal partition tools. Only ISO that are designed as hybrid work with dd copy.

[http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb](http://ubuntuforums.org/showthread.php?t=1509175&highlight=usb)

       Used win7 repair ISO to create USB. used xcopy *.* /s/e/f/h/r/x J:
[http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx)

    

You should be able to totally erase MBR or first sector of flash drive to make it work as a partitioned drive.
       sudo parted -l
Erase - Make double sure you have correct drive & partition, change sdX to correct sdb, sdc etc drive.

 dd if=/dev/zero of=/dev/sdX bs=512 count=1

Some have reported that some of the USB tools do work with Windows and others say it does not. May be versions? You can try unetbootin.
I did try to create a Windows repair flash drive from a Windows repair ISO and never could get it to work. The way I did it was to install ISO to CD which did work and then from Windows repairCD format & copy to flash drive.

---

