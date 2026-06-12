---
title: "error trying to install fvwm-crystal"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Papillonrus on 2007-01-30
Why am I getting this error when I enter the command "startx" ?


root@daryl-laptop:~/fvwm-crystal-3.0.4# startx
xauth:  creating new authority file /root/.serverauth.5069

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

root@daryl-laptop:~/fvwm-crystal-3.0.4# 

Give me a hint, please.  Thanks, Darrell

---

### Post by taurus on 2007-01-30
You log in as root, **root@daryl-laptop:~/fvwm-crystal-3.0.4#**?

The error message said that X is already running and you can't start another session.  How did you log into root anyway?  What happens when you press <Alt>F7?  Do you see a GUI login screen?

---

### Post by Papillonrus on 2007-01-30
on the desktop <alt> F7 does nothing.  I installed thru the terminal as sudo -i this is the last hurdle.  Thanks, Darrell

---

### Post by taurus on 2007-01-30
So your machine boots directly into a console!  Why don't you log in with your username and password.  Then, see if X runs with 

```
startx
```
And if you still get the same error message, paste the output of this command here.

```
ps -A
```

---

### Post by Papillonrus on 2007-01-30
root@daryl-laptop:~# ps -A
  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
   84 ?        00:00:00 kseriod
  115 ?        00:00:00 pdflush
  116 ?        00:00:00 pdflush
  117 ?        00:00:00 kswapd0
  118 ?        00:00:00 aio/0
 1682 ?        00:00:00 khubd
 1732 ?        00:00:00 kjournald
 1805 ?        00:00:00 logd
 1951 ?        00:00:00 udevd
 2653 ?        00:00:00 shpchpd
 2671 ?        00:00:00 pccardd
 2723 ?        00:00:00 kpsmoused
 3177 ?        00:00:00 dhclient3
 3414 tty1     00:00:00 getty
 3415 tty2     00:00:00 getty
 3416 tty3     00:00:00 getty
 3417 tty4     00:00:00 getty
 3418 tty5     00:00:00 getty
 3419 tty6     00:00:00 getty
 3648 ?        00:00:00 acpid
 3744 ?        00:00:00 syslogd
 3770 ?        00:00:00 dd
 3772 ?        00:00:00 klogd
 3845 ?        00:00:00 gdm
 3846 ?        00:00:00 gdm
 3865 tty7     00:00:45 Xorg
 3883 ?        00:00:00 cupsd
 3900 ?        00:00:00 hpiod
 3905 ?        00:00:00 python
 3953 ?        00:00:00 dbus-daemon
 3968 ?        00:00:05 hald
 3969 ?        00:00:00 hald-runner
 3975 ?        00:00:00 hald-addon-acpi
 3986 ?        00:00:00 hald-addon-keyb
 4000 ?        00:00:00 hald-addon-stor
 4018 ?        00:00:00 perl
 4114 ?        00:00:00 hcid
 4121 ?        00:00:00 sdpd
 4132 ?        00:00:00 krfcommd
 4173 ?        00:00:00 atd
 4186 ?        00:00:00 cron
 4302 ?        00:00:01 x-session-manag
 4355 ?        00:00:00 ssh-agent
 4358 ?        00:00:00 dbus-launch
 4359 ?        00:00:00 dbus-daemon
 4361 ?        00:00:01 gconfd-2
 4364 ?        00:00:00 gnome-keyring-d
 4367 ?        00:00:00 gnome-settings-
 4376 ?        00:00:00 sh
 4377 ?        00:00:00 esd
 4382 ?        00:00:04 metacity
 4387 ?        00:00:05 gnome-panel
 4389 ?        00:00:02 nautilus
 4393 ?        00:00:00 bonobo-activati
 4397 ?        00:00:00 gnome-vfs-daemo
 4398 ?        00:00:00 gnome-volume-ma
 4406 ?        00:00:01 update-notifier
 4410 ?        00:00:00 evolution-alarm
 4415 ?        00:00:00 gnome-cups-icon
 4419 ?        00:00:00 gnome-power-man
 4442 ?        00:00:00 trashapplet
 4458 ?        00:00:00 mapping-daemon
 4477 ?        00:00:01 mixer_applet2
 4485 ?        00:00:00 gnome-netstatus
 4493 ?        00:00:00 gnome-screensav
 5415 ?        00:00:15 firefox-bin
 5488 ?        00:00:01 gnome-terminal
 5492 ?        00:00:00 gnome-pty-helpe
 5493 pts/0    00:00:00 bash
 5520 pts/0    00:00:00 bash
 5579 pts/0    00:00:00 ps
root@daryl-laptop:~# 

Here is the post.  I have installed Edgy 6.10

---

### Post by taurus on 2007-01-30
You already logged in to Gnome.  So why do you want to run "**startx**" again?  If you need to open a GUI as root, use 

Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by Papillonrus on 2007-01-30
i am tring to install fvwm-crystal-3.0.4  Guess I will have to start over. Thanks

---

