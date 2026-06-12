---
title: "Intell 3945 card into monitor mode"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by mitpat on 2007-05-15
Does anyone how to get the intel 3945 (as in its built in, centrino and all) card into monitor mode. I'm using ubuntu 7.04 and i'm hoping to use something like kismet

---

### Post by Bachstelze on 2007-05-15
The monitor mode is disabled by default in the drivers of the card so you'll have to compile rhem yourself if you want to enable it. No big deal but I've had problems using self-compiled driver for that card in Feisty. I guess it just doesn't like you not doing things "The Ubuntu Way" (TM)...

---

### Post by mitpat on 2007-05-15
do you know someone who could either compile them for me or already has as i'm very new to ubuntu (i only got it yeserday).

---

### Post by chili555 on 2007-05-16
I don't quite agree with my esteemed colleague. Here is my terminal output showing my card and then putting it in monitor mode:```
chili@LAPTOP60:~$ dmesg | grep 3945
[   20.748000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   20.748000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   20.748000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   22.644000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
chili@LAPTOP60:~$ sudo iwconfig eth1 mode monitor
Password:
chili@LAPTOP60:~$ 
```

---

### Post by Bachstelze on 2007-05-16
Oh, then they enabled it in the driver in Ubuntu. When using the vanilla drivers :

```
mfb@ana ~ $ sudo iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.

```

---

### Post by esoterica on 2007-05-16
I have the same exact card, Ubuntu by default installs the restricted drivers for it. Since it's working I've been afraid to mess with it.

Here are the drivers you want though, as well as instructions on how to compile them your self (that part is easy)

[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

What I'm not sure about is in Ubuntu, how do you remove an existing driver to install the new one?

Then if that new one doesn't work, how do you resort back to the working driver?

I really want to do this badly, but I'm afraid since it is working right now and Ubuntu included only the restricted drivers there must have been some reason for them doing so. I hate to break something that is working, I'd hate even more to screw this wireless card up, without it working I'd have no way to get back on the Internet to try and fix it.

---

### Post by Tex-Twil on 2007-07-15
> **esoterica said:**
> 
I really want to do this badly, but I'm afraid since it is working right now and Ubuntu included only the restricted drivers there must have been some reason for them doing so. I hate to break something that is working, I'd hate even more to screw this wireless card up, without it working I'd have no way to get back on the Internet to try and fix it.

I have the same fears :)

---

### Post by 123someone on 2007-07-28
I have the exact same setup and problem as Mitpat -- if there is anyone who can show a nuub a tutorial of either how the edit the makefile so that I can enable monitoring or show me some other step-by-step way to enable my ipw3945 card, I would really applicate it.  Thanks guys.

---

### Post by Papi-KB7VGW on 2007-07-28
So tell me, what if the function/purpose of mode monitor.  As far as I can tell my 3945 is working.

Edit: sorry, I did a search and answered my own ?.  Should have done that in the first place.

---

### Post by 123someone on 2007-07-29
Or if someone could even just explain to me how to get to the make file of the wireless driver I am currently using (the ipw3945 driver Ubuntu 7.04 installs by default)  I could figure it out from there.  Thanks again.

---

### Post by phb5 on 2007-08-05
seems like this card works differently on different machines.
my problem is that the card goes into monitor mode, but stays there only a short period of time (under a minute). then switches itself back to managed mode. this also occures when putting card to ad-hoc mode.
EDIT: i'm using Ubuntu 7.04

can anyone give a reasonable explanation to this?

greets!!! :)

PS! excuse me if my english is bad.... not my native language tho. ;)

---

### Post by Woggles on 2007-08-09
> **phb5 said:**
> seems like this card works differently on different machines.
my problem is that the card goes into monitor mode, but stays there only a short period of time (under a minute). then switches itself back to managed mode. this also occures when putting card to ad-hoc mode.
EDIT: i'm using Ubuntu 7.04

can anyone give a reasonable explanation to this?

greets!!! :)

PS! excuse me if my english is bad.... not my native language tho. ;)



The reason is because of the network manager that is installed with Ubuntu 7.04 by default.  Right-click on the network connection icon, and select 'Enable Wireless' to deselect it.  Now you can put the device in monitor mode and it'll stay.  I'm having trouble getting the network program to sync up though after returning it from monitor mode.  Anybody have any luck?

---

### Post by phb5 on 2007-08-11
Thanks Woggles! :)

by the way i found an alternative solution myself... that automatic switching is caused by roaming... disabling that (manual network configuration) eliminated the problem.

---

### Post by 123someone on 2007-08-13
Got it working -- thanks guys!  :)

---

