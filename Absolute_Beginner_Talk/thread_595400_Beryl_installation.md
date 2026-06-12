---
title: "Beryl installation???"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by omi291 on 2007-10-28
Hi everybody...i'm pretty new to ubuntu, and i have heard a lot of compliments about beryl. I've been having problems installing though. Can anyone help me? This is as far as i got by myself:

dominator@Javaid:~$ sudo -i
root@Javaid:~# cd /usr/local/bin
root@Javaid:/usr/local/bin# wget [http://distfiles.gentoo-xeffects.org/beryl-setup](http://distfiles.gentoo-xeffects.org/beryl-setup)
--18:40:07--  [http://distfiles.gentoo-xeffects.org/beryl-setup](http://distfiles.gentoo-xeffects.org/beryl-setup)
           => `beryl-setup.1'
Resolving distfiles.gentoo-xeffects.org... 69.73.191.2
Connecting to distfiles.gentoo-xeffects.org|69.73.191.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 22,238 (22K) [text/plain]

100%[====================================>] 22,238        --.--K/s             

18:40:07 (965.30 KB/s) - `beryl-setup.1' saved [22238/22238]

root@Javaid:/usr/local/bin# chmod 755 beryl-setup
root@Javaid:/usr/local/bin# beryl-setup --setup
Welcome to the nesl247 Beryl Setup Manager
Today we are going to setup beryl

To begin, I'm going to ask you a few questions

-------------------------------------------
You have chosen to setup beryl with the following options:

Distro: debian
Display Method: 
Video Card: intel
Login Manager(s): 
Desktop Environment(s): gnome

Please review the above information, then press enter to continue setup 
Setting up beryl. This may take a moment...
-------------------------------------------
Preparing to install software...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl
-------------------------------------------
Warning: You must have xserver-xorg-video-i810installed
If you do not have it already, please install it after setup is completed

Your driver in the Device section should be "i810"

Notes:
        None
-------------------------------------------
Enter all the usernames you wish to setup beryl-manager for (space separated): dominator
Warning: If you already have an autostart entry for beryl-manager in Gnome,
please remove it after setup

Creating Gnome autostart entry...
Traceback (most recent call last):
  File "/usr/local/bin/beryl-setup", line 747, in <module>
    setup(advanced)
  File "/usr/local/bin/beryl-setup", line 637, in setup
    os.makedirs("/home/" + x + "/.config/autostart")
  File "/usr/lib/python2.5/os.py", line 172, in makedirs
    mkdir(name, mode)
OSError: [Errno 17] File exists: '/home/dominator/.config/autostart'
root@Javaid:/usr/local/bin#

---

### Post by FuturePilot on 2007-10-28
Ubuntu 7.10 comes with Compiz Fusion which is the result of the Beryl-Compiz merger. Beryl is a dead project now. What graphics card do you have? Once you get the correct driver setup, Compiz Fusion will automatically be enabled.

---

