---
title: "Admin user"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by KriswithaK on 2007-01-27
I am trying to install automatix, but when I download the installer it says I already have admin tasks open. Is there a command that can show me all programs that are currently running, and if so, what command should I use to close them. (The program using the admin function is not viewable, as I have closed all icons in the system tray except gaim).
Thanks for the support

---

### Post by taurus on 2007-01-27
Applications -> Accessories -> Terminal
```
ps -A
```

p.s.  Post the output here if you don't know which one to kill.

```
sudo kill -9 **PID**
```

---

### Post by KriswithaK on 2007-01-27
kris@kris-basement:~$ ps -a
  PID TTY          TIME CMD
 8492 pts/0    00:00:00 ps

---

### Post by taurus on 2007-01-27
It's capital A.  Linux/Unix is case sensitive so **a** is not the same as **A**.

```
**ps -A**
```

---

### Post by KriswithaK on 2007-01-27
you learn something every day I guess, heres what I got:
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  127 ?        00:00:00 kseriod
  160 ?        00:00:00 pdflush
  161 ?        00:00:00 pdflush
  162 ?        00:00:00 kswapd0
  163 ?        00:00:00 aio/0
 1634 ?        00:00:00 ata/0
 1732 ?        00:00:00 khubd
 1811 ?        00:00:00 kjournald
 1885 ?        00:00:00 logd
 2031 ?        00:00:00 udevd
 2789 ?        00:00:00 kpsmoused
 2797 ?        00:00:00 shpchpd
 3324 ?        00:00:00 dhclient3
 3530 tty1     00:00:00 getty
 3531 tty2     00:00:00 getty
 3532 tty3     00:00:00 getty
 3533 tty4     00:00:00 getty
 3534 tty5     00:00:00 getty
 3535 tty6     00:00:00 getty
 3744 ?        00:00:00 acpid
 3840 ?        00:00:00 syslogd
 3866 ?        00:00:00 dd
 3868 ?        00:00:00 klogd
 3940 ?        00:00:00 gdm
 3941 ?        00:00:00 gdm
 3960 tty7     00:02:08 Xorg
 3978 ?        00:00:00 cupsd
 4013 ?        00:00:00 hpiod
 4016 ?        00:00:00 python
 4064 ?        00:00:00 dbus-daemon
 4079 ?        00:00:01 hald
 4080 ?        00:00:00 hald-runner
 4086 ?        00:00:00 hald-addon-acpi
 4093 ?        00:00:00 hald-addon-keyb
 4106 ?        00:00:00 hald-addon-stor
 4130 ?        00:00:00 perl
 4201 ?        00:00:00 hcid
 4208 ?        00:00:00 sdpd
 4219 ?        00:00:00 krfcommd
 4251 ?        00:00:00 atd
 4268 ?        00:00:00 cron
 7778 ?        00:00:00 x-session-manag
 7813 ?        00:00:00 ssh-agent
 7816 ?        00:00:00 dbus-launch
 7817 ?        00:00:00 dbus-daemon
 7819 ?        00:00:00 gconfd-2
 7822 ?        00:00:00 gnome-keyring-d
 7825 ?        00:00:00 gnome-settings-
 7834 ?        00:00:00 sh
 7835 ?        00:00:00 esd
 7842 ?        00:00:03 metacity
 7847 ?        00:00:02 gnome-panel
 7849 ?        00:00:00 nautilus
 7853 ?        00:00:00 bonobo-activati
 7857 ?        00:00:00 gnome-vfs-daemo
 7860 ?        00:00:00 gnome-volume-ma
 7863 ?        00:00:00 update-notifier
 7865 ?        00:00:00 evolution-alarm
 7871 ?        00:00:00 gnome-cups-icon
 7877 ?        00:00:00 gnome-power-man
 7891 ?        00:00:00 evolution-data-
 7898 ?        00:00:00 evolution-excha
 7907 ?        00:00:00 trashapplet
 7930 ?        00:00:00 mapping-daemon
 7949 ?        00:00:00 mixer_applet2
 7955 ?        00:00:24 firefox-bin
 7979 ?        00:00:00 gnome-screensav
 8023 ?        00:00:07 gaim
 8636 ?        00:00:00 gnome-terminal
 8638 ?        00:00:00 gnome-pty-helpe
 8639 pts/0    00:00:00 bash
 8659 pts/0    00:00:00 ps

---

### Post by taurus on 2007-01-27
```
sudo kill -9 7863
sudo aptitude update
sudo aptitude install automatix2
```

---

### Post by KriswithaK on 2007-01-27
Well, I did that, but after I type the last command I get this:
kris@kris-basement:~$ sudo aptitude install automatix2
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
kris@kris-basement:~$ 

I'm very sorry if this is a stupid mistake, but as I said I just started on linux.

---

### Post by taurus on 2007-01-27
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude install automatix2
```

---

