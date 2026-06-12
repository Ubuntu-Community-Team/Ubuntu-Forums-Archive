---
title: "Simple command help- what am I typing wrong here?"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by SunshineSmile on 2006-11-17
Hi guys. This should be really simple. I am just following the recipe stated in [this D-link WLAN thread]("http://www.ubuntuforums.org/showthread.php?t=106328")

Ahem.. we're at my Desktop. I have the file: rt2570-1.1.0-b2.tar.gz and now I am gonna follow the few steps in that thread above 100%

gunzip rt2570-1.1.0-b2.tar.gz
tar -xvf rt2570-1.1.0-b2.tar
cd rt2570-1.1.0-b2
make
# the fun begins:
**no targets specified and no makefile found**
cd module
make
make[1]Entering directory `/lib/modules/2.6.12-9-986/build'
make[1]***no rule to make target 'modules'. Stop.
make[1]Leaving directorz '/lib/modules/2.6.12-9-986/build
rt2570.ko failed to build!!
make:***[module] Error1

what the ****
bash: what: command not found

How come MY comp won't *make*, while the PC in Reggie's thread is doing fine? This just ain't fair. I want my WLAN to work :evil: Somebody heelp!!:neutral:

---

### Post by Zeerak on 2006-11-17
sudo aptitude install build-essentials

that install assumes you've gotten that file.

---

### Post by SunshineSmile on 2006-11-17
Thanks. I'll try that out immediately. 

Say, is there a method of installing build-essentials by downloading the packages to an external drive and installing them manually? 

I want to get wlan usb up and running on a laptop with no ethernet access, that's why I am asking.

---

### Post by SunshineSmile on 2006-11-17
No, it doesn't work. I had already installed build-essential. It still displays "No rule to make target "modules" , when I type "make"

](*,)

---

### Post by taurus on 2006-11-17
What if you try this command first?

```
./configure
make

```

---

### Post by SunshineSmile on 2006-11-17
in what directory do I type that command? It only gives me bash: ./configure: No such file or directory

---

### Post by taurus on 2006-11-17
Okay, while you are still in "rt2570-1.1.0-b2", what is the output of this command then?

```
ls -la
```

---

### Post by SunshineSmile on 2006-11-17
Ok, the list with -la gives me the following:

flux@ubuntu:~/Desktop/rt2570-1.1.0-b2/Module$ ls -la
total 1236
drwxr-xr-x  2 flux flux   4096 2006-06-17 22:08 .
drwxr-xr-x  3 flux flux   4096 2006-06-17 22:08 ..
-rw-r--r--  1 flux flux  36798 2006-06-17 22:08 assoc.c
-rw-r--r--  1 flux flux  16833 2006-06-17 22:08 auth.c
-rw-r--r--  1 flux flux   5993 2006-06-17 22:08 auth_rsp.c
-rw-r--r--  1 flux flux  50131 2006-06-17 22:08 connect.c
-rw-r--r--  1 flux flux   2040 2006-06-17 22:08 iwpriv_usage.txt
-rw-r--r--  1 flux flux   5728 2006-06-17 22:08 Makefile
-rw-r--r--  1 flux flux  44082 2006-06-17 22:08 md5.c
-rw-r--r--  1 flux flux   3369 2006-06-17 22:08 md5.h
-rw-r--r--  1 flux flux 147321 2006-06-17 22:08 mlme.c
-rw-r--r--  1 flux flux  18979 2006-06-17 22:08 mlme.h
-rw-r--r--  1 flux flux  30265 2006-06-17 22:08 oid.h
-rw-r--r--  1 flux flux  30704 2006-06-17 22:08 rt2570.h
-rw-r--r--  1 flux flux 101364 2006-06-17 22:08 rt2570sw.h
-rw-r--r--  1 flux flux   5934 2006-06-17 22:08 rt_config.h
-rw-r--r--  1 flux flux   4089 2006-06-17 22:08 rtmp_ckipmic.h
-rw-r--r--  1 flux flux  22712 2006-06-17 22:08 rtmp_def.h
-rw-r--r--  1 flux flux  31002 2006-06-17 22:08 rtmp_tkip.c
-rw-r--r--  1 flux flux   5018 2006-06-17 22:08 rtmp_type.h
-rw-r--r--  1 flux flux  12816 2006-06-17 22:08 rtmp_wep.c
-rw-r--r--  1 flux flux  40026 2006-06-17 22:08 rtusb_bulk.c
-rw-r--r--  1 flux flux 101282 2006-06-17 22:08 rtusb_data.c
-rw-r--r--  1 flux flux   9497 2006-06-17 22:08 rtusb.h
-rw-r--r--  1 flux flux 144344 2006-06-17 22:08 rtusb_info.c
-rw-r--r--  1 flux flux  67730 2006-06-17 22:08 rtusb_init.c
-rw-r--r--  1 flux flux  19665 2006-06-17 22:08 rtusb_io.c
-rw-r--r--  1 flux flux  57603 2006-06-17 22:08 rtusb_main.c
-rw-r--r--  1 flux flux  27890 2006-06-17 22:08 sanity.c
-rw-r--r--  1 flux flux   2624 2006-06-17 22:08 sha1.h
-rw-r--r--  1 flux flux  68683 2006-06-17 22:08 sync.c
-rw-r--r--  1 flux flux   1920 2006-06-17 22:08 TESTING
-rw-r--r--  1 flux flux  44447 2006-06-17 22:08 wpa.c
-rw-r--r--  1 flux flux   5363 2006-06-17 22:08 wpa.h

flux@ubuntu:~/Desktop/rt2570-1.1.0-b2/Module$ cd ..


flux@ubuntu:~/Desktop/rt2570-1.1.0-b2$ ls -la
total 48
drwxr-xr-x  3 flux flux  4096 2006-06-17 22:08 .
drwxr-xr-x  3 flux flux  4096 2006-11-17 23:02 ..
-rw-r--r--  1 flux flux  2569 2006-06-17 22:08 CHANGELOG
-rw-r--r--  1 flux flux   105 2006-06-17 22:08 FAQ
-rw-r--r--  1 flux flux 18371 2006-06-17 22:08 LICENSE
drwxr-xr-x  2 flux flux  4096 2006-06-17 22:08 Module
-rw-r--r--  1 flux flux  1539 2006-06-17 22:08 README
-rw-r--r--  1 flux flux   823 2006-06-17 22:08 THANKS


Well, there is a .makefile in there, but typing *make* doesn't help me. Are there any other programs I might be missing?

What does this ***No rule to make target 'modules.' Stop. mean really?

---

### Post by taurus on 2006-11-17
What does the README say anyway?

```
more README
```

---

### Post by SunshineSmile on 2006-11-17
This is the README file:

Installation instructions for the rt2570 Module

=======================================================================
Build Instructions:
====================
	For 2.4 or 2.6 series kernel:

	a. $tar -xvzf rt2570-x.x.x.tar.gz
	go to "./rt2570-x.x.x/Module" directory.

	b. $make # compile driver source code

	c. $make install # installs kernel module driver

	d. $modprobe rt2570

=======================================================================
UTILITY
====================
	There is no utility as of yet, use iwconfig to configure your usb stick.

=======================================================================
CONFIGURATION:
====================
	RT2570 driver can be configured via following interfaces,
	i.e. (i)"iwconfig" command, (ii)"iwpriv" command

	i) iwconfig comes with kernel.
	ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.

MORE INFORMATION
=================================================================================
	If you want for rt2570 driver to auto-load at boot time:

	A) choose rausb0 for first RT2570 WLAN card, rausb1 for second RT2570 WLAN card, etc.

	B) create(edit) 'ifcfg-rausb0' file in /etc/sysconfig/network-scripts/,
	edit( or add the line) in /etc/modules.conf:
	alias rausb0 rt2570

	C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-rausb0
	DEVICE='rausb0'
	ONBOOT='yes'


	NOTE:
	if you use dhcp, add this line too .
	BOOTPROTO='dhcp'

	*D) To ease the Default Gateway setting,
	add the line
	GATEWAY=x.x.x.x
	in /etc/sysconfig/network

---

### Post by taurus on 2006-11-17
It looks to me like you need to install a kernel header for your kernel before you can build a module for your wireless card!!!

---

### Post by CatKiller on 2006-11-18
> **SunshineSmile said:**
> Say, is there a method of installing build-essentials by downloading the packages to an external drive and installing them manually? 

I want to get wlan usb up and running on a laptop with no ethernet access, that's why I am asking.

**build-essential** should be on the install cd.

---

### Post by taurus on 2006-11-18
If you need to install build-essential, insert the CD that you used to install Ubuntu into the drive and at the prompt (from a terminal), type

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by CatKiller on 2006-11-18
Does the cd not automatically get added as a repository for the install? I'm sure mine did, although that was a while ago now, relative to my memory.

---

### Post by SunshineSmile on 2006-11-18
Ok, thanks for the feedback.. It is a great sunshiny day (unfortunately not) and I will now embark on a quest to find out what a kernel header is, which one I need, and how to install it. Thanks for the tips!!

---

### Post by argie on 2006-11-18
That would be the package "linux-headers" with the same version as you get from <code>uname -r</code>

---

### Post by SunshineSmile on 2006-11-18
> **argie said:**
> That would be the package "linux-headers" with the same version as you get from <code>uname -r</code>

Uname -r
2.6.12-9-386

flux@ubuntu:~$ sudo apt-get install linux-headers-2.6.12-9-386
Password:
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  linux-headers-2.6.12-9-386

Yay! :mrgreen: Then let's try again:

flux@ubuntu:~/Desktop/rt2570-1.1.0-b2$ ls
CHANGELOG  FAQ  LICENSE  Module  README  THANKS

flux@ubuntu:~/Desktop/rt2570-1.1.0-b2$ cd Module

flux@ubuntu:~/Desktop/rt2570-1.1.0-b2/Module$ make

make[1]: Entering directory `/lib/modules/2.6.12-9-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-9-386/build'
rt2570.ko failed to build!
make: *** [module] Error 1


It still doesn't work... :-k 

Should I look for another kernel-header? Another kernel? I am on breezy. And I am stuck.

Oh, perhaps this could help you, help me:

usr/lib/modules:
2.6.12-9-386
2.6-12-9-686-smp

usr/src
linux-headers-2.6.12-9
linux-headers-2.6.12-9-686-smp

I have an intel celeron processor

---

### Post by taurus on 2006-11-18
If you can backup your personal files, I would recommend you either upgrade to Dapper or install Dapper (or even Edgy).  It is getting better in detecting your wireless card than Breezy...

---

### Post by ArtechnikA on 2006-11-18
> **Zeerak said:**
> sudo aptitude install build-essentials


for completeness (since I just tried this...) that should be "build-essential".  No 's'.

---

### Post by anaconda on 2006-11-18
did you type the ./configure before you typed make?

Usually it goes like this:

./configure
make

(both done in the same directory)

---

### Post by argie on 2006-11-18
I downloaded the the linux-headers for 2.6.12-9-386 and this driver package. It compiled perfectly with a little modification (I'm not currently on 2.6.12-9-386) to the Makefile.

Do you have a /lib/modules/2.6.12-9-386/ subdirectory have a subdirectory "build" or a link "build" to another subdirectory?

EDIT: Apparently you do. Did you modify the Makefile in any way? I can't think of anything, since it seems to work fine for me.

---

### Post by DirtDawg on 2006-12-12
I am having this exact same problem with the exact same package (rt2570-1.1.0-b). I get the error:
```
make
make[1]: Entering directory `/lib/modules/2.6.15-27-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.15-27-386/build'
rt2570.ko failed to build!
make: *** [module] Error 1

```

I have build-essential, I have the correct linux headers, I have tried './configure', and I have not altered the make file. 

Any ideas about what is wrong would be welcome. I am losing my patience with wireless issues.

---

