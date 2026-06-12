---
title: "Monitor Resolution"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by bman on 2006-05-14
My resolution is set too 1024x768, which normally in Windows I have it to one higher. I have a ATI Radeon 9600 series card...do I need to install drivers, or what.

If I do, where and how do I install them??


Thanks

---

### Post by MasonM on 2006-05-14
The ATI website has a Linux driver installer you can download. Run it as root and it will install the driver for you. Then simply edit your xorg config file to use the new driver.

---

### Post by 23meg on 2006-05-14
Check [this thread]("http://ubuntuforums.org/showthread.php?t=83973") out if you haven't.

---

### Post by bman on 2006-05-14
Thanks, I'll give that a try when I have a chance.

---

### Post by Aximilli on 2006-05-14
[QUOTE=MasonM]The ATI website has a Linux driver installer you can download. Run it as root and it will install the driver for you. Then simply edit your xorg config file to use the new driver.[/QUOTE]

I downloaded this file but couldn't run it. What do you mean by 'Run it as root"?

---

### Post by catlett on 2006-05-14
If you went to this sight and downloaded the installer.[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)
You will follow the directions here.[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.24.8-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.24.8-inst.html)
To clarify. Download it with firefox.
Firefox will download it to your desktop but drag it into your home folder to make life easy.
> Enter the command sh ./ati-driver-installer-8.24.8-i386.run to launch the 32bit version of the ATI Proprietary Linux driver installer or sh ./ati-driver-installer-8.24.8-x86_64.run to launch the 64 bit version of the ATI Proprietary Linux driver installer. The ATI Proprietary Linux Driver Setup dialog box is displayed.
That is from the page. This is about your system. The first one is for a 32 bit system and the second is 64. I'm going to use 32 for the example.
You should be able to just run this command in the terminal because it's in your home folder and you don't have to be root.```
sh ./ati-driver-installer-8.24.8-i386
```. If things go right the dialogue should open.
If there is a problem try ```
sudo sh ./ati-driver-installer-8.24.8-i386
```. That makes you root for that command. If there is an error post it. I don't have ATI and I never ran this installler. I just checked the link and tried to interpret it a bit for you.
But post any error, if I'm stumped someone else will join in and save the day.

---

### Post by bman on 2006-05-14
I can't download or find the -i386 version, i can only get the x86 version??

---

### Post by catlett on 2006-05-14
I just checked the website and you're right. That is odd. The quote I give is fvrom there installation how to but when you go to the download site the 1386 is not an option. I would try it with the x86 and see what happens, ```
sh ./ati-driver-installer-8.24.8-x86.run
``` What happens when you download the x86 and run that command?

---

### Post by bman on 2006-05-14
nothing, says directory or file is invalid, something like that

---

### Post by ZiLOG_Z80 on 2006-05-14
If i remember right I had to ```
chmod a+x ati_driver_name.run
```
before it would let me run it to install

---

### Post by bman on 2006-05-16
[QUOTE=catlett]I just checked the website and you're right. That is odd. The quote I give is fvrom there installation how to but when you go to the download site the 1386 is not an option. I would try it with the x86 and see what happens, ```
sh ./ati-driver-installer-8.24.8-x86.run
``` What happens when you download the x86 and run that command?[/QUOTE]

I tryed that and this is what I get...

ATI Technologies Linux Driver Installer/Packager
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: Xorg 7.0.0

Detected version of X does not have a matching 'x700' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x410        XFree86 4.1.x
    x420        XFree86 4.2.x
    x430        XFree86 4.3.x
    x680        X.Org 6.8.x
    x690        X.Org 6.9.x
Removing temporary directory: fglrx-install
bman@ubuntu:

---

### Post by ZiLOG_Z80 on 2006-05-16
It appears the driver doesnt support the Xorg version you are running so I would suggest you override wth the nearest version which is 6.9```
X_VERSION=x690 ./ati-driver-installer-8.24.8-x86.run
```

---

### Post by bman on 2006-05-16
Alright, I'll give that a try

---

### Post by bman on 2006-05-16
It says no such file or directory?

---

### Post by ZiLOG_Z80 on 2006-05-16
are you in the directory with the ati installer if so I'm not sure whats going on, i was just following the instructions given in the outmut in your post, sorry

---

### Post by bman on 2006-05-16
frig, whats going on,

---

### Post by bman on 2006-05-16
Does the driver file need to be in a certain place?

---

### Post by ZiLOG_Z80 on 2006-05-16
should be ok as long as your console is in the same directory as the installer, easiest if its in you home as thats where new consoles start

---

### Post by ZiLOG_Z80 on 2006-05-17
ok had a bit of spare time so decided to have a bit more of a look at this as im not a linux expert

```
X_VERSION=x690 ./ati-driver-installer-8.24.8-x86.run
```

works but states 'You need to run this installer as the Super-User'. So I tried```
sudo X_VERSION=x690 ./ati-driver-installer-8.24.8-x86.run
``` and get the error ```
sudo: X_VERSION=x690 command not found
```

seems sudo assumes X_VERSION=x690 is the comand not an option, so in order to do it with super-user (root) privilages without a root password, use```
sudo su
X_VERSION=x690 ./ati-driver-installer-8.24.8-x86.run
``` and it should now work

---

### Post by bman on 2006-05-20
why can't things like this be simple, still dosen't work, I did the last thing you posted. asked for password, etc etc...

entered X_VERSION=x690 ./ati-driver-installer-8.24.8-x86.run....gave me permission denied...

wtf

---

### Post by ZiLOG_Z80 on 2006-05-20
that should just be your normal password you use to logon

---

### Post by bman on 2006-05-20
no i entered the right password, but thats the error it gives me anyways

---

### Post by bman on 2006-05-21
I guess this is a problem that can't be fixed?? or what

---

### Post by ZiLOG_Z80 on 2006-05-21
sorry, I'm out of ideas, after doing
sudo su
you should be root and therefore have permission

---

