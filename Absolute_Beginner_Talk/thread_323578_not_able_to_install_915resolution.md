---
title: "not able to install 915resolution"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Korrontean on 2006-12-22
I am installing Ubuntu 6.06 on a Acer Aspire 3500 laptop and I have read I need to install 91 resolution, as the resolution is not the correct one.

However, when I type apt-get install 915 resolution, I get this message:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jon@jon-laptop:~$ sudo apt-get install 915resolution
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


THANK YOU VERY MUCH FOR YOUR HELP!

---

### Post by taurus on 2006-12-22
You have another program, adept or synaptic, running in the background so you can't run both at the same time!  You need to kill that process first.  What's the output of this command from a terminal, Applications -> Accessories -> Terminal, then?

```
ps -A
```

---

### Post by Korrontean on 2006-12-22
I've already closed the other programas, but still apt-get install 915resolution won't work.

The answer to ps -A is the following:

 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
   53 ?        00:00:00 kacpid-work-0
   54 ?        00:00:00 kacpid-work-1
   55 ?        00:00:00 kacpid-work-2
  113 ?        00:00:00 pdflush
  114 ?        00:00:00 pdflush
  116 ?        00:00:00 aio/0
  115 ?        00:00:00 kswapd0
  703 ?        00:00:00 kseriod
 1802 ?        00:00:00 khubd
 1886 ?        00:00:00 kjournald
 2115 ?        00:00:00 udevd
 2874 ?        00:00:00 shpchpd_event
 2994 ?        00:00:00 pccardd
 3765 ?        00:00:00 acpid
 3881 ?        00:00:00 dd
 3883 ?        00:00:00 klogd
 4206 ?        00:00:00 gdm
 4218 ?        00:00:00 gdm
 4240 tty7     00:05:29 Xorg
 4249 ?        00:00:00 hpiod
 4253 ?        00:00:00 python
 4326 ?        00:00:00 dbus-daemon
 4341 ?        00:00:00 hald
 4342 ?        00:00:00 hald-runner
 4347 ?        00:00:00 hald-addon-acpi
 4401 ?        00:00:00 hald-addon-keyb
 4417 ?        00:00:00 hald-addon-stor
 4418 ?        00:00:00 hald-addon-stor
 4499 ?        00:00:00 hcid
 4503 ?        00:00:00 sdpd
 4518 ?        00:00:00 krfcommd
 4531 ?        00:00:00 mdadm
 4566 ?        00:00:00 atd
 4579 ?        00:00:00 cron
 4658 tty1     00:00:00 getty
 4659 tty2     00:00:00 getty
 4660 tty3     00:00:00 getty
 4661 tty4     00:00:00 getty
 4662 tty5     00:00:00 getty
 4663 tty6     00:00:00 getty
 4689 ?        00:00:00 dhclient3
 4702 ?        00:00:00 x-session-manag
 4744 ?        00:00:00 ssh-agent
 4747 ?        00:00:00 dbus-launch
 4748 ?        00:00:00 dbus-daemon
 4750 ?        00:00:00 gconfd-2
 4753 ?        00:00:00 gnome-keyring-d
 4755 ?        00:00:00 bonobo-activati
 4757 ?        00:00:00 gnome-settings-
 4761 ?        00:00:00 esd
 4766 ?        00:00:00 esd
 4771 ?        00:00:03 metacity
 4776 ?        00:00:03 gnome-panel
 4778 ?        00:00:00 nautilus
 4781 ?        00:00:00 gnome-volume-ma
 4787 ?        00:00:00 update-notifier
 4793 ?        00:00:00 gnome-cups-icon
 4798 ?        00:00:00 gnome-vfs-daemo
 4809 ?        00:00:00 gnome-power-man
 4812 ?        00:00:00 trashapplet
 4819 ?        00:00:00 mapping-daemon
 4821 ?        00:00:00 stickynotes_app
 4823 ?        00:00:00 gnome-netstatus
 4825 ?        00:00:00 gweather-applet
 4828 ?        00:00:00 mixer_applet2
 4830 ?        00:00:00 clock-applet
 4845 ?        00:00:00 gnome-screensav
 4849 ?        00:00:00 dhclient3
 4873 ?        00:01:00 firefox-bin
 5086 ?        00:00:00 cupsd
 5357 ?        00:00:00 syslogd
 5437 ?        00:00:01 gnome-terminal
 5439 ?        00:00:00 gnome-pty-helpe
 5440 pts/0    00:00:00 bash
 6272 pts/0    00:00:00 ps


THANK YOU!

---

### Post by taurus on 2006-12-22
Try to kill the update-notifier and see if you can install it again...

```
sudo kill -9 4787
sudo aptitude update
sudo aptitude install 915resolution
```

p.s. You need to enable both universe and multiverse in /etc/apt/sources.list before you can install 915resolution!

---

### Post by Korrontean on 2006-12-22
First two commands apparently worked, but the answer to the third one was:

Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "915resolution"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


How do I enable universe and multiverse???

THANK YOU!

---

### Post by taurus on 2006-12-22
Remove the # sign in front of all the lines with universe & multiverse (at the end) in /etc/apt/sources.list.  Those lines usually start with the "deb" word...

```
gksudo gedit /etc/apt/sources.list
```
Save it and run the last two commands again.

```
sudo aptitude update
sudo aptitude install 915resolution
```

---

### Post by Korrontean on 2006-12-22
PERFECT!

It finally worked. How do I use 915 resolution? (sorry for needing so much help)

I thought that now I'd be able to choose the right resolution in System/Preferences/Screen resolution.

THANKS

---

### Post by macogw on 2006-12-22
```

sudo 915resolution -l
sudo gedit /etc/default/915resolution 
sudo gedit /etc/X11/xorg.conf
sudo /etc/init.d/915resolution start

```
After the first one, read the modes and resolutions listed
After the second, plug in the mode, XRESO, YRESO, and put in how many bits (probably 32) for the resolution you want, save
After the third, put that new resolution at the start of the list of resolutions where the depth is 24, save
After the fourth, hit ctrl+alt+backspace to restart X
That resolution should be an option in your System > Preferences > Resolution now

---

### Post by Korrontean on 2006-12-23
thank you Macogw!!!

it didn't work, though.

I don't know if the error came from the beginning, after the first command, it said:

"Unknown chipset type and unrecognized bios."

and "Chipset Id: 6611039"

The changes in 915resolution were correctly saved (well, I believe the resolution of my screen is 1280x800 even if a google search doesn't leave it completely clear).

When I edited xorg.conf the resolution was not written there in Depth 24, but I added it in the first place, and saved.

Finally, after the last command, the response was:

Starting 915resolution: Panel id read failed.
*** Your 915resolution was not automatically configured! ***
Please read..."

THANK YOU VERY MUCH FOR YOUR SUPPORT! (and sorry for my lack of...ability)

---

