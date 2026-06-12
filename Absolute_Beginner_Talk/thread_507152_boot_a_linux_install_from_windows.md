---
title: "boot a linux install from windows"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by infurno on 2007-07-22
Hello everyone,

I have been successfully searching this forum to get answers to all my questions until now. 

I installed linux to a WD passport HDD that I use at home, school, work, and pretty much any other computer I want to boot a personal desktop onto. Its really great, works perfect. But sometimes, especially at home I would like access to my ubuntu os from within windows.

The problem is that at home I really count on windows because I do a lot of professional graphics work / video editing / sound editing.

 I have found many guides here that demonstrate how to boot windows from linux. What I would really like to do is be able to boot my linux install from my usb WD drive in windows. I have tried setting this up through vmware, qemu, and others with no success. They seem to all want to run linux from an image file, or a native install through the VM software.

Could someone please write out a few steps in how to boot a linux install from under windows?

Thank you for your time :)

---

### Post by iUSER-Mike on 2007-07-22
Hello infurno, I'm using Vista Home Premium at mo. Installed Microsoft's Virtual PC 2007.It says its not supporting Vista but you run it anyway. I have Suse 10, Ubuntu Studio(just up and running tonight, no mouse yet though) and lastly XP pro Sp2 is my final virtual machine which runs any thing Vista won't, basicaly Wavelab 5.1. 
[http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx](http://www.microsoft.com/windows/products/winfamily/virtualpc/default.mspx)
Its not bad for a freebie.

Install it. Run it.Name a new virtual machine( I name it after the OS I'm going to install),NEXT  choose from the drop down menu the OS to be installed, OTHER for LINUX. NEXT set your chosen memorey.Next create a new Harddrive and give it a size. I think it goes in that order. Then it will run.

Click on CD and click on capture ISO. Point the "Browse button" to the folder where you would have an ISO image of your chosen OS( Basicly take an image of the OS and while you're at it, any other App you want  to install), this is how your CD/DVD Rom drive is emulated.The ISO will begin as the OS disk would in a real machine. And you're away.

Goodluck
Mike:guitar:

---

### Post by bodhi.zazen on 2007-07-22
If you just want access to a few files see here :

[http://www.fs-driver.org/](http://www.fs-driver.org/)

If you want to run Ubuntu within windows take a look at VMWare, VirtualBox, or qemu.

ooops, I did not read your full post ...

Yea, booting from a HD install is not fully supported yet ...

---

### Post by infurno on 2007-07-22
Tried a few other options and just got it working in vmware.  :)

Thanks.

---

### Post by its_toby on 2007-09-04
So it's not possible to access files on your hard drive from a distro running in QEMU from a usb pen drive or portable HD?

---

