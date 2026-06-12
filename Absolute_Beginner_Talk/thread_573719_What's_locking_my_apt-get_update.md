---
title: "What's locking my apt-get update?"
date: 2007-10-11
forum: Absolute Beginner Talk
---

### Post by OliverN on 2007-10-11
...and how do I kill it?

sudo apt-get update returns

```
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
```

ps -A returns:

```
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
   29 ?        00:00:00 kblockd/0
   30 ?        00:00:00 kacpid
   31 ?        00:00:00 kacpi_notify
  161 ?        00:00:00 kseriod
  186 ?        00:00:00 pdflush
  187 ?        00:00:00 pdflush
  188 ?        00:00:00 kswapd0
  189 ?        00:00:00 aio/0
 1983 ?        00:00:00 ksuspend_usbd
 1984 ?        00:00:00 khubd
 2039 ?        00:00:00 khpsbpkt
 2130 ?        00:00:00 ata/0
 2131 ?        00:00:00 ata_aux
 2132 ?        00:00:00 scsi_eh_0
 2133 ?        00:00:00 scsi_eh_1
 2198 ?        00:00:00 knodemgrd_0
 2250 ?        00:00:00 scsi_eh_2
 2251 ?        00:00:01 usb-storage
 2558 ?        00:00:00 kjournald
 2760 ?        00:00:00 udevd
 3695 ?        00:00:00 kpsmoused
 3712 ?        00:00:00 ipw3945/0
 3713 ?        00:00:00 ipw3945/0
 3733 ?        00:00:00 kmmcd
 3839 ?        00:00:00 hda_codec
 3927 ?        00:00:16 ipw3945d-2.6.20
 4357 ?        00:00:00 portmap
 4487 tty4     00:00:00 getty
 4488 tty5     00:00:00 getty
 4493 tty2     00:00:00 getty
 4494 tty3     00:00:00 getty
 4495 tty1     00:00:00 getty
 4496 tty6     00:00:00 getty
 4738 ?        00:00:00 acpid
 4835 ?        00:00:00 syslogd
 4888 ?        00:00:00 dd
 4890 ?        00:00:00 klogd
 4911 ?        00:00:01 dbus-daemon
 4927 ?        00:00:05 hald
 4928 ?        00:00:00 hald-runner
 4934 ?        00:00:00 hald-addon-usb-
 4935 ?        00:00:00 hald-addon-keyb
 4937 ?        00:00:00 hald-addon-cpuf
 4938 ?        00:00:00 hald-addon-acpi
 4939 ?        00:00:00 hald-addon-keyb
 4940 ?        00:00:00 hald-addon-keyb
 4941 ?        00:00:00 hald-addon-keyb
 4955 ?        00:00:00 hald-addon-stor
 4968 ?        00:00:00 dhcdbd
 4983 ?        00:00:00 NetworkManager
 5001 ?        00:00:00 avahi-daemon
 5002 ?        00:00:00 avahi-daemon
 5017 ?        00:00:00 NetworkManagerD
 5031 ?        00:00:00 system-tools-ba
 5032 ?        00:00:00 dbus-daemon
 5081 ?        00:00:00 gdm
 5168 ?        00:00:02 cupsd
 5192 ?        00:00:00 hpiod
 5195 ?        00:00:00 python
 5331 ?        00:00:00 freshclam
 5397 ?        00:00:00 inetutils-inetd
 5441 ?        00:00:00 lockd
 5442 ?        00:00:00 rpciod/0
 5443 ?        00:00:00 nfsd4
 5444 ?        00:00:00 nfsd
 5445 ?        00:00:00 nfsd
 5446 ?        00:00:00 nfsd
 5447 ?        00:00:00 nfsd
 5448 ?        00:00:00 nfsd
 5449 ?        00:00:00 nfsd
 5450 ?        00:00:00 nfsd
 5451 ?        00:00:00 nfsd
 5455 ?        00:00:00 rpc.mountd
 5475 ?        00:00:00 kondemand/0
 5492 ?        00:00:00 nmbd
 5500 ?        00:00:00 smbd
 5559 ?        00:00:00 rpc.statd
 5560 ?        00:00:00 smbd
 5569 ?        00:00:00 rpc.idmapd
 5586 ?        00:00:00 hcid
 5600 ?        00:00:00 krfcommd
 5622 ?        00:00:00 anacron
 5636 ?        00:00:00 atd
 5650 ?        00:00:00 cron
 5843 ?        00:00:00 bonobo-activati
 5968 ?        00:00:00 evolution-data-
 6197 ?        00:00:00 wpa_supplicant
 6237 ?        00:00:00 dhclient
 6438 ?        00:00:00 sh
 6439 ?        00:00:00 run-parts
 6450 ?        00:00:00 apt
 6462 ?        00:00:00 apt-get
 6464 ?        00:00:00 http
 6465 ?        00:00:00 http
 6466 ?        00:00:00 http
 6467 ?        00:00:00 http
 6468 ?        00:00:00 http
 6469 ?        00:00:00 http
 6470 ?        00:00:00 http
 6472 ?        00:00:00 gpgv
 6485 ?        00:00:00 bzip2
10393 ?        00:00:00 avahi-autoipd
10394 ?        00:00:00 avahi-autoipd
10402 ?        00:00:00 dhclient3
18789 ?        00:00:00 gdm
18790 tty7     00:00:09 Xorg
20256 ?        00:00:00 gconfd-2
20271 ?        00:00:00 gnome-session
20312 ?        00:00:00 ssh-agent
20315 ?        00:00:00 dbus-daemon
20316 ?        00:00:00 dbus-launch
20317 ?        00:00:07 Xgl
20326 ?        00:00:00 dbus-daemon
20327 ?        00:00:00 dbus-launch
20330 ?        00:00:00 gnome-keyring-d
20332 ?        00:00:00 gnome-settings-
20340 ?        00:00:00 sh
20341 ?        00:00:00 esd
20346 ?        00:00:01 nautilus
20348 ?        00:00:01 gnome-panel
20351 ?        00:00:00 gnome-vfs-daemo
20352 ?        00:00:00 gnome-volume-ma
20357 ?        00:00:00 update-notifier
20362 ?        00:00:00 gnome-cups-icon
20363 ?        00:00:00 evolution-alarm
20365 ?        00:00:00 compiz
20366 ?        00:00:00 python
20367 ?        00:00:00 python
20371 ?        00:00:00 emerald
20374 ?        00:00:00 kiba-dock
20375 ?        00:00:00 python
20415 ?        00:00:00 unclutter
20416 ?        00:00:00 cairo-clock
20417 ?        00:00:00 nm-applet
20420 ?        00:00:00 gnome-power-man
20439 ?        00:00:00 evolution-excha
20454 ?        00:00:00 mapping-daemon
20645 ?        00:00:00 compiz
20646 ?        00:00:03 compiz.real
20663 ?        00:00:00 gnome-screensav
20669 ?        00:00:00 sh
20670 ?        00:00:00 gnome-terminal
20675 ?        00:00:00 gnome-pty-helpe
20676 pts/0    00:00:00 bash
20701 ?        00:00:07 firefox-bin
20743 pts/0    00:00:00 ps
```

---

### Post by Jimmyfj on 2007-10-11
Do you have more than one packet manager running?

---

### Post by Pumalite on 2007-10-11
Close Synaptic

---

### Post by OliverN on 2007-10-11
> **Jimmyfj said:**
> Do you have more than one packet manager running?

Well, not as far as I know, but I thought that would show from the ps -A output. I use Synaptic, but it's not running when I do apt-get update. -At least not that I know of :neutral:

---

### Post by OliverN on 2007-10-11
> **Pumalite said:**
> Close Synaptic

If this is because of a Synaptic process then please tell me how to kill it and how to stop it from loading into my session on its own.

---

### Post by Pumalite on 2007-10-11
It was only in case you had it opened and had forgotten it.

---

