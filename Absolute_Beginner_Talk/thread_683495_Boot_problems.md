---
title: "Boot problems"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Pawka on 2008-01-31
I have problems with starting my Ubuntu. I can not boot up even recovery mode. Every time when my laptop starts, boot process goes into loop with some error. After I click Alt + Ctrl + Del, it shows me GDM error. I've booted my laptop from Live CD (with Live CD Ubuntu boots without almost problems), mounted my Linux partition. There are repeating messages in syslog (same from the loop, I've wrote before):

Jan 31 09:18:28 pawka-laptop kernel: [  376.616000] gspca: probe of 1-4:1.0 failed with error -5
Jan 31 09:18:28 pawka-laptop kernel: [  376.892000] usb 1-4: new high speed USB device using ehci_hcd and address 53
Jan 31 09:18:28 pawka-laptop kernel: [  377.048000] usb 1-4: configuration #1 chosen from 1 choice
Jan 31 09:18:28 pawka-laptop kernel: [  377.048000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
Jan 31 09:18:29 pawka-laptop kernel: [  377.256000] usb 1-4: USB disconnect, address 53
Jan 31 09:18:29 pawka-laptop kernel: [  377.256000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera

Yesterday after few times, OS boots up, even I didn't change anything. Today at work I'm trying love this problem ;-)

---

### Post by njparton on 2008-01-31
There are a few references to USB devices there.

Are you using a USB keyboard and mouse?  If not, turn off USB ports in the bios and try again.

If you are, try unplugging all other USB devices such as printers etc to see if they're causing the problem.

If that doesn't work, post your hardware back here (MB, CPU, RAM etc).

---

### Post by Pawka on 2008-01-31
I'm using USB mouse, but I think it is not a problem. My integrated webcam is recognized as USB device. There is my lsusb content:

pawka@pawka-laptop:~$ lsusb
Bus 005 Device 005: ID 046d:0896 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  

I've finaly boot up somehow, but I'm afraid that this problem will repeat next time when I'll restart my laptop. I think this is kernel problem, because with older ones everything was OK.

---

### Post by dark_harmonics on 2008-01-31
Do you use anything that your computer might consider to be a boot device? I recently had a problem where if I had my ipod connected it wouldn't start correctly. 

You should try disconnecting all devices from your laptop before boot as a test. 

I have to say, your system sounds very unstable right now. It goes without saying that you should backup everything while you can. I guess i dont understand enough about the internals about how the linux boot process works, because i would be re-installing if i had your error.

---

### Post by Pawka on 2008-01-31
My laptop boot sequence is as follow: 1. CD-ROM, 2. HDD. So I don't think, that laptop tryes boot from my USB mouse or integrated web cam :-)

---

### Post by Pawka on 2008-02-01
Problem still repeats. Maybe then someone have idea how disable my webcam drivers on system boot?

---

### Post by dstew on 2008-02-01
Add the kernel parameter **nousb** to the kernel boot line. You can add it temporarily at the grub menu by using the 'e' key, or permanently by editing the /boot/grub/menu.lst file. At least this might get your system booted. But maybe then your mouse won't work!

---

