---
title: "GRUB Error 22"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by wrgarrett on 2008-02-09
I installed Ubuntu on an external drive and all was working well. I could select to boot XP or Ubuntu on startup. This morning, while Ubuntu was booting, the power cable became disconnected before boot was completed. Now, I can't boot XP or Ubuntu. I get a GRUB Error 22. I can't even run Ubuntu off the Live CD. I have a Kubuntu CD and it will run off the CD, which I am on now. I tried re-installing Ubuntu but it gives me an error message that the file system cannot be created. I tried to re-format the external drive but get the same error that file system cannot be created. I tried installing Kubuntu and same message about file system. I need to get XP open, I tried my XP CD and it won't boot off that either, gives the GRUB Error 22 message even with the external drive disconnected. I'm sweating bullets here! Can anyone help?

---

### Post by sandysandy on 2008-02-09
have a look at this

[http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html](http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

### Post by buntu_Geek on 2008-02-09
Try installing the grub through the Kubuntu LiveCD..

But i m not that much used to Kubuntu....

---

### Post by ajgreeny on 2008-02-09
Start by restoring the windows MBR using the recovery module, or whatever it's called on the windows install CD.  Once you've done that you can use the kubuntu live CD to reinstall grub, but better put it on the external CD than the internal one.  Now set your BIOS to boot first from the external and second from the internal drive so that at boot time, you machine will boot of the external if it is attached and go to grub but from the internal drive if there is no external drive to boot from, and go straight to windows.  This is an elegant way to deal with external drive OSs which may not always be present on the machine.

Boot into the kubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on an external disk, use hd1, etc as appropriate for your external drive.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

---

