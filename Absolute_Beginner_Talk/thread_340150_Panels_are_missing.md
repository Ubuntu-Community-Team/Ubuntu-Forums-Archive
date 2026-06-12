---
title: "Panels are missing"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by molex on 2007-01-16
After installing kiba-dock I rebooted and now my panels on the top and bottom of the screen are gone!

How do I get them back?

---

### Post by taurus on 2007-01-16
```
gnome-panel &
```

---

### Post by molex on 2007-01-16
"I have detected a panel already running and will now exit"

I don't see my panels still!

How can I see a list of running apps and maybe restart the panels

---

### Post by taurus on 2007-01-16
Maybe kiba-dock screws up your gnome-panel!  What's the output of this command from a terminal?

```
ps -A
```

Did you happen to start kiba-dock or add it to your Sessions?

---

### Post by molex on 2007-01-16
I added it my session start up

---

### Post by molex on 2007-01-16
molex@BlackMonster:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
   10 ?        00:00:00 kacpi_notify
  108 ?        00:00:00 kseriod
  144 ?        00:00:00 pdflush
  145 ?        00:00:00 pdflush
  146 ?        00:00:00 kswapd0
  147 ?        00:00:00 aio/0
 1601 ?        00:00:00 ata/0
 1602 ?        00:00:00 scsi_eh_0
 1607 ?        00:00:00 scsi_eh_1
 1682 ?        00:00:00 khubd
 1698 ?        00:00:00 khpsbpkt
 1727 ?        00:00:00 knodemgrd_0
 1744 ?        00:00:00 scsi_eh_2
 1745 ?        00:00:00 usb-storage
 1803 ?        00:00:00 kjournald
 1887 ?        00:00:00 logd
 2035 ?        00:00:00 udevd
 2790 ?        00:00:00 kpsmoused
 2820 ?        00:00:00 shpchpd
 3441 tty1     00:00:00 getty
 3442 tty2     00:00:00 getty
 3443 tty3     00:00:00 getty
 3444 tty4     00:00:00 getty
 3445 tty5     00:00:00 getty
 3446 tty6     00:00:00 getty
 3640 ?        00:00:00 acpid
 3723 ?        00:00:00 syslogd
 3749 ?        00:00:00 dd
 3751 ?        00:00:00 klogd
 3823 ?        00:00:00 gdm
 3824 ?        00:00:00 gdm
 3848 tty7     00:00:06 Xorg
 3857 ?        00:00:00 cupsd
 3878 ?        00:00:00 hpiod
 3881 ?        00:00:00 python
 3938 ?        00:00:00 dhclient3
 3948 ?        00:00:00 dbus-daemon
 3967 ?        00:00:01 hald
 3968 ?        00:00:00 hald-runner
 3974 ?        00:00:00 hald-addon-acpi
 3982 ?        00:00:00 hald-addon-keyb
 3995 ?        00:00:00 hald-addon-stor
 4028 ?        00:00:00 perl
 4100 ?        00:00:00 hcid
 4106 ?        00:00:00 sdpd
 4115 ?        00:00:00 krfcommd
 4147 ?        00:00:00 atd
 4160 ?        00:00:00 cron
 4247 ?        00:00:00 gnome-session
 4283 ?        00:00:00 ssh-agent
 4286 ?        00:00:00 dbus-launch
 4287 ?        00:00:00 dbus-daemon
 4289 ?        00:00:00 gconfd-2
 4292 ?        00:00:00 gnome-keyring-d
 4295 ?        00:00:00 gnome-settings-
 4305 ?        00:00:00 sh
 4306 ?        00:00:00 esd
 4318 ?        00:00:01 gnome-panel
 4320 ?        00:00:01 nautilus
 4324 ?        00:00:00 bonobo-activati
 4326 ?        00:00:00 gnome-volume-ma
 4332 ?        00:00:00 gnome-vfs-daemo
 4345 ?        00:00:00 update-notifier
 4348 ?        00:00:00 beryl-manager
 4357 ?        00:00:00 kiba-dock
 4365 ?        00:00:00 evolution-alarm
 4390 ?        00:00:00 gnome-cups-icon
 4422 ?        00:00:00 gnome-power-man
 4490 ?        00:00:01 metacity
 4491 ?        00:00:00 emerald
 4497 ?        00:00:00 mapping-daemon
 4502 ?        00:00:00 evolution-data-
 4515 ?        00:00:00 evolution-excha
 4534 ?        00:00:00 mixer_applet2
 4549 ?        00:00:00 gnome-terminal
 4551 ?        00:00:00 gnome-pty-helpe
 4557 pts/1    00:00:00 bash
 4590 pts/1    00:00:11 firefox-bin
 4600 ?        00:00:00 gnome-screensav
 4612 pts/1    00:00:00 netstat <defunct>
 4636 pts/0    00:00:00 bash
 4654 pts/0    00:00:00 ps

---

### Post by taurus on 2007-01-16
```
sudo kill -9 4357
```

---

### Post by molex on 2007-01-16
Nope, didn't fix it

Perhaps the panels are just outside of my desktop area and need to be cascaded or something?

Any further suggestions?

---

### Post by molex on 2007-01-16
Can I start ubuntu in like a safe mode or w/ a default startup programs?

How?

---

### Post by taurus on 2007-01-16
```
sudo kill -9 4318
gnome-panel &
```

---

### Post by molex on 2007-01-16
I swear I am doing that, but the panels are not reappearing and it says "The panel is already open. I will now exit"

AHHH!

---

### Post by taurus on 2007-01-16
```
ps -A
```

---

### Post by molex on 2007-01-16
PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
   10 ?        00:00:00 kacpi_notify
  108 ?        00:00:00 kseriod
  144 ?        00:00:00 pdflush
  145 ?        00:00:00 pdflush
  146 ?        00:00:00 kswapd0
  147 ?        00:00:00 aio/0
 1601 ?        00:00:00 ata/0
 1602 ?        00:00:00 scsi_eh_0
 1607 ?        00:00:00 scsi_eh_1
 1682 ?        00:00:00 khubd
 1698 ?        00:00:00 khpsbpkt
 1727 ?        00:00:00 knodemgrd_0
 1744 ?        00:00:00 scsi_eh_2
 1745 ?        00:00:00 usb-storage
 1793 ?        00:00:00 kjournald
 1877 ?        00:00:00 logd
 2025 ?        00:00:00 udevd
 2777 ?        00:00:00 kpsmoused
 2815 ?        00:00:00 shpchpd
 3426 tty1     00:00:00 getty
 3427 tty2     00:00:00 getty
 3428 tty3     00:00:00 getty
 3429 tty4     00:00:00 getty
 3430 tty5     00:00:00 getty
 3431 tty6     00:00:00 getty
 3625 ?        00:00:00 acpid
 3708 ?        00:00:00 syslogd
 3734 ?        00:00:00 dd
 3736 ?        00:00:00 klogd
 3765 ?        00:00:00 dhclient3
 3835 ?        00:00:00 gdm
 3836 ?        00:00:00 gdm
 3860 tty7     00:00:09 Xorg
 3869 ?        00:00:00 cupsd
 3890 ?        00:00:00 hpiod
 3893 ?        00:00:00 python
 3939 ?        00:00:00 dbus-daemon
 3954 ?        00:00:01 hald
 3955 ?        00:00:00 hald-runner
 3961 ?        00:00:00 hald-addon-acpi
 3969 ?        00:00:00 hald-addon-keyb
 3982 ?        00:00:00 hald-addon-stor
 4015 ?        00:00:00 perl
 4087 ?        00:00:00 hcid
 4093 ?        00:00:00 sdpd
 4102 ?        00:00:00 krfcommd
 4134 ?        00:00:00 atd
 4147 ?        00:00:00 cron
 4234 ?        00:00:00 gnome-session
 4270 ?        00:00:00 ssh-agent
 4273 ?        00:00:00 dbus-launch
 4274 ?        00:00:00 dbus-daemon
 4276 ?        00:00:00 gconfd-2
 4279 ?        00:00:00 gnome-keyring-d
 4282 ?        00:00:00 gnome-settings-
 4292 ?        00:00:00 sh
 4293 ?        00:00:00 esd
 4305 ?        00:00:01 gnome-panel
 4307 ?        00:00:00 nautilus
 4311 ?        00:00:00 bonobo-activati
 4313 ?        00:00:00 gnome-volume-ma
 4319 ?        00:00:00 gnome-vfs-daemo
 4324 ?        00:00:00 update-notifier
 4335 ?        00:00:00 beryl-manager
 4348 ?        00:00:00 evolution-alarm
 4407 ?        00:00:00 gnome-power-man
 4475 ?        00:00:00 emerald
 4481 ?        00:00:01 metacity
 4487 ?        00:00:00 mapping-daemon
 4490 ?        00:00:00 evolution-data-
 4503 ?        00:00:00 evolution-excha
 4531 ?        00:00:00 mixer_applet2
 4536 ?        00:00:27 firefox-bin
 4551 ?        00:00:00 netstat <defunct>
 4568 ?        00:00:00 gnome-screensav
 4582 ?        00:00:00 gnome-terminal
 4584 ?        00:00:00 gnome-pty-helpe
 4585 pts/0    00:00:00 bash
 4616 ?        00:00:00 gnome-cups-icon
 4636 pts/0    00:00:00 ps

---

### Post by molex on 2007-01-16
Sorry, the message is "I have detected a panel already running and will now exit"

---

### Post by taurus on 2007-01-16
```
sudo kill -9 4305 
ps -A
```

---

### Post by molex on 2007-01-16
PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
   10 ?        00:00:00 kacpi_notify
  108 ?        00:00:00 kseriod
  144 ?        00:00:00 pdflush
  145 ?        00:00:00 pdflush
  146 ?        00:00:00 kswapd0
  147 ?        00:00:00 aio/0
 1601 ?        00:00:00 ata/0
 1602 ?        00:00:00 scsi_eh_0
 1607 ?        00:00:00 scsi_eh_1
 1682 ?        00:00:00 khubd
 1698 ?        00:00:00 khpsbpkt
 1727 ?        00:00:00 knodemgrd_0
 1744 ?        00:00:00 scsi_eh_2
 1745 ?        00:00:00 usb-storage
 1793 ?        00:00:00 kjournald
 1877 ?        00:00:00 logd
 2025 ?        00:00:00 udevd
 2777 ?        00:00:00 kpsmoused
 2815 ?        00:00:00 shpchpd
 3426 tty1     00:00:00 getty
 3427 tty2     00:00:00 getty
 3428 tty3     00:00:00 getty
 3429 tty4     00:00:00 getty
 3430 tty5     00:00:00 getty
 3431 tty6     00:00:00 getty
 3625 ?        00:00:00 acpid
 3708 ?        00:00:00 syslogd
 3734 ?        00:00:00 dd
 3736 ?        00:00:00 klogd
 3765 ?        00:00:00 dhclient3
 3835 ?        00:00:00 gdm
 3836 ?        00:00:00 gdm
 3860 tty7     00:00:14 Xorg
 3869 ?        00:00:00 cupsd
 3890 ?        00:00:00 hpiod
 3893 ?        00:00:00 python
 3939 ?        00:00:00 dbus-daemon
 3954 ?        00:00:01 hald
 3955 ?        00:00:00 hald-runner
 3961 ?        00:00:00 hald-addon-acpi
 3969 ?        00:00:00 hald-addon-keyb
 3982 ?        00:00:00 hald-addon-stor
 4015 ?        00:00:00 perl
 4087 ?        00:00:00 hcid
 4093 ?        00:00:00 sdpd
 4102 ?        00:00:00 krfcommd
 4134 ?        00:00:00 atd
 4147 ?        00:00:00 cron
 4234 ?        00:00:00 gnome-session
 4270 ?        00:00:00 ssh-agent
 4273 ?        00:00:00 dbus-launch
 4274 ?        00:00:00 dbus-daemon
 4276 ?        00:00:00 gconfd-2
 4279 ?        00:00:00 gnome-keyring-d
 4282 ?        00:00:00 gnome-settings-
 4292 ?        00:00:00 sh
 4293 ?        00:00:00 esd
 4307 ?        00:00:01 nautilus
 4311 ?        00:00:00 bonobo-activati
 4313 ?        00:00:00 gnome-volume-ma
 4319 ?        00:00:00 gnome-vfs-daemo
 4324 ?        00:00:00 update-notifier
 4335 ?        00:00:00 beryl-manager
 4348 ?        00:00:00 evolution-alarm
 4407 ?        00:00:00 gnome-power-man
 4475 ?        00:00:00 emerald
 4481 ?        00:00:01 metacity
 4487 ?        00:00:00 mapping-daemon
 4490 ?        00:00:00 evolution-data-
 4503 ?        00:00:00 evolution-excha
 4536 ?        00:00:44 firefox-bin
 4551 ?        00:00:00 netstat <defunct>
 4568 ?        00:00:00 gnome-screensav
 4616 ?        00:00:00 gnome-cups-icon
 4738 ?        00:00:00 gnome-terminal
 4741 ?        00:00:00 gnome-pty-helpe
 4742 pts/0    00:00:00 bash
 4763 ?        00:00:01 gnome-panel
 4769 ?        00:00:00 mixer_applet2
 4772 pts/0    00:00:00 ps



Thanks!

It works, now

2 last thing

1.The top panel is restored, however, I deleted the bottom panel when I figured kiba would replace it, can I recreate it

2. How can I prevent from starting again?

---

### Post by molex on 2007-01-16
NM, I figured it out on my own!

Thanks for your help.

Now, give a man a fish and he eats for a day, teach a man to fish and he is fed for a life time

Where is a good place to learn Ubuntu and Linux shell and all that good stuff. Is there a book you like? or perhaps a good wiki

---

### Post by highneko on 2007-01-16
> **molex said:**
> 
Thanks!

It works, now

2 last thing

1.The top panel is restored, however, I deleted the bottom panel when I figured kiba would replace it, can I recreate it

2. How can I prevent from starting again?
You could uninstall kiba-dock. Try "sudo apt-get remove kiba-dock". Right click your top panel then click "New Panel".

---

### Post by taurus on 2007-01-16
Don't forget to remove kiba-dock from the Sessions if you won't want it to start up when you login to Gnome!

---

