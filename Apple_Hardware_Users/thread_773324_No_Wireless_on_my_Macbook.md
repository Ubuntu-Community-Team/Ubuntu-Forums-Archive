---
title: "No Wireless on my Macbook"
date: 2008-04-28
forum: Apple Hardware Users
---

### Post by KC_HYPE on 2008-04-28
Just got started with ubuntu
everything works except the wireless internet 

here's what people seem to want to know:
Wireless Card Type:	AirPort Extreme (0x14E4, 0x8
Wireless Card Locale:	USA
Wireless Card Firmware Version:	Broadcom BCM43xx 1.0 (4.170.46.5)

and i'm using 64 bit ubuntu
i've followed the wiki and other sources but nothing seems to work as when i type commands in the terminal i get some kind of error. 
says that it cant identify the character 'z' in ['xvzy;] or something similar to that, as well as other problems.

---

### Post by cyberdork33 on 2008-04-28
> **KC_HYPE said:**
> Just got started with ubuntu
everything works except the wireless internet 

here's what people seem to want to know:
Wireless Card Type:    AirPort Extreme (0x14E4, 0x8
Wireless Card Locale:    USA
Wireless Card Firmware Version:    Broadcom BCM43xx 1.0 (4.170.46.5)

and i'm using 64 bit ubuntu
i've followed the wiki and other sources but nothing seems to work as when i type commands in the terminal i get some kind of error. 
says that it cant identify the character 'z' in ['xvzy;] or something similar to that, as well as other problems.
you need to be more specific. give a real example of the error message.
Is this the page you are following:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-2f7056245889dcedf7dc1d286118bfda214af23b)

---

### Post by colday on 2008-04-28
> **KC_HYPE said:**
> Just got started with ubuntu
everything works except the wireless internet 

here's what people seem to want to know:
Wireless Card Type:	AirPort Extreme (0x14E4, 0x8
Wireless Card Locale:	USA
Wireless Card Firmware Version:	Broadcom BCM43xx 1.0 (4.170.46.5)

and i'm using 64 bit ubuntu
i've followed the wiki and other sources but nothing seems to work as when i type commands in the terminal i get some kind of error. 
says that it cant identify the character 'z' in ['xvzy;] or something similar to that, as well as other problems.

I tried many links - I also have a MacBook with the Broadcom firmware - none of the links worked.

... Until I found this:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

A quite long process, but when completed I instantly (no reboot) had wireless!

Take your time, follow the directions explicitly & it should work.  Be aware that the "l" looks a lot like the "1"!   Best option would be to cut & paste - and do that one line at a time (watch out for line wraps).

I'm not even an Ubuntu novice (is there a level below that?), and it worked first time through.

Steve

---

### Post by KC_HYPE on 2008-04-28
this is the site i'm using

[https://help.ubuntu.com/community/MacBook?highlight=%28macbook%29#](https://help.ubuntu.com/community/MacBook?highlight=%28macbook%29#)

kevin@kevin-laptop:~$ sudo apt-get install build-essential autoconf automake
[sudo] password for kevin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package autoconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package autoconf has no installation candidate
kevin@kevin-laptop:~$ 

using this site: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
everything goes good until
sudo ndiswrapper -m
then it reads: invalid driver!


i then went to the site listed above and had the same error with "sudo ndiswrapper - m"

i continued and i did get to this:
# /etc/modules: kernel modules to load at boot time. 
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
ndiswrapper

but what's next?

---

### Post by KC_HYPE on 2008-04-28
and once i have everything done (if this ever happens) 
will i just be able to choose "wireless connection" from Network Settings, or is there more to it?

---

### Post by cyberdork33 on 2008-04-28
> **KC_HYPE said:**
> this is the site i'm using

[https://help.ubuntu.com/community/MacBook?highlight=%28macbook%29#](https://help.ubuntu.com/community/MacBook?highlight=%28macbook%29#)That is the wrong page. that is only 1st and 2nd generation Macbooks that have an atheros chipset. You have a broadcom chipset. follow the direction at the link I gave.

> **KC_HYPE said:**
> ```
kevin@kevin-laptop:~$ sudo apt-get install build-essential autoconf automake
[sudo] password for kevin:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package autoconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package autoconf has no installation candidate
kevin@kevin-laptop:~$
```ok then that package doesn't need to be installed. Don't try to install it.

---

### Post by KC_HYPE on 2008-04-28
Ok, i'm just about positive everything is installed correctly

there's still no wireless connection option in Network Settings...
should this just appear or is there something else i need to do?

you have no idea how thankful i am for your help

---

### Post by blurg on 2008-04-29
Can you clarify:

(1) is ndiswrapper installed ok?

(2) which driver did you give to ndiswrapper? where did you get it? - specifically you are on 64 bit so you must have a 64 bit driver for it to work.

I have my BCM4328-based Airport Extreme working in 64bit Ubuntu hardy and yes network manager does its job once you've gotten ndiswrapper going with the correct driver.

---

### Post by cyberdork33 on 2008-04-29
> **KC_HYPE said:**
> there's still no wireless connection option in Network Settings...
should this just appear or is there something else i need to do?
You might try rebooting just to make sure...

give the output of ```
ndiswrapper -l
``` (that's a lowercase L not an i)
and ```
lsmod |grep ndiswrapper
```

---

### Post by KC_HYPE on 2008-04-29
code: 
ndiswrapper -l 

gives: 
bcmwl5 : invalid driver!
(i guess this means no to your first question blurg)

lsmod |grep ndiswrapper 
gives:
ndiswrapper           233632  0 
usbcore               161584  8 hci_usb,ndiswrapper,isight_usb,xpad,usbhid,ehci_hcd,uhci_hcd

---

### Post by cyberdork33 on 2008-04-29
> **KC_HYPE said:**
> ```
ndiswrapper -l 
bcmwl5 : invalid driver!
```
(i guess this means no to your first question blurg)Right on.

remove that driver:
```
sudo ndiswrapper -r bcmwl5
```

then get the driver from your OSX restore dvd as shown here:
[http://ubuntuforums.org/showthread.php?t=735846](http://ubuntuforums.org/showthread.php?t=735846)
you can ignore step 5,6, and 7 as that bug was fixed in Hardy final.

---

### Post by KC_HYPE on 2008-04-29
ok, so i put in the osx disc.
in BootCamp/drivers  i click on broadcominstaller.exe, and cant open it "No application suitable for automatic installation is available for hadling this kind of file"
though i'm not sure i was supposed to try that anyways...

 unrar x broadcomxpinstaller.exe
and
unrar x broadcominstaller.exe (changed it to match the file name... not sure if you can do that or if its right)
these both give:

The program 'unrar' is currently not installed.  You can install it by typing:
sudo apt-get install unrar
You will have to enable component called 'multiverse'
bash: unrar: command not found

so i do as directed (though not enabling 'multiverse', not sure what that means)
and i get:
kevin@kevin-laptop:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

does any of this have to do with 64bit vs 32bit? 
is enabling 'multiverse' my problem?

thanks again

---

### Post by KC_HYPE on 2008-04-29
never mind the multiverse 
that was easy enough to find out :)
unrar is now installed 
but...

kevin@kevin-laptop:~$ unrar x broadcomxpinstaller.exe

UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal

Cannot open broadcomxpinstaller.exe
No such file or directory
No files to extract

tries it as well with broadcominstaller.exe (the actual file name on the disk)


hope this isn't as simple as my mutiverse problem..

---

### Post by cyberdork33 on 2008-04-29
> **KC_HYPE said:**
> never mind the multiverse 
that was easy enough to find out :)
unrar is now installed 
but...

kevin@kevin-laptop:~$ unrar x broadcomxpinstaller.exe

UNRAR 3.70 beta 3 freeware      Copyright (c) 1993-2007 Alexander Roshal

Cannot open broadcomxpinstaller.exe
No such file or directory
No files to extract

tries it as well with broadcominstaller.exe (the actual file name on the disk)


hope this isn't as simple as my mutiverse problem..
I don't really know why it uses unrar since it really is a zip archive, but whatever...

there should be an xp driver package and a vista driver package, just make sure you are using the xp one. If you continue to have trouble, send me a PM and I can help you better.

---

### Post by larrinski on 2008-04-30
Looking in my system profiler I have the Macbook 2,1. I have installed wifi successfully in the past from here [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook"). This time when I try to follow those instructions, I get that it can't find package build-essential when trying both methods, including subversion. I am using 8.04 LTS. I had no problems with 8.04 Betas in the past.  

Any idea why it can't find it? I am connected right now via ethernet, so I have internet access...

Cheers,
Larrinski.

---

### Post by larrinski on 2008-05-02
> **larrinski said:**
> Looking in my system profiler I have the Macbook 2,1. I have installed wifi successfully in the past from here [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook"). This time when I try to follow those instructions, I get that it can't find package build-essential when trying both methods, including subversion. I am using 8.04 LTS. I had no problems with 8.04 Betas in the past.  

Any idea why it can't find it? I am connected right now via ethernet, so I have internet access...

Cheers,
Larrinski.

Now it seems to download using subversion and I get as far as the last step and then I get
> jamie@jamie-desktop:~$ sudo iwpriv ath0 bgscan 0
ath0      no private ioctls.

Any idea why it is not taking? I am running Hardy under Parallels...

---

### Post by cyberdork33 on 2008-05-02
> **larrinski said:**
> Any idea why it is not taking? I am running Hardy under Parallels...
then why would you need to access wifi hardware directly? set the vm settings to share the host connection...

---

