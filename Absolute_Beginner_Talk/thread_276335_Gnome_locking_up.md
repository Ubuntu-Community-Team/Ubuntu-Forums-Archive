---
title: "Gnome locking up"
date: 2006-10-12
forum: Absolute Beginner Talk
---

### Post by EvanPMeth on 2006-10-12
Just recently I reformated my harddrive with ubuntu 64.
I then installed blackbox & fbpanel and set that sesion as my defualt.
I use nautilus with no desktop as my file manager and gedit along with kterm.

Today i went to start kterm and it would just freeze up, then tried to start nautilus with no desktop and it wouldnt start. Then about 2 minutes later it would pop up and kterm would start working.
Another thing is that trying to start gedit under sudo it would open not display anything ( greybox with top bar) and freeze.

What is wrong, is there something wrong with gnome. Here is my process tree:
```
init&#9472;&#9516;&#9472;acpid
     &#9500;&#9472;atd
     &#9500;&#9472;bonobo-activati
     &#9500;&#9472;cron
     &#9500;&#9472;cupsd
     &#9500;&#9472;2*[dbus-daemon]
     &#9500;&#9472;dbus-launch
     &#9500;&#9472;dd
     &#9500;&#9472;esd
     &#9500;&#9472;events/0
     &#9500;&#9472;firefox-bin&#9472;&#9472;&#9472;2*[{firefox-bin}]
     &#9500;&#9472;gconfd-2
     &#9500;&#9472;gdm&#9472;&#9472;&#9472;gdm&#9472;&#9516;&#9472;.bbstartup.sh&#9472;&#9516;&#9472;blackbox&#9472;&#9516;&#9472;nautilus&#9472;&#9472;&#9472;{nautilus}
     &#9474;           &#9474;               &#9474;          &#9492;&#9472;xterm&#9472;&#9472;&#9472;bash
     &#9474;           &#9474;               &#9500;&#9472;fbpanel
     &#9474;           &#9474;               &#9500;&#9472;gnome-settings-&#9472;&#9472;&#9472;{gnome-settings-}
     &#9474;           &#9474;               &#9492;&#9472;ssh-agent
     &#9474;           &#9492;&#9472;Xorg
     &#9500;&#9472;6*[getty]
     &#9500;&#9472;gnome-screensav
     &#9500;&#9472;gnome-terminal&#9472;&#9516;&#9472;bash&#9472;&#9472;&#9472;pstree
     &#9474;                &#9500;&#9472;gnome-pty-helpe
     &#9474;                &#9492;&#9472;{gnome-terminal}
     &#9500;&#9472;gnome-vfs-daemo&#9472;&#9472;&#9472;{gnome-vfs-daemo}
     &#9500;&#9472;hald&#9472;&#9472;&#9472;hald-runner&#9472;&#9516;&#9472;hald-addon-acpi
     &#9474;                    &#9500;&#9472;hald-addon-keyb
     &#9474;                    &#9492;&#9472;4*[hald-addon-stor]
     &#9500;&#9472;hcid
     &#9500;&#9472;khelper
     &#9500;&#9472;khpsbpkt
     &#9500;&#9472;2*[kjournald]
     &#9500;&#9472;klogd
     &#9500;&#9472;knodemgrd_0
     &#9500;&#9472;krfcommd
     &#9500;&#9472;ksoftirqd/0
     &#9500;&#9472;kswapd0
     &#9500;&#9472;kthread&#9472;&#9516;&#9472;aio/0
     &#9474;         &#9500;&#9472;ata/0
     &#9474;         &#9500;&#9472;ata_hotplug/0
     &#9474;         &#9500;&#9472;kacpid
     &#9474;         &#9500;&#9472;kblockd/0
     &#9474;         &#9500;&#9472;kgameportd
     &#9474;         &#9500;&#9472;khubd
     &#9474;         &#9500;&#9472;kseriod
     &#9474;         &#9500;&#9472;2*[pdflush]
     &#9474;         &#9500;&#9472;scsi_eh_0
     &#9474;         &#9500;&#9472;scsi_eh_1
     &#9474;         &#9500;&#9472;scsi_eh_3
     &#9474;         &#9492;&#9472;usb-storage
     &#9500;&#9472;mapping-daemon
     &#9500;&#9472;mdadm
     &#9500;&#9472;migration/0
     &#9500;&#9472;sdpd
     &#9500;&#9472;shpchpd_event
     &#9500;&#9472;syslogd
     &#9500;&#9472;udevd
     &#9492;&#9472;watchdog/0

```

also my x startup includes:
```
#!/bin/sh

gnome-settings-daemon &
fbpanel &
blackbox

```

If anyone has any sugestions what im doing wrong feel free

I can supply as much info as you need.

---

### Post by EvanPMeth on 2006-10-12
Also when trying to log back into the gnome desktop sesion and failsafe gnome session i get a blank burgandy screen.

Any ideas?

---

