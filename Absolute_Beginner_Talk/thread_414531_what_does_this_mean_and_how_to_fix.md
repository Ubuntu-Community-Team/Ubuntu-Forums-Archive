---
title: "what does this mean and how to fix?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by DreamcastJack on 2007-04-19
> Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package frostwire needs to be reinstalled, but I can't find an archive for it.'

how do I fix this?!?!?!

---

### Post by DreamcastJack on 2007-04-19
help please. tried installing frostwire from there website..and now this happens when I do anything w/ Package manager

---

### Post by Pobega on 2007-04-19
When do you get this error message?

Is Frostwire installed?

It looks like one of the Ubuntu devs borked some type of dependency, and now it messed up your system (Not permanently, of course. The genius design behind dpkg/apt enables you to easily fix it). We just need a bit more information before we can help you.

---

### Post by DreamcastJack on 2007-04-19
I tried to install frostwire (.deb) but it got a error. now when i click on package manager it tells me to run package manger to see what the error is, and thast what I get. I would reinstall it if I could. but it wont let me.. anyone know how to reinstall frostwire through apt-get?  i dunno what to do.

---

### Post by DreamcastJack on 2007-04-19
when i try to unistall this pops up.

E: The package frostwire needs to be reinstalled, but I can't find an archive for it.

---

### Post by RomeReactor on 2007-04-19
Hi. If you still have .deb package you downloaded from their site, double click on it (it will open with GDEBI) and try reinstalling it or removing it from there. If you don't have it anymore, download it again.

---

### Post by DreamcastJack on 2007-04-20
i have the .deb but when I try to open it it says >  could not open "frostwire-4.13.1.7.i586.deb"
the package might be corrupt or you are not allowed to open file. check the permissions of the file.

I dunno I redownloaded it and everything.

---

### Post by lamalex on 2007-04-20
try setting permissions to 777
```

sudo chmod 777 <name of package>

```

---

### Post by DreamcastJack on 2007-04-20
> **Iamalex said:**
> try setting permissions to 777
```

sudo chmod 777 <name of package>

```

no good, same thing.

---

### Post by Ripfox on 2007-04-20
I had this problem and it was due to installing a debian  package that wasn't Ubuntu specific...can't recall what exactly I found to fix it, but it was a one command in the terminal...I will keep looking.

---

### Post by Ripfox on 2007-04-20
This was a lead I had started with when it happened to me...

[http://ubuntuforums.org/showthread.php?p=2198294](http://ubuntuforums.org/showthread.php?p=2198294)

I think I followed a few posts from that post to solve it...sorry I don't have more time to look.

Good luck!

---

### Post by DreamcastJack on 2007-04-20
i didnt get any of that to work.

---

### Post by DreamcastJack on 2007-04-20
anyone?

---

### Post by llamakc on 2007-04-20
You could try installing it with sudo. You understand that only administrators (root or users with root privileges) can install packages outside of /home/YOURUSERNAME right?

---

### Post by Pobega on 2007-04-20
dpkg -r frostwire.deb
**or**
apt-get remove --purge frostwire

---

### Post by llamakc on 2007-04-20
[http://www.frostwire.com/download.php?os=ubuntu](http://www.frostwire.com/download.php?os=ubuntu)

I let the gdebi installer run for me and it installed perfectly.

---

### Post by DreamcastJack on 2007-04-20
none of taht worked.. looks like a full reinstall..yay..not

---

### Post by llamakc on 2007-04-20
Full reinstall of what? Why would you reinstall an operating system because installation of a package messed up?

Are you on Feisty or Edgy? Open a terminal and type:

sudo apt-get -f install

AND paste the output of that in here.

---

### Post by llamakc on 2007-04-20
You have a process locking up dpkg. Open a terminal and type:

ps aux

paste all of that stuff in here.

---

### Post by DreamcastJack on 2007-04-20
> sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package frostwire needs to be reinstalled, but I can't find an archive for it.
dreamcastjack@DCJack:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.7  0.2   2908  1844 ?        Ss   00:59   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    00:59   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   00:59   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    00:59   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   00:59   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   00:59   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   00:59   0:00 [kthread]
root        30  0.0  0.0      0     0 ?        S<   00:59   0:00 [kblockd/0]
root        31  0.0  0.0      0     0 ?        S<   00:59   0:00 [kacpid]
root        32  0.0  0.0      0     0 ?        S<   00:59   0:00 [kacpi_notify]
root       174  0.0  0.0      0     0 ?        S<   00:59   0:00 [kseriod]
root       199  0.0  0.0      0     0 ?        S    00:59   0:00 [pdflush]
root       200  0.0  0.0      0     0 ?        S    00:59   0:00 [pdflush]
root       201  0.0  0.0      0     0 ?        S<   00:59   0:00 [kswapd0]
root       202  0.0  0.0      0     0 ?        S<   00:59   0:00 [aio/0]
root      2027  0.0  0.0      0     0 ?        S<   00:59   0:00 [ksuspend_usbd]
root      2028  0.0  0.0      0     0 ?        S<   00:59   0:00 [khubd]
root      2042  0.0  0.0      0     0 ?        S<   00:59   0:00 [ata/0]
root      2043  0.0  0.0      0     0 ?        S<   00:59   0:00 [ata_aux]
root      2149  0.0  0.0      0     0 ?        S<   00:59   0:00 [scsi_eh_0]
root      2150  0.0  0.0      0     0 ?        S<   00:59   0:00 [scsi_eh_1]
root      2402  0.0  0.0      0     0 ?        S<   00:59   0:00 [kjournald]
root      2601  0.1  0.1   2916  1260 ?        S<s  00:59   0:00 /sbin/udevd --d
root      3483  0.0  0.0      0     0 ?        S<   00:59   0:00 [kpsmoused]
root      4180  0.0  0.0   1652   508 tty4     Ss+  01:00   0:00 /sbin/getty 384
root      4181  0.0  0.0   1652   512 tty5     Ss+  01:00   0:00 /sbin/getty 384
root      4183  0.0  0.0   1648   504 tty2     Ss+  01:00   0:00 /sbin/getty 384
root      4187  0.0  0.0   1648   504 tty3     Ss+  01:00   0:00 /sbin/getty 384
root      4188  0.0  0.0   1648   508 tty1     Ss+  01:00   0:00 /sbin/getty 384
root      4189  0.0  0.0   1652   512 tty6     Ss+  01:00   0:00 /sbin/getty 384
root      4433  0.0  0.1   2256  1172 ?        Ss   01:00   0:00 /usr/sbin/acpid
root      4527  0.0  0.0   1700   640 ?        Ss   01:00   0:00 /sbin/syslogd
root      4583  0.0  0.0   1796   528 ?        Ss   01:00   0:00 /bin/dd bs 1 if
klog      4585  0.0  0.1   2428  1372 ?        Ss   01:00   0:00 /sbin/klogd -P
103       4606  0.0  0.1   2852  1056 ?        Ss   01:00   0:00 /usr/bin/dbus-d
107       4622  1.6  1.1  10284  8608 ?        Ss   01:00   0:02 /usr/sbin/hald
root      4623  0.0  0.1   2872  1020 ?        S    01:00   0:00 hald-runner
107       4629  0.0  0.1   2100   888 ?        S    01:00   0:00 hald-addon-acpi
root      4630  0.0  0.1   2928  1092 ?        S    01:00   0:00 /usr/lib/hal/ha
107       4637  0.0  0.1   2100   904 ?        S    01:00   0:00 hald-addon-keyb
107       4646  0.0  0.1   2096   896 ?        S    01:00   0:00 hald-addon-keyb
107       4649  0.0  0.1   2096   896 ?        S    01:00   0:00 hald-addon-keyb
107       4652  0.0  0.1   2100   900 ?        S    01:00   0:00 hald-addon-keyb
107       4664  0.0  0.1   2100   908 ?        S    01:00   0:00 hald-addon-stor
root      4677  0.0  0.1   1940   844 ?        Ss   01:00   0:00 /usr/sbin/dhcdb
root      4692  0.0  0.2  12320  1956 ?        Ssl  01:00   0:00 /usr/sbin/Netwo
avahi     4710  0.0  0.1   2664  1356 ?        Ss   01:00   0:00 avahi-daemon: r
avahi     4711  0.0  0.0   2664   460 ?        Ss   01:00   0:00 avahi-daemon: c
root      4727  0.0  0.1   3056  1268 ?        Ss   01:00   0:00 /usr/sbin/Netwo
root      4740  0.0  0.1   2868   804 ?        Ss   01:00   0:00 /usr/bin/system
root      4741  0.0  0.1   2716  1220 ?        S    01:00   0:00 dbus-daemon --s
root      4773  0.0  0.1  12216  1408 ?        Ss   01:00   0:00 /usr/sbin/gdm
root      4774  0.0  0.3  12576  2396 ?        S    01:00   0:00 /usr/sbin/gdm
root      4779  3.6  3.3  31752 25756 tty7     SLs+ 01:00   0:04 /usr/X11R6/bin/
dhcp      4803  0.0  0.1   2456  1216 ?        S    01:00   0:00 /sbin/dhclient
cupsys    4843  0.0  0.2   4680  1872 ?        Ss   01:00   0:00 /usr/sbin/cupsd
root      4867  0.0  0.1   6416   840 ?        Ss   01:00   0:00 /usr/sbin/hpiod
hplip     4875  0.0  0.6   9984  4888 ?        S    01:00   0:00 python /usr/sbi
root      4937  0.0  0.0      0     0 ?        S<   01:00   0:00 [kondemand/0]
root      4974  0.0  0.1   2692  1000 ?        Ss   01:00   0:00 /usr/sbin/hcid
root      4991  0.0  0.0      0     0 ?        S<   01:00   0:00 [krfcommd]
root      5012  0.0  0.0   1648   620 ?        Ss   01:00   0:00 /usr/sbin/anacr
daemon    5026  0.0  0.0   1908   420 ?        Ss   01:00   0:00 /usr/sbin/atd
root      5040  0.0  0.1   2284   900 ?        Ss   01:00   0:00 /usr/sbin/cron
1000      5184  0.2  1.4  30072 11084 ?        Ssl  01:00   0:00 x-session-manag
1000      5224  0.0  0.0   4252   532 ?        Ss   01:00   0:00 /usr/bin/ssh-ag
1000      5227  0.0  0.0   2660   640 ?        S    01:00   0:00 /usr/bin/dbus-l
1000      5228  0.0  0.1   2720   992 ?        Ss   01:00   0:00 /usr/bin/dbus-d
1000      5230  0.6  0.5   6588  4128 ?        S    01:00   0:00 /usr/lib/libgco
1000      5233  0.0  0.1   2752  1000 ?        S    01:00   0:00 /usr/bin/gnome-
1000      5235  0.2  1.2  29528  9960 ?        Sl   01:00   0:00 /usr/lib/contro
1000      5242  0.0  0.0   1712   480 ?        Ss   01:00   0:00 /bin/sh -c /usr
1000      5243  0.0  0.4   4960  3320 ?        S    01:00   0:00 /usr/bin/esd -t
1000      5247  0.2  1.1  15724  8580 ?        S    01:00   0:00 /usr/bin/metaci
1000      5250  0.9  2.4  61024 19120 ?        S    01:00   0:01 gnome-panel --s
1000      5253  0.5  2.3  95012 18428 ?        S    01:00   0:00 nautilus --no-d
1000      5259  0.2  0.4  39588  3104 ?        Ssl  01:00   0:00 /usr/lib/bonobo
1000      5262  0.0  0.4   8460  3312 ?        S    01:00   0:00 /usr/lib/gnome-
1000      5263  0.0  0.6  18824  4756 ?        Ss   01:00   0:00 gnome-volume-ma
1000      5267  0.1  1.5  51288 12216 ?        S    01:00   0:00 update-notifier
1000      5269  0.0  1.2  26808  9340 ?        Sl   01:00   0:00 /usr/lib/evolut
1000      5271  0.1  1.3  48572 10332 ?        S    01:00   0:00 nm-applet --sm-
1000      5272  0.0  0.7  48472  5880 ?        Ss   01:00   0:00 gnome-power-man
1000      5273  0.0  1.0  56324  8136 ?        S    01:00   0:00 gnome-cups-icon
1000      5298  0.0  1.1  81356  8800 ?        S    01:00   0:00 /usr/lib/gnome-
1000      5311  0.0  0.1   2456   884 ?        S    01:00   0:00 /usr/lib/nautil
1000      5332  0.1  1.5  52032 12356 ?        S    01:00   0:00 /usr/lib/gnome-
1000      5344  8.6  5.4 151888 42220 ?        Sl   01:00   0:06 /usr/lib/firefo
1000      5348  0.2  0.2  15896  2260 ?        Ss   01:00   0:00 gnome-screensav
1000      5366  2.7  5.7 134200 44908 ?        Sl   01:00   0:01 amarokapp
1000      5373  0.0  0.7  25600  5792 ?        Ss   01:01   0:00 kdeinit Running
1000      5378  0.0  0.6  25312  4792 ?        S    01:01   0:00 dcopserver [kde
1000      5381  0.0  0.8  25788  6492 ?        S    01:01   0:00 klauncher [kdei
1000      5383  0.1  1.3  27816 10120 ?        S    01:01   0:00 kded [kdeinit]
1000      5400  0.0  0.9  26452  7432 ?        S    01:01   0:00 kio_file [kdein
1000      5401  0.0  0.9  26364  7376 ?        S    01:01   0:00 kio_file [kdein
1000      5402  0.0  0.3   3860  2372 ?        S    01:01   0:00 ruby /usr/share
1000      5405  0.0  0.9  26152  7104 ?        S    01:01   0:00 kio_file [kdein
1000      5406  0.0  0.9  26152  7112 ?        S    01:01   0:00 kio_file [kdein
1000      5417  1.2  2.0  73960 15740 ?        Sl   01:01   0:00 gnome-terminal
1000      5419  0.0  0.0   2460   728 ?        S    01:01   0:00 gnome-pty-helpe
1000      5420  0.5  0.4   5620  3140 pts/0    Ss   01:01   0:00 bash
1000      5450  0.0  0.1   2564   996 pts/0    R+   01:02   0:00 ps aux


thats what I get

---

### Post by DreamcastJack on 2007-04-20
this is driving me insane!

---

### Post by Spinelli on 2007-04-20
> **DreamcastJack said:**
> how do I fix this?!?!?!

How are you trying to install it? Are you using synaptic or did you just download the .deb file from the internet?

To install a .deb you should type this:
```
sudo dpkg -i frostwire-xxx.deb
```

I am running the Feisty live CD with universe and multiverse enabled and I can't find a frostwire package in the repositories, so I am assuming you downloaded the .deb from somewhere on the internet. You might want to tell us what version of frostwire you are trying to install.

---

### Post by DreamcastJack on 2007-04-20
> **Spinelli said:**
> How are you trying to install it? Are you using synaptic or did you just download the .deb file from the internet?

To install a .deb you should type this:
```
sudo dpkg -i frostwire-xxx.deb
```

I am running the Feisty live CD with universe and multiverse enabled and I can't find a frostwire package in the repositories, so I am assuming you downloaded the .deb from somewhere on the internet. You might want to tell us what version of frostwire you are trying to install.

you just saved my life..and taht was so easy to fix..THANK YOU!!!

---

### Post by Spinelli on 2007-04-20
I'm glad I could help. Don't forget to read the man pages.

```
man dpkg
man apt-get
man apt-cache
```

---

### Post by DreamcastJack on 2007-04-20
> **Spinelli said:**
> I'm glad I could help. Don't forget to read the man pages.

```
man dpkg
man apt-get
man apt-cache
```

will save those commands and read through those. thank you very much!

---

