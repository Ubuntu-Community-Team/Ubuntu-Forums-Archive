---
title: "problem with package installer"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Resistance on 2007-12-09
Hello,

I was trying to install Limewire, when the the process froze. I restarted the PC, and tried again, but got an error message telling me that "only one software management tool is allowed to run at the same time". I even switched off my computer, but I keep getting this error. 

How do I convince Ubuntu there is really only one smt running, or how do I terminate this process in case it is running somewhere in the background....?

Thank you very much for your advice.

---

### Post by taurus on 2007-12-09
Post the output of this command from a terminal.

```
ps -A
```

---

### Post by bsell on 2007-12-09
Use the top command or the System Monitor under the System>Administration menu to view what processes are running.

---

### Post by Resistance on 2007-12-09
1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   30 ?        00:00:00 kblockd/0
   31 ?        00:00:00 kblockd/1
   32 ?        00:00:00 kacpid
   33 ?        00:00:00 kacpi_notify
  198 ?        00:00:00 kseriod
  233 ?        00:00:00 pdflush
  234 ?        00:00:00 pdflush
  235 ?        00:00:00 kswapd0
  288 ?        00:00:00 aio/0
  289 ?        00:00:00 aio/1
 2294 ?        00:00:00 ksuspend_usbd
 2295 ?        00:00:00 khubd
 2314 ?        00:00:00 ata/0
 2315 ?        00:00:00 ata/1
 2316 ?        00:00:00 ata_aux
 2340 ?        00:00:00 khpsbpkt
 2390 ?        00:00:00 scsi_eh_0
 2391 ?        00:00:00 scsi_eh_1
 2431 ?        00:00:00 scsi_eh_2
 2432 ?        00:00:00 scsi_eh_3
 2471 ?        00:00:00 scsi_eh_4
 2472 ?        00:00:00 scsi_eh_5
 2506 ?        00:00:00 scsi_eh_7
 2507 ?        00:00:00 usb-storage
 2713 ?        00:00:00 knodemgrd_0
 2815 ?        00:00:00 kjournald
 2875 ?        00:00:00 scsi_eh_8
 2876 ?        00:00:00 usb-storage
 3020 ?        00:00:00 udevd
 4182 ?        00:00:00 kpsmoused
 4796 ?        00:00:00 mount.ntfs
 4799 ?        00:00:00 mount.ntfs
 5041 tty4     00:00:00 getty
 5042 tty5     00:00:00 getty
 5044 tty2     00:00:00 getty
 5047 tty3     00:00:00 getty
 5048 tty1     00:00:00 getty
 5049 tty6     00:00:00 getty
 5236 ?        00:00:00 acpid
 5264 ?        00:00:00 kondemand/0
 5265 ?        00:00:00 kondemand/1
 5349 ?        00:00:00 syslogd
 5405 ?        00:00:00 dd
 5407 ?        00:00:00 klogd
 5428 ?        00:00:00 dbus-daemon
 5444 ?        00:00:00 NetworkManager
 5458 ?        00:00:00 NetworkManagerD
 5471 ?        00:00:00 system-tools-ba
 5472 ?        00:00:00 dbus-daemon
 5491 ?        00:00:00 hald
 5492 ?        00:00:00 hald-runner
 5552 ?        00:00:00 cupsd
 5553 ?        00:00:00 hald-addon-keyb
 5561 ?        00:00:00 hald-addon-keyb
 5562 ?        00:00:00 hald-addon-keyb
 5563 ?        00:00:00 hald-addon-keyb
 5564 ?        00:00:00 hald-addon-keyb
 5589 ?        00:00:00 hald-addon-cpuf
 5591 ?        00:00:00 hald-addon-acpi
 5638 ?        00:00:00 console-kit-dae
 5745 ?        00:00:00 avahi-daemon
 5746 ?        00:00:00 avahi-daemon
 5776 ?        00:00:00 dhcdbd
 5802 ?        00:00:00 hcid
 5812 ?        00:00:00 hald-addon-stor
 5821 ?        00:00:00 hald-addon-stor
 5825 ?        00:00:00 bluetoothd-serv
 5826 ?        00:00:00 bluetoothd-serv
 5831 ?        00:00:00 krfcommd
 5886 ?        00:00:00 gdm
 5887 ?        00:00:00 gdm
 5894 tty7     00:00:24 Xorg
 5900 ?        00:00:00 dhclient
 5937 ?        00:00:00 atd
 5951 ?        00:00:00 cron
 6061 ?        00:00:00 x-session-manag
 6112 ?        00:00:00 ssh-agent
 6114 ?        00:00:00 gconfd-2
 6155 ?        00:00:00 gnome-keyring-d
 6157 ?        00:00:00 dbus-daemon
 6159 ?        00:00:00 gnome-settings-
 6166 ?        00:00:00 compiz
 6168 ?        00:00:02 gnome-panel
 6170 ?        00:00:01 nautilus
 6176 ?        00:00:00 bonobo-activati
 6179 ?        00:00:00 gnome-volume-ma
 6232 ?        00:00:00 gnome-vfs-daemo
 6234 ?        00:00:00 mount.ntfs-3g
 6272 ?        00:00:00 gtk-window-deco
 6273 ?        00:00:07 compiz.real
 6277 ?        00:00:00 vino-session
 6278 ?        00:00:01 gnome-screensav
 6279 ?        00:00:00 bluetooth-apple
 6284 ?        00:00:00 update-notifier
 6291 ?        00:00:00 evolution-alarm
 6293 ?        00:00:00 trackerd
 6298 ?        00:00:00 nm-applet
 6300 ?        00:00:00 python
 6302 ?        00:00:00 gnome-power-man
 6310 ?        00:00:00 trashapplet
 6325 ?        00:00:00 mapping-daemon
 6354 ?        00:00:00 fast-user-switc
 6356 ?        00:00:00 deskbar-applet
 6360 ?        00:00:00 mixer_applet2
 6365 ?        00:00:00 swiftfox
 6377 ?        00:00:00 run-mozilla.sh
 6381 ?        00:00:52 swiftfox-bin
 6412 ?        00:00:01 pidgin
 6430 ?        00:00:02 gxine
 6461 ?        00:00:00 gnome-terminal
 6463 ?        00:00:00 gnome-pty-helpe
 6464 pts/0    00:00:00 bash
 6481 pts/0    00:00:00 ps

---

