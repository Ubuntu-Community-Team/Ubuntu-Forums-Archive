---
title: "NTLDR missing"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by martunes13 on 2007-05-12
I have a happily working dual boot setup (Ubuntu Feisty and WInXP) in my computer.  However, when I tried it on a friend's computer, it didn't work quite as well.

Let me give a rundown of events:
1. WIndows XP Professional is working fine in computer.
2. Installed Ubuntu Feisty. Restarted after installation. Grub menu is fine.
3. After restart, updated Ubuntu
4. After updating, restarted.
5. The message "NTLDR missing" appeared.
6. If I put a WInXP installation CD, the NTLDR message disappears and the GRUB menu appears.

Is there a way to get the normal grub menu without putting a WinXP installation CD in the drive?  I do not wish to reinstall both WinXP and Ubuntu.  Please help this noob.  Thanks.

---

### Post by BoneKracker on 2007-05-12
Read The Friendly Manual:

# How to fix the 'NTLDR is Missing' error and other NTLDR errors
[http://pcsupport.about.com/od/findbyerrormessage/a/ntldrmissingxp.htm](http://pcsupport.about.com/od/findbyerrormessage/a/ntldrmissingxp.htm)

# How to fix: NTLDR is missing, press any key to restart
[http://www.ntldrismissing.com/](http://www.ntldrismissing.com/)

# Possible causes and solutions to 'NTLDR is Missing' error message
[http://www.computerhope.com/issues/ch000465.htm](http://www.computerhope.com/issues/ch000465.htm)

You also might want to Google NTLDR Missing Linux

---

### Post by Herman on 2007-05-12
Hello martunes13,
There are two kinds of 'NTLDR is missing' errors. 

One kind of 'NTLDR is missing' error usually comes from the BIOS, and if so it normally means the computer is trying to boot up from a non-bootable disk like for example a non-bootable floppy disk or CD-ROM. 
Perhaps you have left a non-bootable floppy disk in your floppy disk drive and when a CD-ROM is in the CD drawer it boots off that, but when there's no CD your freind's computer is trying to boot a non-bootable floppy disk first. Check there is no floppy on the floppy disk drive.
The same goes for usbdisks like USB thumb drives and other such devices, even USB cameras and MP3 players, they are all seen as extra hard disks.

Otherwise, if you installed Ubuntu with a USB disk plugged in, and now it's unplugged, try plugging it back in again and booting and see if that helps. Grub might have installed to MBR in the USB device. 
I think your problem is something along those lines but I don't yet know exactly what.


The other kind of 'NTLDR is Missing' error happens after the Grub menu, when Grub has already done its job abd chainloaded the Windows bootsector and handed over control to Windows bootloader. If there is something wrong in Windows boot.ini file or the partition number has been changed it can result in that error message. I don't think it's that problem this time. More likely it's the first one.

Regards, Herman :)

---

### Post by martunes13 on 2007-05-12
Thanks for the reply BoneKracker and Herman.  I will try your suggestions when I visit my friend this weekend.  Have a great weekend.  \\:D/

---

