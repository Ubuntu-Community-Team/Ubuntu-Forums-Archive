---
title: "XMMS gui won't work"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by onejoy on 2005-11-25
I just installed XMMS using apt-get and it'll run, but the gui won't come up.  I can right click on an mp3 and select "Open with XMMS" and the song'll start playing, but there's no GUI, no window, and nothing that I can see that's playing it, but I found 3 instances of XMMS running (I tried to start it multiple times).  

Does anyone know what's wrong?  Thanks

---

### Post by kori.mendocino on 2005-11-25
hm, weird. what does the console say about it?
in the meantime, try beep-media-player

---

### Post by onejoy on 2005-11-25
Sorry, but What's the console?

---

### Post by wsanders on 2005-11-25
Console: go to applications: accessories: Terminal . It's the command line, type xmms into it and see if any text comes up in the console.

---

### Post by onejoy on 2005-11-25
i went into the terminal and typed in 

```

marachan@onejoy:~$ xmms
marachan@onejoy:~$

```

and nothing happened.

---

### Post by wsanders on 2005-11-25
type in 
```

ps -A

```
after you run xmms from the console, and see if xmms shows up in that list.

---

### Post by onejoy on 2005-11-25
I tried out ps -a and this is what I get.

```

marachan@onejoy:~$ xmms
marachan@onejoy:~$ ps -a
  PID TTY          TIME CMD
27039 pts/2    00:00:00 ps
marachan@onejoy:~$

```

I have no idea what this means.

---

### Post by manicka on 2005-11-25
I may have minimised itself to the systray.

---

### Post by wsanders on 2005-11-25
it has to be ps -A (be sure that the A is capitalized). You'll get a long list of running programs, just copy the last 15 or so and paste them here.

---

### Post by nahtura on 2008-07-23
Hello there, i am not the same user as above but i seem to be having a similar problem, This is my print out of the active services, if anyone could shed some light on the matter that would be great. Many thanks.

?@?-desktop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
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
   44 ?        00:00:00 kblockd/0
   45 ?        00:00:00 kblockd/1
   48 ?        00:00:00 kacpid
   49 ?        00:00:00 kacpi_notify
  141 ?        00:00:00 kseriod
  188 ?        00:00:00 pdflush
  189 ?        00:00:00 pdflush
  190 ?        00:00:00 kswapd0
  233 ?        00:00:00 aio/0
  234 ?        00:00:00 aio/1
 1413 ?        00:00:00 ksuspend_usbd
 1414 ?        00:00:00 khubd
 1553 ?        00:00:00 khpsbpkt
 1576 ?        00:00:00 ata/0
 1581 ?        00:00:00 ata/1
 1594 ?        00:00:00 ata_aux
 2378 ?        00:00:00 scsi_eh_0
 2380 ?        00:00:00 scsi_eh_1
 2418 ?        00:00:00 knodemgrd_0
 2420 ?        00:00:00 scsi_eh_2
 2421 ?        00:00:00 scsi_eh_3
 2458 ?        00:00:00 scsi_eh_4
 2459 ?        00:00:00 scsi_eh_5
 2523 ?        00:00:00 scsi_eh_6
 2524 ?        00:00:00 scsi_eh_7
 2744 ?        00:00:00 kjournald
 3032 ?        00:00:00 udevd
 3692 ?        00:00:00 rtl8187
 4916 tty4     00:00:00 getty
 4917 tty5     00:00:00 getty
 4919 tty2     00:00:00 getty
 4921 tty3     00:00:00 getty
 4923 tty6     00:00:00 getty
 5103 ?        00:00:00 acpid
 5155 ?        00:00:00 kondemand/0
 5156 ?        00:00:00 kondemand/1
 5217 ?        00:00:00 syslogd
 5275 ?        00:00:00 dd
 5277 ?        00:00:00 klogd
 5299 ?        00:00:00 dbus-daemon
 5315 ?        00:00:00 NetworkManager
 5329 ?        00:00:00 NetworkManagerD
 5342 ?        00:00:00 system-tools-ba
 5362 ?        00:00:00 avahi-daemon
 5363 ?        00:00:00 avahi-daemon
 5395 ?        00:00:00 cupsd
 5458 ?        00:00:00 dhcdbd
 5477 ?        00:00:00 hald
 5480 ?        00:00:00 console-kit-dae
 5542 ?        00:00:00 hald-runner
 5566 ?        00:00:00 hald-addon-inpu
 5568 ?        00:00:00 hald-addon-cpuf
 5569 ?        00:00:00 hald-addon-acpi
 5588 ?        00:00:00 hald-addon-stor
 5608 ?        00:00:00 hcid
 5618 ?        00:00:00 btaddconn
 5619 ?        00:00:00 btdelconn
 5629 ?        00:00:00 bluetoothd-serv
 5630 ?        00:00:00 bluetoothd-serv
 5635 ?        00:00:00 krfcommd
 5674 ?        00:00:00 gdm
 5677 ?        00:00:00 gdm
 5681 tty7     00:00:50 Xorg
 5722 ?        00:00:00 atd
 5736 ?        00:00:00 cron
 5816 tty1     00:00:00 getty
 5875 ?        00:00:00 dhclient
 6148 ?        00:00:00 gconfd-2
 6150 ?        00:00:00 gnome-keyring-d
 6151 ?        00:00:00 x-session-manag
 6207 ?        00:00:00 seahorse-agent
 6211 ?        00:00:00 dbus-daemon
 6212 ?        00:00:00 gnome-settings-
 6220 ?        00:00:01 pulseaudio
 6223 ?        00:00:00 gconf-helper
 6232 ?        00:00:00 compiz
 6234 ?        00:00:02 gnome-panel
 6235 ?        00:00:01 gnome-screensav
 6236 ?        00:00:00 nautilus
 6246 ?        00:00:00 bonobo-activati
 6263 ?        00:00:00 gvfsd
 6277 ?        00:00:00 gvfs-fuse-daemo
 6306 ?        00:00:10 compiz.real
 6307 ?        00:00:00 bluetooth-apple
 6310 ?        00:00:00 update-notifier
 6317 ?        00:00:00 tracker-applet
 6321 ?        00:00:00 trackerd
 6324 ?        00:00:00 python
 6325 ?        00:00:00 gnome-volume-ma
 6328 ?        00:00:00 nm-applet
 6332 ?        00:00:00 trashapplet
 6334 ?        00:00:00 gnome-power-man
 6338 ?        00:00:00 gvfsd-trash
 6348 ?        00:00:00 gvfsd-burn
 6357 ?        00:00:00 mixer_applet2
 6360 ?        00:00:00 fast-user-switc
 6363 ?        00:00:00 evolution-data-
 6380 ?        00:00:00 sh
 6381 ?        00:00:00 compiz-decorato
 6383 ?        00:00:00 gtk-window-deco
 6452 ?        00:00:03 pidgin
 6454 ?        00:00:14 java
 6526 ?        00:00:00 evolution-alarm
 6722 ?        00:00:00 gvfsd-network
 6724 ?        00:00:00 gvfsd-smb-brows
 6735 ?        00:00:00 gvfsd-dnssd
 6861 ?        00:00:00 gnome-terminal
 6863 ?        00:00:00 gnome-pty-helpe
 6864 pts/0    00:00:00 bash
 6930 ?        00:00:00 xmms2d
 6995 ?        00:00:01 firefox
 7026 pts/0    00:00:00 ps

---

### Post by 0x29a on 2008-07-23
Interesting. What version of Ubuntu are you running? xmms2d is running. xmms2d is a background application. That means you can't directly interact with it. I've read somewhere on here that the original xmms has been removed from the repositories. 

Try typing ```
 which xmms 
``` the output will look something like, but maybe not identical to this ```
 0x29a@yogibot:/home/0x29a$ which xmms
/usr/bin/xmms

```
Once you've done that note the path to xmms and type ```
0x29a@yogibot:/home/0x29a$ ls -l /usr/bin/xmms 
```
and paste that output here as well. I'm thinking you've installed xmms2-core. So, we need to find out if xmms is a link (like a shortcut) to the wrong thing.

On a personal note, I've never liked xmms2. I've downloaded the original xmms from here
[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

Good ol' xmms. :-)

Hope this all helps.

---

