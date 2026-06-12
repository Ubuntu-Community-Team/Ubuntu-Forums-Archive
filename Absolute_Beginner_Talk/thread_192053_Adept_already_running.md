---
title: "Adept already running?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by highslime on 2006-06-08
Last night I was trying to install the JRE5.0 or whatchamacallit(Java) by using the Adept package manager, and all went well until it reached the license agreement.  It was taking an unusual amount of time to install JRE, so I clicked details, and I saw the EULA in the details, and it was waiting for me to click OK.  Well, after several curious keystrokes later, I still wasn't able to get it to continue on, so I closed the Adept window, and just figured I could start over using the command line so I could click OK at the agreement.  Well apparently I screwed something up, because now whenever I try to get an update, or do anything like that, it tells me the package manager is already running.  I've rebooted my comp since then, and I still get this message.  I tried reading the killall man page, but I couldn't make heads or tails of any of it.  The error message I get is as follows:

     You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

I opened up the system monitor to see running processes, and I saw Adept notifier, so I killed that, and still got the same message.  This sucks.  Can someone help me figure out how to make it so I can use it again?

---

### Post by taurus on 2006-06-08
What is the output of this command, from a terminal?
```

ps -A

```

---

### Post by highslime on 2006-06-08
```

 PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  150 ?        00:00:00 pdflush
  151 ?        00:00:00 pdflush
  153 ?        00:00:00 aio/0
  152 ?        00:00:00 kswapd0
  740 ?        00:00:00 kseriod
 1754 ?        00:00:00 ata/0
 1755 ?        00:00:00 ata_hotplug/0
 1845 ?        00:00:00 khubd
 1939 ?        00:00:00 kjournald
 2167 ?        00:00:00 udevd
 2978 ?        00:00:00 shpchpd_event
 3418 ?        00:00:00 dhclient3
 3857 ?        00:00:00 acpid
 3947 ?        00:00:00 syslogd
 3973 ?        00:00:00 dd
 3975 ?        00:00:00 klogd
 4000 ?        00:00:00 hpiod
 4003 ?        00:00:00 python
 4050 ?        00:00:00 cupsd
 4073 ?        00:00:00 dbus-daemon
 4088 ?        00:00:01 hald
 4089 ?        00:00:00 hald-runner
 4094 ?        00:00:00 hald-addon-acpi
 4144 ?        00:00:00 hald-addon-keyb
 4155 ?        00:00:00 hald-addon-stor
 4156 ?        00:00:00 hald-addon-stor
 4230 ?        00:00:00 hcid
 4235 ?        00:00:00 sdpd
 4245 ?        00:00:00 krfcommd
 4258 ?        00:00:00 mdadm
 4292 ?        00:00:00 atd
 4305 ?        00:00:00 cron
 4652 ?        00:00:00 kdm
 4705 tty1     00:00:00 getty
 4706 tty2     00:00:00 getty
 4707 tty3     00:00:00 getty
 4708 tty4     00:00:00 getty
 4709 tty5     00:00:00 getty
 4716 tty6     00:00:00 getty
 5008 tty7     00:00:36 Xorg
 5009 ?        00:00:00 kdm
 5018 ?        00:00:00 startkde
 5055 ?        00:00:00 ssh-agent
 5058 ?        00:00:00 dbus-daemon
 5059 ?        00:00:00 dbus-launch
 5091 ?        00:00:00 kdeinit
 5094 ?        00:00:00 dcopserver
 5096 ?        00:00:00 klauncher
 5098 ?        00:00:00 kded
 5100 ?        00:00:01 gam_server
 5105 ?        00:00:00 kwrapper
 5107 ?        00:00:00 ksmserver
 5108 ?        00:00:01 kwin
 5110 ?        00:00:00 kdesktop
 5112 ?        00:00:12 kicker
 5118 ?        00:00:00 kio_uiserver
 5129 ?        00:00:02 artsd
 5133 ?        00:00:00 kaccess
 5136 ?        00:00:00 kmix
 5138 ?        00:00:00 katapult
 5142 ?        00:00:00 kbluetoothd
 5144 ?        00:00:00 klipper
 5149 ?        00:00:00 kdesu
 5151 ?        00:00:00 kdesud
 5153 pts/1    00:00:00 kdesu_stub
 5155 pts/2    00:00:00 sudo
 5156 ?        00:00:00 firefox
 5167 ?        00:00:00 run-mozilla.sh
 5172 ?        00:00:58 firefox-bin
 5218 ?        00:00:00 knotify
 5227 ?        00:00:01 konqueror
 5235 ?        00:00:00 kio_file
 5302 ?        00:00:00 artsd
 5326 ?        00:00:05 ksysguard
 5327 ?        00:00:00 ksysguardd
 5332 ?        00:00:00 konsole
 5333 pts/3    00:00:00 bash
 5350 pts/3    00:00:00 ps

```

in the process monitor it says i have 83 processes.  that sounds like WAY too much for just running firefox, process table, and the konsole.  wtf.

---

### Post by taurus on 2006-06-08
83 processes for KDE seem to be about right!  If you think you have too many processes running, then don't use window manager.  That would cut back some!!!  See what happens when you run this from a terminal!
```

sudo apt-get update

```

---

### Post by highslime on 2006-06-08
```

Get:1 ftp://ftp.free.fr dapper Release.gpg
Ign ftp://ftp.free.fr dapper Release.gpg
Get:2 ftp://ftp.free.fr dapper Release
Ign ftp://ftp.free.fr dapper Release
Get:3 ftp://ftp.free.fr dapper/free Packages
Ign ftp://ftp.free.fr dapper/free Packages
Get:4 ftp://ftp.free.fr dapper/non-free Packages
Ign ftp://ftp.free.fr dapper/non-free Packages
Get:5 ftp://ftp.free.fr dapper/free Sources
Ign ftp://ftp.free.fr dapper/free Sources
Get:6 ftp://ftp.free.fr dapper/non-free Sources
Get:7 http://kubuntu.org dapper Release.gpg [191B]
Get:8 http://kubuntu.org dapper Release.gpg [191B]
Get:9 http://mirror3.ubuntulinux.nl dapper-seveas Release.gpg [309B]
Get:10 http://mirror.ubuntulinux.nl dapper-seveas Release.gpg [309B]
Hit http://kubuntu.org dapper Release
Ign ftp://ftp.free.fr dapper/non-free Sources
Get:11 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:12 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://mirror.ubuntulinux.nl dapper-seveas Release
Hit http://kubuntu.org dapper Release
Hit http://mirror3.ubuntulinux.nl dapper-seveas Release
Hit http://us.archive.ubuntu.com dapper Release
Err http://kubuntu.org dapper Release

Err http://mirror.ubuntulinux.nl dapper-seveas Release

Err http://mirror3.ubuntulinux.nl dapper-seveas Release

Get:13 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:14 http://us.archive.ubuntu.com dapper-updates Release [27.0kB]
Get:15 http://kubuntu.org dapper Release [2327B]
Ign http://kubuntu.org dapper Release
Hit ftp://ftp.free.fr dapper/free Packages
Get:16 http://mirror.ubuntulinux.nl dapper-seveas Release [8343B]
Get:17 ftp://cipherfunk.org dapper Release.gpg [189B]
Get:18 http://security.ubuntu.com dapper-security Release [23.4kB]
Get:19 http://kubuntu.org dapper Release [2330B]
Ign http://kubuntu.org dapper Release
Get:20 http://mirror3.ubuntulinux.nl dapper-seveas Release [8343B]
Ign http://mirror.ubuntulinux.nl dapper-seveas Release
Hit http://kubuntu.org dapper/main Packages
Hit http://kubuntu.org dapper/main Sources
Hit ftp://ftp.free.fr dapper/non-free Packages
Hit http://mirror.ubuntulinux.nl dapper-seveas/all Packages
Hit http://kubuntu.org dapper/main Packages
Ign http://mirror3.ubuntulinux.nl dapper-seveas Release
Hit http://kubuntu.org dapper/main Sources
Hit ftp://cipherfunk.org dapper Release
Err ftp://cipherfunk.org dapper Release

Get:21 http://us.archive.ubuntu.com dapper/main Packages [619kB]
Get:22 ftp://cipherfunk.org dapper Release [1387B]
Hit ftp://ftp.free.fr dapper/free Sources
Hit http://mirror3.ubuntulinux.nl dapper-seveas/all Sources
Get:23 http://security.ubuntu.com dapper-security/main Packages [2616B]
Hit ftp://ftp.free.fr dapper/non-free Sources
Ign ftp://cipherfunk.org dapper Release
Get:24 http://security.ubuntu.com dapper-security/restricted Packages [14B]
Get:25 http://security.ubuntu.com dapper-security/main Sources [1015B]
Get:26 http://security.ubuntu.com dapper-security/restricted Sources [14B]
Get:27 http://security.ubuntu.com dapper-security/universe Packages [868B]
Get:28 http://security.ubuntu.com dapper-security/multiverse Packages [14B]
Get:29 http://security.ubuntu.com dapper-security/universe Sources [14B]
Get:30 http://security.ubuntu.com dapper-security/multiverse Sources [14B]
Get:31 ftp://cipherfunk.org dapper/main Packages
Ign ftp://cipherfunk.org dapper/main Packages
Get:32 ftp://cipherfunk.org dapper/main Sources
Get:33 http://us.archive.ubuntu.com dapper/restricted Packages [4571B]
Hit http://us.archive.ubuntu.com dapper/main Sources
Get:34 http://us.archive.ubuntu.com dapper/restricted Sources [1478B]
Get:35 http://us.archive.ubuntu.com dapper/universe Packages [2458kB]
Ign ftp://cipherfunk.org dapper/main Sources
Hit ftp://cipherfunk.org dapper/main Packages
Hit ftp://cipherfunk.org dapper/main Sources
Get:36 http://us.archive.ubuntu.com dapper/multiverse Packages [95.2kB]
Get:37 http://us.archive.ubuntu.com dapper/universe Sources [975kB]
Get:38 http://us.archive.ubuntu.com dapper/multiverse Sources [46.6kB]
Get:39 http://us.archive.ubuntu.com dapper-updates/main Packages [10.2kB]
Get:40 http://us.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:41 http://us.archive.ubuntu.com dapper-updates/main Sources [5153B]
Get:42 http://us.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:43 http://us.archive.ubuntu.com dapper-updates/universe Packages [3267B]
Get:44 http://us.archive.ubuntu.com dapper-updates/multiverse Packages [14B]
Get:45 http://us.archive.ubuntu.com dapper-updates/universe Sources [1628B]
Get:46 http://us.archive.ubuntu.com dapper-updates/multiverse Sources [14B]
Fetched 4300kB in 26s (161kB/s)
W: GPG error: http://kubuntu.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: http://kubuntu.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: GPG error: http://mirror.ubuntulinux.nl dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: http://mirror3.ubuntulinux.nl dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: ftp://cipherfunk.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

```

From what I can gather there, all it's fetching is the gpg keys, but not much else.  I got my sources.list from the list generator on the ubuntu site, because all my sources were pointing to australian domains(i think, they started with au.blah blah.).

---

### Post by taurus on 2006-06-08
You have a couple sites you probably need to comment out by placing a # in front since they gave you an error message...

[http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas Release
[ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release

Then, run "sudo apt-get update" again...

---

### Post by highslime on 2006-06-08
most excellent. i had to add in the keys for the kubuntu sources, and now i run sudo apt-get update with no problems, and now adept comes up with no error messages, thanks for your help! :D

---

### Post by taurus on 2006-06-08
Glad to hear that you have finally resolved your problem.  =D> 

Good luck.

---

### Post by highslime on 2006-06-08
Or not.

```
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 
```

adlkfja;slkjfslakjflask;jflk;asjfl;asjdf;asljf

---

### Post by taurus on 2006-06-08
[QUOTE=highslime]Or not.

```
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 
```

adlkfja;slkjfslakjflask;jflk;asjfl;asjdf;asljf[/QUOTE]
What command did you run before you got that message and what packages are we talking here?

---

### Post by highslime on 2006-06-08
my bad, i should have included that.  i was just trying to install the w32codecs so i can play my mp3's, and was trying to do it through adept.  it's odd, as i'm replying, running apt-get install w32codecs in konsole gives me no problems whatsoever.  everything worked fine from the terminal, and it even finished doing the java thing.  i guess the message shows up when a package is being installed but is cancelled out and remains unresolved?  adept seems to be working fine now, i installed znes(snes emu) in adept rather than console, and everything went off like it's supposed to.

EDIT: maybe there should be a warning about installing the jre through adept, because you can't hit OK at the license agreement to continue(at least i haven't figured out how, if you can).

---

