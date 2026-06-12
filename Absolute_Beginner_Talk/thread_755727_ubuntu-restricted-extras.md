---
title: "ubuntu-restricted-extras"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by saurabhgupta on 2008-04-15
The following  ERROR that i get while installing resticted extras:

saurabh@saurabh-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for saurabh:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras


[COLOR="Blue"]
I have a dual boot ie: XP and Ubuntu. I have the internet (it  is of DATA MODEM type)
on XP but not ubuntu.
Also i  can't install the setup file (.exe) on UBUNTU.
some solution would be highly appreciated.
thanx in advance...


BOTTOM LINE IS THAT I DONT HAVE INTERNET ON UBUNTU AND I HOW DO I GO ABOUT FROM 
HERE...
__________________
[/COLOR]

---

### Post by kesman on 2008-04-15
I remember you creating a thread about this yesterday. It's against the forum rules to create multiple threads on the same subject. Please use the existing threads.

---

### Post by zvacet on 2008-04-15
@ **saurabhgupta**

Why don´t you try to set internet connection on Ubuntu first?If you don´t konw how to do it simply ask.

---

### Post by thisismalhotra on 2008-04-15
> **saurabhgupta said:**
> The following  ERROR that i get while installing resticted extras:

saurabh@saurabh-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for saurabh:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras


[COLOR="Blue"]
I have a dual boot ie: XP and Ubuntu. I have the internet (it  is of DATA MODEM type)
on XP but not ubuntu.
Also i  can't install the setup file (.exe) on UBUNTU.
some solution would be highly appreciated.
thanx in advance...


BOTTOM LINE IS THAT I DONT HAVE INTERNET ON UBUNTU AND I HOW DO I GO ABOUT FROM 
HERE...
__________________
[/COLOR]

Issue is you dont have repos enabled, but even if you enable the repositories, you will need and internet connection.

Alternatively you can download Ubuntu repositories on a DVD and use it as your local repos. Goole search for 'Ubuntu repositories on a DVD' and go from there. Also, as mentioned above do not strat another thread for the same topic if you have one already.

---

### Post by chrisdugdale on 2008-04-15
I've been having the same problem. So far, I found out that Ubuntu doesn't install drivers for a dialup modem, so you have to do it yourself. There is a clear and detailed guide for many, if not most modems at [https://help.ubuntu.com/community/DialupModemHowto/ScanModem](https://help.ubuntu.com/community/DialupModemHowto/ScanModem) Sorry, but it does mean a lot of reading and being very careful to do as they say. The ScanModem utility is the trick. It works out what kind of modem you have and tells you how to find software that works to run it. Unfortunately ScanModem output is long, detailed and confusing at first, for me anyway. It is however very clear if you follow the page I mentioned. They say it works for most, but not all modems. Apparantly an external modem is more likely to be easier to get running, but I paid $18 for an internal one rather than $80 for internal. Will be trying to actually follow through and follow the instructions when I have time!

---

### Post by stchman on 2008-04-15
> **saurabhgupta said:**
> The following  ERROR that i get while installing resticted extras:

saurabh@saurabh-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for saurabh:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras


[COLOR="Blue"]
I have a dual boot ie: XP and Ubuntu. I have the internet (it  is of DATA MODEM type)
on XP but not ubuntu.
Also i  can't install the setup file (.exe) on UBUNTU.
some solution would be highly appreciated.
thanx in advance...


BOTTOM LINE IS THAT I DONT HAVE INTERNET ON UBUNTU AND I HOW DO I GO ABOUT FROM 
HERE...
__________________
[/COLOR]

The bottom line is that to effectively use a PC these days an internet connection is a must.

If internet access is not possible you will need to get the packages (with dependencies) from somewhere else and burn them to a CD.

---

