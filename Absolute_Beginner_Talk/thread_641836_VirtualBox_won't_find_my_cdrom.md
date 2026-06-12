---
title: "VirtualBox won't find my cdrom"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by wescrow on 2007-12-15
So i've read a million of these posts and have derived no answers for my problem.  I run Gutsy and I want to use VirtualBox.  I have installed it and it seems to work just fine.  The problem is when I go to mount my cdrom which contains my boot media and the dropdown box is empty so I cannot choose anything at all.  Does anyone know how to make my cdrom available?

---

### Post by popch on 2007-12-16
You can attach either the CD/DVD drive to your virtual machine or an ISO image of a CD or DVD.

While your virtual machine is turned off (not running or saved) open the application VirtualBox. Select the machine which needs the drive. On the right hand side of the window (on the page 'Details') click on the link CD/DVD. 

While your virtual machine is actually running in a Window of its own, the bottom border of that window should contain a few icons resembling disk drives, CDs, folders, mice and so on. Right-klick on the CD icon. VirtualBox should show a menu consisting of entries like 'Attach Drive' and 'Attach Image'.

The names of the items may be different for you. I am not using the English language version and guessing at what they might be called in English.

---

### Post by wescrow on 2007-12-17
Thanks, but I just went with vmware.

---

### Post by malibusurfer2 on 2008-01-02
I am having the same issue. The dropdown box in VirtualBox  is blank (can't choose /dev/cdrom). Ubuntu Gutsy shows CD as /media/cdrom0, and the cd/dvd works perfectly in Ubuntu.

---

### Post by kavoura on 2008-01-08
I get the same problem. VirtualBox only sees one CD drive, which is /dev/cdrom
But I have a CD-RW and a DVD-RW, which are cdrom1 and cdrom0. 
I put a Windows 98 CD-ROM into each drive but neither could be seen by VirtualBox. Considering Ubuntu mounts the CD drives on /media/cdrom0 and /media/cdrom1, why then supply a program that demands a CD to be on /dev/cdrom? Maybe I am not understanding something here.
Is there a way to get Ubuntu to link to a CD drive as /dev/cdrom, or is there a way to edit the settings for VirtualBox to change the default CD location?

I did manage to copy the Windows 98 CD to an ISO file and boot from that, but this does mean that I cannot use any CD-ROMs in the virtual machine, I assume.

---

### Post by popch on 2008-01-08
I just have RTFMed for you.:

11.4.2 Linux host’s CD/DVD drive not found
If you have configured a virtual machine to use the host’s CD/DVD drive, but this does
not appear to work, make sure that the current user has permission to access the cor-
responding Linux device file (usually /dev/cdrom or similar). On most distributions,
the user must be added to a corresponding group (usually called cdrom or cdrw).
   Also, if your CD/DVD device has a different name, VirtualBox may be unable to find
it. On Linux hosts, VirtualBox performs the following steps to locate your CD/DVD
drives:
    1. VirtualBox examines if the environment variable VBOX_CDROM is defined (see
       below). If so, VirtualBox omits all the following checks.
    2. VirtualBox tests if /dev/cdrom works.
    3. In addition, VirtualBox checks if any CD/DVD drives are currently mounted by
       checking /etc/mtab.
    4. In addition, VirtualBox checks if any of the entries in /etc/fstab point to
       CD/DVD devices.
   In other words, you can try to set VBOX_CDROM to contain a list of your CD/DVD
devices, separated by colons, for example as follows:
export VBOX_CDROM=’/dev/cdrom0:/dev/cdrom1’

from: [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
User manual (in PDF), page 115

@kavoura: since you already said that your drives are named /dev/cdrom0 and ..1, it now is clear why VirtualBox does not find your drive.

---

### Post by ebex on 2008-03-23
This is the fix that worked for me.  From the [http://www.virtualbox.org/ticket/775](http://www.virtualbox.org/ticket/775)

"On Gutsy, please install the package libhal-dev (in addition to libhal1) when using VirtualBox 1.5.2. The reason is that VirtualBox tries to load libhal.so dynamically. This lib is only provided by libhal-dev. If this library is not found, VirtualBox will not use hal to enumerate CD/DVD devices. VirtualBox 1.5.4 will look for libhal.so.1 which is the correct link."


  sudo apt-get install libhal-dev

and BAM all my cd drives are enumerated by virtualbox...

---

