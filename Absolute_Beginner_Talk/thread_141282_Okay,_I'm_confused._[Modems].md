---
title: "Okay, I'm confused. [Modems]"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by Cloudy on 2006-03-08
> 
#

Since udev rewrites /dev on each boot, and some dialup programs rely on the existence of /dev/modem, you need to have a symlink created on boot (from /dev/ttyLTM0 to /dev/modem). To do this, create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:

  #ltmodem 
  KERNEL="ttyLTM0", SYMLINK="modem"

#

Now load the drivers for the first time:

  $ sudo modprobe lt_serial
  $ sudo modprobe lt_modem



Okay, so.. 
I'm confused, now. How do I create the 10-local.rules file? Through the terminal? How? ._.; :confused:

---

### Post by Jason_25 on 2006-03-08
In that situation I think you would just type
```

sudo nano /etc/udev/rules.d/10-local.rules

```
and nano will pop up waiting for you to copy/paste those lines.  Then ctrl-o, and enter will save.  Then ctrl-z to quit.

---

### Post by Cloudy on 2006-03-08
Thank you. :D

---

### Post by Cloudy on 2006-03-10
Okay.. I'm having more problems.
So, I know what modem I have. 56k Lucent WinModem, PCI slot.
So, going off the directions on the DialUpHowTo section in the wiki:

> 
 Now load the drivers for the first time:

  $ sudo modprobe lt_serial
  $ sudo modprobe lt_modem


I get "FATAL: Module not found". Now, I know it has the solution right there in quotes beneath that part about loading the drivers on the wiki. I tried that. I added the "pci=routeirq" part to /boot/grub/menu.lst and updated the GRUB.

However, I still get "FATAL: Module not found" when I try to sudo modprobe and load lt_serial and lt_modem.

I'm not sure what I'm doing wrong. D: Help?

---

### Post by montablac on 2006-03-10
why not track down the company that made it and and see if they have linux drivers in a .deb or .rpm package

or you could look in the repostorys

or just buy a linmodem...

---

### Post by StefanoCole on 2006-03-10
Cloudy, maybe this thread can help you: [http://www.ubuntuforums.org/showthread.php?t=93852&highlight=ltmodem]("http://www.ubuntuforums.org/showthread.php?t=93852&highlight=ltmodem")

Stefano

---

### Post by Cloudy on 2006-03-12
[QUOTE=StefanoCole]Cloudy, maybe this thread can help you: [http://www.ubuntuforums.org/showthread.php?t=93852&highlight=ltmodem]("http://www.ubuntuforums.org/showthread.php?t=93852&highlight=ltmodem")

Stefano[/QUOTE]

Thank you, Stefano, but I'm still having problems. 

Whenever I get to:
```

download
http://archive.ubuntu.com/ubuntu/poo...untu8_i386.deb
http://archive.ubuntu.com/ubuntu/poo...untu8_i386.deb
http://archive.ubuntu.com/ubuntu/poo...untu8_i386.deb

install them:
dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb

```

Particularly, installing them is giving me troubles. I downloaded all three and they're on my desktop, but whenever I go to install them I get an error about invalid directories (I will copy and paste it/edit it into this post here in a bit.)

---

### Post by Cloudy on 2006-03-12
Okay, this is what happens when I try to install those three .deb packages:

```

travis@ubuntu:~$ sudo dpkg -i cpp-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4_3.4.4-6ubuntu8_i386.deb gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
Password:
dpkg: error processing cpp-3.4_3.4.4-6ubuntu8_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing gcc-3.4_3.4.4-6ubuntu8_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing gcc-3.4-base_3.4.4-6ubuntu8_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cpp-3.4_3.4.4-6ubuntu8_i386.deb
 gcc-3.4_3.4.4-6ubuntu8_i386.deb
 gcc-3.4-base_3.4.4-6ubuntu8_i386.deb
travis@ubuntu:~$

```

All three packages are on my desktop, should they be somewhere else on my system.. ? @_@

---

### Post by towsonu2003 on 2006-03-12
do
cd Desktop
than do that dpkg command again. it cant find the files bc its looking for them in the wrong place

---

### Post by Cloudy on 2006-03-12
Thanks. :D

---

### Post by towsonu2003 on 2006-03-12
your most welcome :) any chance you could fix the wiki page parts that got you screwed? would be helpful for others... do the changes and we'll clean up :)

---

### Post by Cloudy on 2006-03-12
[QUOTE=towsonu2003]your most welcome :) any chance you could fix the wiki page parts that got you screwed? would be helpful for others... do the changes and we'll clean up :)[/QUOTE]

Actually, I was going off of:
[http://www.ubuntuforums.org/showthread.php?t=93852&highlight=ltmodem](http://www.ubuntuforums.org/showthread.php?t=93852&highlight=ltmodem)


What Stefano linked to. Which I don't believe is on the wiki. :o

---

### Post by Cloudy on 2006-03-12
Okay.. I'm having more problems. >___< I've got to be getting annoying by now. :-# 
```
travis@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.
travis@ubuntu:~$
```

However, when I sudo nano /etc/wvdial.conf, this is what comes up:
```

[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
: Phone = 5015565758
: Username = llholden1
: Password = blahblah etc. etc.
Stupid mode = on
```

So the [Dialer Defaults] section *does* exist in wvdial.conf, and there is a valid phone #, username, & password. Also, if I attempt to connect via Networking or pppconfig, it sounds as though it's dialing, but I'm never sure if it was successful or not..? That's a somewhat confusing way to put it, I suppose, but it starts to dial and then whenever I open Gaim or Firefox it starts to dial *again* for extended periods of time. I'm a bit miffed..

..and after rebooting it also dials up when starting network interfaces (because I used pppconfig?, I think) and it dials up while loading the desktop too.

-_o; awesome...

---

### Post by towsonu2003 on 2006-03-13
[QUOTE=Cloudy]Okay.. I'm having more problems. >___< I've got to be getting annoying by now. :-# 
[/quote]
nope, that's the winmodem getting annoying not you :) no worries, everyone had his/her share of winmodem problems... 
[QUOTE=Cloudy]
```
travis@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.54.0
--> Warning: section [Dialer Defaults] does not exist in wvdial.conf.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
[b]--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.[/b]
travis@ubuntu:~$
```

However, when I sudo nano /etc/wvdial.conf, this is what comes up:
```

[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
: Phone = 5015565758
: Username = xxxxxxxx
: Password = blahblah etc. etc.
Stupid mode = on
```

So the [Dialer Defaults] section *does* exist in wvdial.conf, and there is a valid phone #, username, & password. 
[/quote]
Edit that file (sudo nano /etc/vwdial.conf) so that this part: 
```

**:** Phone = 5015565758
**:** Username = xxxxxxxx 
**:** Password = blahblah etc. etc.

```
looks rather like this: 
```

Phone = 5015565758
Username = xxxxxxxx
Password = blahblah etc. etc.

```
it will ignore stuff starting with : so it doesn't see your info in there... 
[QUOTE=Cloudy]Also, if I attempt to connect via Networking or pppconfig, it sounds as though it's dialing, but I'm never sure if it was successful or not..? That's a somewhat confusing way to put it, I suppose, but it starts to dial and then whenever I open Gaim or Firefox it starts to dial *again* for extended periods of time. I'm a bit miffed..

..and after rebooting it also dials up when starting network interfaces (because I used pppconfig?, I think) and it dials up while loading the desktop too.
[/QUOTE]
I'm not sure how to fix pppconfig. try going to networking>modem and deactivate it. hopefully that will shut the thing up.

---

### Post by Cloudy on 2006-03-13
Thanks, I'll do that when I get home. :D

---

### Post by montablac on 2006-03-13
you can also add a modem monotor to the panel in gnome,that works and is easer to set up for new linux users

---

### Post by Cloudy on 2006-03-14
[QUOTE=montablac]you can also add a modem monotor to the panel in gnome,that works and is easer to set up for new linux users[/QUOTE]

Alright, I'll have to look up how to do that. Thanks. :D

---

### Post by Cloudy on 2006-03-15
Again, thank you so much towsonu2003. :D 
I deactivated the interface through Networking and rebooted, then used Pon in the terminal to get online - and it worked, without flaw! :D

*SQUEE*

---

