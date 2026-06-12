---
title: "Can't detect usb using Ubuntu Host in Virtual machine"
date: 2012-03-14
forum: Apple Hardware Users
---

### Post by nickypeh on 2012-03-14
Hi All, 
I am using MAC OS X or LION. 
I have installed the virtual machine from oracle in order to run Ubuntu. Using the virtual machine, I am able to boot and run the program such as x-term (beginner) without any problem.  There is a problem, I plug in my pendrive or flash disk into my usb port. My Host OS MAC is able to detect the flash memory but in the ubuntu OS side, I could not access to the flash memory. Even when I am using the x-term to access but it shows nothing. The command I am using is "sudo fdisk -l". 
Is there any setting i need to set for the virtual machine or any software i need to install? 
Please help in this matter. 

Regards, 
Nicky

---

### Post by NoBugs! on 2012-03-16
> **nickypeh said:**
> My Host OS MAC is able to detect the flash memory but in the ubuntu OS side, I could not access to the flash memory.

You're only allowed to have it mounted in one, either host or guest. Unmount it and you should have an option to enable device in guest OS.

---

