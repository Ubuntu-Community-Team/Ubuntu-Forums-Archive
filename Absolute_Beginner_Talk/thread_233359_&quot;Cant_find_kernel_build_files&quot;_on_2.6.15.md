---
title: "&quot;Cant find kernel build files&quot; on 2.6.15????"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by WalmartSniperLX on 2006-08-10
Im trying to install ndiswrapper for my wireless card/driver. When I try and install it gives me this output:


[I]make -C driver
make[1]: Entering directory `/home/patrick/ndiswrapper-1.22/driver'
Can't find kernel build files in /lib/modules/2.6.15-26-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/patrick/ndiswrapper-1.22/driver'
make: *** [all] Error 2
[/I]


I was told to do try typing in:


*sudo aptitude install build-essentials* from a helpful member here and I got this:

[I]Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "build-essentials"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.[/I]


So what do I need to do to fix this problem so I can install Ndiswrapper?

---

### Post by skale on 2006-08-10
```
sudo aptitude install ndiswrapper
```

Why waste energy?

---

### Post by Jagot on 2006-08-10
It may be asking for the header files:

```
sudo aptitude update
sudo aptitude install linux-headers-`uname -r`
```

Is there any reason you're not using the version of ndiswrapper in the repositories?

---

### Post by WalmartSniperLX on 2006-08-10
> **Jagot said:**
> It may be asking for the header files:

```
sudo aptitude update
sudo aptitude install linux-headers-`uname -r`
```

Is there any reason you're not using the version of ndiswrapper in the repositories?

What do you mean? How do I find that?? sorry im a linux noob :confused: :p

---

### Post by WalmartSniperLX on 2006-08-10
> **skale said:**
> ```
sudo aptitude install ndiswrapper
```

Why waste energy?

Couldn't find package "ndiswrapper".  However, the following
packages contain "ndiswrapper" in their name:
  ndiswrapper-utils ndiswrapper-source ndiswrapper-modules-1.8
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
patrick@patrick-desktop:~/ndiswrapper-1.22$   

Im so confused :(

---

### Post by WalmartSniperLX on 2006-08-10
> **Jagot said:**
> It may be asking for the header files:

```
sudo aptitude update
sudo aptitude install linux-headers-`uname -r`
```

Is there any reason you're not using the version of ndiswrapper in the repositories?

the update did something but the install did this


Couldn't find any package whose name or description matched "linux-headers-uname -r"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

EDIT: OOPS TYPO IN THE CODE

EDIT: nvm same output.

---

### Post by Jagot on 2006-08-10
Copy and paste the code - you did not put exactly what I had said.

And yes, the ndiswrapper in the repositories is ndiswrapper-utils.  You do not need to compile ndiswrapper as you are trying to do now unless you need specific features that are no available in the current Ubuntu version of ndiswrapper:

```
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

---

### Post by WalmartSniperLX on 2006-08-10
> **Jagot said:**
> Copy and paste the code - you did not put exactly what I had said.

And yes, the ndiswrapper in the repositories is ndiswrapper-utils.  You do not need to compile ndiswrapper as you are trying to do now unless you need specific features that are no available in the current Ubuntu version of ndiswrapper:

```
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

OK thank you!!! it installed. I was seaching the list manually for ndiswrapper lol im sorry im such a noob. Thanks again!!!!!!!!!!!!:p :KS :cool:

---

### Post by Jagot on 2006-08-10
You mean how do you use ndiswrapper?

What wireless card do you have?  Are you sure you need ndiswrapper?

The driver you require I think should be a .inf file.  This is the basic method of getting a driver working with ndiswrapper:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
```

The above code actually installs the drive.  My driver happened to be placed in a folder on my desktop - you'd need to change it to wherever you've put your driver.

```
sudo modprobe ndiswrapper
```

The above code starts the module.

```
sudo ndiswrapper -m
```

The above code makes sure that ndiswrapper starts each time you start your computer.

---

### Post by WalmartSniperLX on 2006-08-10
> **Jagot said:**
> You mean how do you use ndiswrapper?

What wireless card do you have?  Are you sure you need ndiswrapper?

The driver you require I think should be a .inf file.  This is the basic method of getting a driver working with ndiswrapper:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
```

The above code actually installs the drive.  My driver happened to be placed in a folder on my desktop - you'd need to change it to wherever you've put your driver.

```
sudo modprobe ndiswrapper
```

The above code starts the module.

```
sudo ndiswrapper -m
```

The above code makes sure that ndiswrapper starts each time you start your computer.


Its a microsoft Wireless PCI adaptor. I have a driver I got from the ndiswrapper wiki so it should work. Thanks a lot for all your help!

---

### Post by WalmartSniperLX on 2006-08-10
patrick@patrick-desktop:~$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.15-26-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory



Now thats odd

---

### Post by Jagot on 2006-08-10
Do this to see if the driver installed correctly before:

```
sudo ndiswrapper -l
```

---

### Post by WalmartSniperLX on 2006-08-10
> **Jagot said:**
> Do this to see if the driver installed correctly before:

```
sudo ndiswrapper -l
```

patrick@patrick-desktop:~$ sudo ndiswrapper -|
>


Thats the output. Is there something i did wrong? Maybe it didnt install correctly, although it said it installed:


[I]patrick@patrick-desktop:~$ sudo ndiswrapper -i ~/Desktop/Wireless/bcmwl5.sys
Installing bcmwl5.sys
patrick@patrick-desktop:~$ sudo modprobe ndiswrapper[/I]

---

### Post by Jagot on 2006-08-10
The file you need should be bcmwl5.inf - not .sys.  Sounds like you have a Broadcom chipset like mine.

---

### Post by WalmartSniperLX on 2006-08-10
> **Jagot said:**
> The file you need should be bcmwl5.inf - not .sys.  Sounds like you have a Broadcome chipset like mine.

Ok. Well the only 2 things i got for the driver were bcmwl5.sys and mn720-ankh.inf . So i should still try the .inf extension on bcmwl5?

---

### Post by Jagot on 2006-08-10
Yep - I'm pretty sure it should be.  Can you run the command lspci so you can tell us exactly what shipset you're using - the specific output you need should be under network controller or something like that.

---

### Post by WalmartSniperLX on 2006-08-10
> **Jagot said:**
> Yep - I'm pretty sure it should be.  Can you run the command lspci so you can tell us exactly what shipset you're using - the specific output you need should be under network controller or something like that.

Network controller: Broadcom Corporation BCM43xG 802.11b/g (rev 02)

---

### Post by Jagot on 2006-08-10
You might want to try the methods here first:

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Ubuntu comes with it's own drivers for Broadcom chipsets.  ndiswrapper is a last resort if you cannot get it working with it's own drivers.

---

### Post by WalmartSniperLX on 2006-08-10
Ok thanks ill follow that then :D

---

### Post by WalmartSniperLX on 2006-08-10
ok to be exactly sure, which of the 2 files was the actual driver?

---

### Post by Jagot on 2006-08-10
> **WalmartSniperLX said:**
> ok to be exactly sure, which of the 2 files was the actual driver?

It should be bcmwl5.inf.

---

### Post by WalmartSniperLX on 2006-08-10
ok thanks. yeah I ran into a problem with that page. 

Told me to input:

*sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o *

and I got:


[I]Cannot open input file /home/patrick/Desktop/wl_apsta.o
[/I] in return

---

### Post by Jagot on 2006-08-10
I'm afraid that I could not get that method to work.  If you get any error messages from it then yo uare better off posting there.  As I say, if you can't get that one working then try ndiswrapper, but post there first.

---

### Post by WalmartSniperLX on 2006-08-10
> **Jagot said:**
> I'm afraid that I could not get that method to work.  If you get any error messages from it then yo uare better off posting there.  As I say, if you can't get that one working then try ndiswrapper, but post there first.

Ok thanks a lot for the help. Btw does ndiswrapper use a lot of cpu cycles when you have it working?

---

### Post by Jagot on 2006-08-10
> **WalmartSniperLX said:**
> Btw does ndiswrapper use a lot of cpu cycles when you have it working?

Nope - no noticeable load.

---

### Post by WalmartSniperLX on 2006-08-10
> **Jagot said:**
> Nope - no noticeable load.

ok thanks

---

### Post by CVpumas61 on 2006-09-15
Walmart, r u using the Microsoft MN-720 pci wireless card by any chance?

---

