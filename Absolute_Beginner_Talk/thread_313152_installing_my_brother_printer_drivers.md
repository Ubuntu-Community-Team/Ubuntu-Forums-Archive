---
title: "installing my brother printer drivers"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by MACRI on 2006-12-05
I run a Brother MFC-440CN a driver that is not in the System>Admistration>printer setup thing. i tried downloading the driver from Brother site but failed due to confusion and the lack of abillity to find the correct driver to download. please help, MACRI

---

### Post by yabbadabbadont on 2006-12-05
I looked up your printer on the Brother website and followed the guide to the correct installation instructions for the MFC-440CN.

Partway down the linux drivers page, I found this:
> For Users of DCP-130C,DCP-330C,DCP-540CN,DCP-750CW,FAX-1860C, FAX-1960C,FAX-2480C,FAX-2580C,MFC-240C,MFC-3360C,MFC-440CN, MFC-5460CN,MFC-5860CN,MFC-660CN,MFC-665CW,MFC-845CW, click here.


The provided link points to these installation instructions:
[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html](http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html)

You will have to use "sudo" instead of logging in as root or using "su" like the instructions say.

---

### Post by MACRI on 2006-12-05
i tried and i got these errors...
```

matt@matt-desktop:~$ cd /home/matt/Desktop
matt@matt-desktop:~/Desktop$ dpkg -i --force all mfc440cnlpr-1.0.0-9.i386.deb
dpkg: operation requires read/write access to dpkg status area
matt@matt-desktop:~/Desktop$ sudo dpkg -i --force all mfc440cnlpr-1.0.0-9.i386.deb
Password:
(Reading database ... 129191 files and directories currently installed.)
Preparing to replace mfc440cnlpr 1.0.0-9 (using mfc440cnlpr-1.0.0-9.i386.deb) ...
Unpacking replacement mfc440cnlpr ...
Setting up mfc440cnlpr (1.0.0-9) ...
mkdir: cannot create directory `/var/spool/lpd/mfc440cn': No such file or directory
chown: cannot access `/var/spool/lpd/mfc440cn': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc440cn': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc440cn': No such file or directory


```

---

### Post by MACRI on 2006-12-05
bump, i need to print something really bad sorry if im being annoying or spammy...

---

### Post by Sef on 2006-12-05
Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Brother-MFC-420CN"). It says that it works perfectly, so you should be able to get it up and printing.

---

### Post by yabbadabbadont on 2006-12-05
> **MACRI said:**
> i tried and i got these errors...
```

matt@matt-desktop:~$ cd /home/matt/Desktop
matt@matt-desktop:~/Desktop$ dpkg -i --force all mfc440cnlpr-1.0.0-9.i386.deb
dpkg: operation requires read/write access to dpkg status area
matt@matt-desktop:~/Desktop$ sudo dpkg -i --force all mfc440cnlpr-1.0.0-9.i386.deb
Password:
(Reading database ... 129191 files and directories currently installed.)
Preparing to replace mfc440cnlpr 1.0.0-9 (using mfc440cnlpr-1.0.0-9.i386.deb) ...
Unpacking replacement mfc440cnlpr ...
Setting up mfc440cnlpr (1.0.0-9) ...
mkdir: cannot create directory `/var/spool/lpd/mfc440cn': No such file or directory
chown: cannot access `/var/spool/lpd/mfc440cn': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc440cn': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc440cn': No such file or directory


```

I told you that you would need to use "sudo"...  :)

---

### Post by yabbadabbadont on 2006-12-05
> **Sef said:**
> Read [LinuxPrinting]("http://linuxprinting.org/show_printer.cgi?recnum=Brother-MFC-420CN"). It says that it works perfectly, so you should be able to get it up and printing.

I'm not sure if you were aware that the link you provided tells him to download the drivers from Brother's website...  Was that your understanding and you were just telling him that it should work, or were you saying that support for the printer is already in Ubuntu?  I'm sure I've just misunderstood your post and am being exceptionally thick today.  :)

---

### Post by MACRI on 2006-12-06
OMG hi T.Bot! <3

---

### Post by scc4fun on 2006-12-06
> **yabbadabbadont said:**
> I told you that you would need to use "sudo"...  :)

S/He did.

> **MACRI said:**
> 
<snip non-sudo dpkg call />
matt@matt-desktop:~/Desktop$ sudo dpkg -i --force all mfc440cnlpr-1.0.0-9.i386.deb
Password:
(Reading database ... 129191 files and directories currently installed.)
Preparing to replace mfc440cnlpr 1.0.0-9 (using mfc440cnlpr-1.0.0-9.i386.deb) ...
Unpacking replacement mfc440cnlpr ...
Setting up mfc440cnlpr (1.0.0-9) ...
mkdir: cannot create directory `/var/spool/lpd/mfc440cn': No such file or directory
chown: cannot access `/var/spool/lpd/mfc440cn': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc440cn': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc440cn': No such file or directory

[/code]

---

### Post by yabbadabbadont on 2006-12-06
> **scc4fun said:**
> S/He did.

DOH!  :oops:

I told you I was being thick that day.  :D

---

### Post by MACRI on 2006-12-06
help me please!!

---

### Post by MACRI on 2006-12-06
ok so i installed the driver, now how do i install the printer? its not working!

---

### Post by spockrock on 2006-12-06
btw macri's problem is now fixed he didnt install both the lpr and cupswrapper driver for his printer from the brother site, he now has it working fine......

---

### Post by ubuntu-mike022465 on 2007-03-21
I have the same unit but I'm having difficulty with it.

I've just recently purchased a Brother Multifunction Center MFC440CN, which I will be using in USB mode.

I downloaded the debs from Brother's website. Set up as per Brother's instructions, lpr deb first then cups deb second.

The printer is recognized and shows up in my print manager.

HOWEVER, when I've accessed the printer through [http://localhost:631](http://localhost:631), and made sure all of the settings are correct, when I go to print a test page, I get the error "Ready: printer not connected, will retry in 30 seconds..." and I know my printer is connected as I have the usb cable in the appropriate usb port.

I'm not sure what else I can do next, I've uninstalled and reinstalled the drivers, shut the printer down and restarted, rebooted my computer, etc... but have had no luck.

Any advice would be greatly appreciated

Thanks in advance,

M.


My Computer:

HP Pavilion dv8000t Laptop
Intel Centrino Duo 2 GHz
7600 Nvidia Go 256 mb
100 GB Fujitsu HD
Lightscribe DVD-RW
Synaptic Mousepad
Intel 3945 wireless
etc...

---

