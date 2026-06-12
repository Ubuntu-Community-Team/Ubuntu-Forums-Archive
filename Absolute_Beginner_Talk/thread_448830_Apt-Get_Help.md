---
title: "Apt-Get Help"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by LancerDragoon on 2007-05-19
Hi, I'm quite new to Ubuntu (although I am starting to get familiar to Unix commands thanks to the fact that I use Cygwin on Windows) and I'm having a problem with apt-get. When I tried to install Links, by typing...
```
sudo apt-get install links
```
this is what I get:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I get this no matter what I do, and I don't have Synaptic or Add/Remove Programs running or Automatix, even. I just tried rebooting and trying to install Links but to no avail. Strangely, Synaptic works, as is Add/Remove Programs.

Please can someone help?

---

### Post by Outrunner on 2007-05-19
Do you have Synaptic open at the time of entering this command? If not, I think sudo apt-get update -f will fix it, although I'm not entirely sure since I didn't need to fix something like this in some time. Too bad I have such a poor memory ehh?

---

### Post by LancerDragoon on 2007-05-19
I've tried that too, actually, forcing an update. It just refuses to do it. And no, I didn't have Synaptic running at the time. I'm assuming that some process is using the directory, but since I didn't run any admin services while doing that, I can't figure out what. 

And like I mentioned, it was odd that Synaptic can run and install packages when the command-line equivalent fails.

---

### Post by taurus on 2007-05-19
Post the output of this command from a terminal.

```
ps -A
```

---

### Post by LancerDragoon on 2007-05-19
Output of ps -A from Terminal:

```
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
   30 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kacpid
   32 ?        00:00:00 kacpi_notify
  131 ?        00:00:00 kseriod
  152 ?        00:00:00 pdflush
  153 ?        00:00:00 pdflush
  154 ?        00:00:00 kswapd0
  155 ?        00:00:00 aio/0
 1959 ?        00:00:00 ksuspend_usbd
 1960 ?        00:00:00 khubd
 1982 ?        00:00:01 ata/0
 1983 ?        00:00:00 ata_aux
 1988 ?        00:00:00 khpsbpkt
 2111 ?        00:00:00 knodemgrd_0
 2114 ?        00:00:02 scsi_eh_0
 2115 ?        00:00:00 scsi_eh_1
 2214 ?        00:00:00 scsi_eh_2
 2215 ?        00:00:00 usb-storage
 2313 ?        00:00:00 kjournald
 2513 ?        00:00:00 udevd
 3419 ?        00:00:00 hda_codec
 3456 ?        00:00:00 kpsmoused
 3457 ?        00:00:00 pccardd
 3458 ?        00:00:00 tifm/0
 3490 ?        00:00:00 ipw2200/0
 3980 ?        00:00:00 mount.ntfs-3g
 3984 ?        00:00:00 mount.ntfs-3g
 4252 tty4     00:00:00 getty
 4253 tty5     00:00:00 getty
 4255 tty2     00:00:00 getty
 4256 tty3     00:00:00 getty
 4257 tty1     00:00:00 getty
 4258 tty6     00:00:00 getty
 4468 ?        00:00:00 avahi-autoipd
 4469 ?        00:00:00 avahi-autoipd
 4529 ?        00:00:00 acpid
 4629 ?        00:00:00 syslogd
 4681 ?        00:00:00 dd
 4683 ?        00:00:00 klogd
 4704 ?        00:00:02 dbus-daemon
 4720 ?        00:00:01 hald
 4721 ?        00:00:00 hald-runner
 4727 ?        00:00:00 hald-addon-keyb
 4730 ?        00:00:00 hald-addon-cpuf
 4731 ?        00:00:00 hald-addon-acpi
 4734 ?        00:00:00 hald-addon-keyb
 4735 ?        00:00:00 hald-addon-keyb
 4748 ?        00:00:01 hald-addon-stor
 4761 ?        00:00:00 dhcdbd
 4776 ?        00:00:00 NetworkManager
 4792 ?        00:00:00 dhclient3
 4811 ?        00:00:00 avahi-daemon
 4812 ?        00:00:00 avahi-daemon
 4827 ?        00:00:00 NetworkManagerD
 4844 ?        00:00:00 system-tools-ba
 4845 ?        00:00:00 dbus-daemon
 4898 ?        00:00:00 gdm
 4901 ?        00:00:00 gdm
 4904 ?        00:00:00 dhclient
 5018 ?        00:00:00 cupsd
 5055 ?        00:00:00 hpiod
 5058 ?        00:00:00 python
 5125 ?        00:00:00 hald-addon-keyb
 5132 ?        00:00:00 hald-addon-keyb
 5152 ?        00:00:00 kondemand/0
 5189 ?        00:00:00 hcid
 5209 ?        00:00:00 krfcommd
 5230 ?        00:00:00 anacron
 5244 ?        00:00:00 atd
 5258 ?        00:00:00 cron
 5403 ?        00:00:00 scsi_eh_3
 5404 ?        00:00:00 usb-storage
 5494 ?        00:00:00 hald-addon-keyb
 5499 ?        00:00:00 hald-addon-keyb
 5527 ?        00:00:00 hald-addon-stor
 5907 ?        00:00:00 sh
 5908 ?        00:00:00 run-parts
 5919 ?        00:00:00 apt
 5931 ?        00:00:00 apt-get
 5933 ?        00:00:00 http
 5934 ?        00:00:00 http
 5935 ?        00:00:00 http
 5936 ?        00:00:00 http
 5937 ?        00:00:00 http
 5939 ?        00:00:00 gpgv
 5947 ?        00:00:00 bzip2
11149 tty7     00:02:01 Xorg
11171 ?        00:00:00 x-session-manag
11209 ?        00:00:00 ssh-agent
11212 ?        00:00:00 dbus-daemon
11213 ?        00:00:00 dbus-launch
11215 ?        00:00:00 gconfd-2
11218 ?        00:00:00 gnome-keyring-d
11220 ?        00:00:00 gnome-settings-
11227 ?        00:00:00 sh
11228 ?        00:00:00 esd
11232 ?        00:00:00 compiz
11237 ?        00:00:03 gnome-panel
11240 ?        00:00:00 gtk-window-deco
11242 ?        00:00:00 nautilus
11245 ?        00:00:00 bonobo-activati
11248 ?        00:00:00 gnome-vfs-daemo
11251 ?        00:00:00 gnome-volume-ma
11259 ?        00:00:03 compiz.real
11261 ?        00:00:00 update-notifier
11263 ?        00:00:00 evolution-alarm
11265 ?        00:00:00 nm-applet
11270 ?        00:00:00 gnome-cups-icon
11290 ?        00:00:00 mount.ntfs-3g
11301 ?        00:00:00 gnome-power-man
11303 ?        00:00:00 trashapplet
11314 ?        00:00:00 mixer_applet2
11316 ?        00:00:00 mapping-daemon
11349 ?        00:00:03 gnome-terminal
11351 ?        00:00:00 gnome-pty-helpe
11352 pts/0    00:00:00 bash
11378 ?        00:00:01 gnome-screensav
11511 ?        00:01:30 firefox-bin
12239 ?        00:00:01 gaim
12322 pts/0    00:00:00 ps

```

---

### Post by taurus on 2007-05-19
You have both apt & apt-get running at the same time.  Can't run two at the same time.

```
 5919 ?        00:00:00 apt
 5931 ?        00:00:00 apt-get
```
Therefore, kill them both with

```
sudo kill -9 5919
sudo kill -9 5931
```
Then, run

```
sudo apt-get update
sudo apt-get install links
```

---

### Post by LancerDragoon on 2007-05-19
Thank you! That solved my problems!

---

