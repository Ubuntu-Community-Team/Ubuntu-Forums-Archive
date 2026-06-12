---
title: "Xubuntu crashes 5-10 times a day"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by vaazu on 2006-08-16
It all started when I entered```
sudo apt-get install xfce4-mount-plugin
```into my terminal. The computer was very overhelmed by another processes and it crashed. After I pressed reset button it said disk boot failure and asked xubuntu cd. I did memtest it lasted for 3 hours and I think it repeated its doings. Then I found out that only way to start the machine again was to turn power off and then start it. I just want to now is there any way I could fix this problem, how to find the problem etc. I just don´t know what to do, only think I could think of was going to synaptic and look for proken packages and remove the mount plugin and install it again.

---

### Post by encompass on 2006-08-16
Sounds liek your not using a lot of memory.
you can do it in text mode.  ```
sudo apt-get remove PACKAGE
``` then ```
sudo apt-get install PACKAGE
``` That MAY fix your problem.  It uses alot let ram to do that then synaptic.

---

### Post by vaazu on 2006-08-16
If you mean ```
sudo apt-get remove xfce4-mount plugin 
sudo apt-get install xfce4-mount plugin

```into the terminal then I have tried that.

---

### Post by vaazu on 2006-08-16
bump
really need help

---

### Post by vaazu on 2006-08-16
anyone?

---

### Post by encompass on 2006-08-16
Pantients dude...
Well if this happens to you every time you try to run something as simple as apt-get I guess we need to find the nasty program that is bugging you.
try running a program called top
it should tellyou what program is taking all you resources.
For details on how to run it type man top.
What program is it.  Report on back.

---

### Post by vaazu on 2006-08-16
it showed me that my memory is very low :|```
top - 21:48:51 up 21 min,  3 users,  load average: 0.28, 0.38, 0.42
Tasks:  69 total,   1 running,  68 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.2% us,  1.0% sy,  0.0% ni, 91.0% id,  0.0% wa,  0.2% hi,  5.5% si
Mem:    256252k total,   251524k used,     4728k free,     1532k buffers
Swap:   746980k total,    19328k used,   727652k free,    74316k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4233 root      15   0 40100  27m 7600 S  2.2 10.9   0:47.44 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 4894 vahur     15   0  412m  91m  26m S  1.0 36.6   0:50.83 java -Xms16m -Xmx128m -cp /home/vahur/azureus/Azureus2.jar:/home/vahur/azureus/swt.jar -Djava.library.pat 4870 vahur     15   0 47744  13m 7884 S  0.4  5.5   0:11.79 /usr/bin/Terminal -x /home/vahur/azureus/azureus
 4683 vahur     15   0  5128 2200 1676 S  0.2  0.9   0:00.29 xscreensaver -no-splash
    1 root      16   0  1564  528  460 S  0.0  0.2   0:01.80 init [2]
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 [ksoftirqd/0]
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 [watchdog/0]
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 [events/0]
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 [khelper]
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [kthread]
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 [kblockd/0]
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 [kacpid]
  112 root      15   0     0    0    0 S  0.0  0.0   0:00.00 [pdflush]
  113 root      15   0     0    0    0 S  0.0  0.0   0:00.00 [pdflush]
  115 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 [aio/0]
  114 root      15   0     0    0    0 S  0.0  0.0   0:00.09 [kswapd0]
  702 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [kseriod]
 1803 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 [khubd]
 1891 root      15   0     0    0    0 S  0.0  0.0   0:00.01 [kjournald]
 2117 root      16  -4  2108  548  368 S  0.0  0.2   0:00.50 /sbin/udevd --daemon
 2915 root      20   0     0    0    0 S  0.0  0.0   0:00.00 [shpchpd_event]
 2984 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 [kgameportd]
 3008 root      15   0     0    0    0 S  0.0  0.0   0:00.00 [pccardd]
 3779 root      16   0  2152 1188  640 S  0.0  0.5   0:00.00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 3869 syslog    16   0  1764  668  548 S  0.0  0.3   0:00.01 /sbin/syslogd -u syslog
 3895 root      15   0  1680  496  412 S  0.0  0.2   0:00.01 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 3897 klog      17   0  2412 1336  388 S  0.0  0.5   0:00.10 /sbin/klogd -P /var/run/klogd/kmsg
 4216 root      15   0 10912 1776 1208 S  0.0  0.7   0:00.00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
 4223 root      16   0 11264 2496 1868 S  0.0  1.0   0:00.03 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
 4255 hplip     16   0 12872  804  688 S  0.0  0.3   0:00.00 /usr/sbin/hpiod
 4262 hplip     15   0  9412 4416 1084 S  0.0  1.7   0:00.03 python /usr/sbin/hpssd
 4309 cupsys    16   0  4196 1664 1224 S  0.0  0.6   0:00.01 /usr/sbin/cupsd
 4334 messageb  17   0  2192  776  660 S  0.0  0.3   0:00.00 /usr/bin/dbus-daemon --system
 4349 haldaemo  16   0  6796 5368 1556 S  0.0  2.1   0:00.91 /usr/sbin/hald
 4350 root      16   0  2716  972  836 S  0.0  0.4   0:00.04 hald-runner
 4355 haldaemo  16   0  2000  792  696 S  0.0  0.3   0:00.00 /usr/lib/hal/hald-addon-acpi
 4409 haldaemo  15   0  2000  788  692 S  0.0  0.3   0:00.01 /usr/lib/hal/hald-addon-keyboard
 4422 haldaemo  16   0  2008  860  760 S  0.0  0.3   0:00.18 /usr/lib/hal/hald-addon-storage
 4423 haldaemo  16   0  2004  816  716 S  0.0  0.3   0:00.22 /usr/lib/hal/hald-addon-storage
 4492 root      16   0  1628  300  232 S  0.0  0.1   0:00.00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
 4523 daemon    20   0  1796  392  296 S  0.0  0.2   0:00.00 /usr/sbin/atd
 4536 root      16   0  2120  840  680 S  0.0  0.3   0:00.00 /usr/sbin/cron
 4619 root      16   0  1560  492  424 S  0.0  0.2   0:00.00 /sbin/getty 38400 tty1
 4620 root      16   0  1564  496  424 S  0.0  0.2   0:00.00 /sbin/getty 38400 tty2
 4621 root      16   0  1560  492  424 S  0.0  0.2   0:00.00 /sbin/getty 38400 tty3
 4622 root      16   0  1564  496  424 S  0.0  0.2   0:00.00 /sbin/getty 38400 tty4
 4623 root      16   0  1560  492  424 S  0.0  0.2   0:00.00 /sbin/getty 38400 tty5
 4624 root      16   0  1560  492  424 S  0.0  0.2   0:00.00 /sbin/getty 38400 tty6
 4637 vahur     23   0  4164 1636 1040 S  0.0  0.6   0:00.06 /bin/sh /etc/xdg/xfce4/xinitrc
 4674 vahur     16   0  4328  688  444 S  0.0  0.3   0:00.00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session startxfce4
 4677 vahur     16   0  2708  644  520 S  0.0  0.3   0:00.00 /usr/bin/dbus-launch --exit-with-session startxfce4
 4678 vahur     15   0  2188  884  756 S  0.0  0.3   0:00.00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
 4682 vahur     19   0  4160  932  336 S  0.0  0.4   0:00.00 /bin/sh /etc/xdg/xfce4/xinitrc
 4683 vahur     16   0  5128 2200 1676 S  0.0  0.9   0:00.28 xscreensaver -no-splash
 4686 vahur     16   0 33076 5736 4168 S  0.0  2.2   0:00.45 /usr/bin/xfce4-session

```

---

### Post by vaazu on 2006-08-17
OK
then is it possible to reinstall xubuntu and save my files like home directory? and if it is, is there a chanche that it will save some programs or etc, that my problems won´t go away?

---

### Post by encompass on 2006-08-17
get rid of java... that was my problem... I hate java for that very reason...  How every your running it... stop.  What programs do you use... are using java?

---

### Post by siacs on 2006-08-17
it's Azureus, surprise surprise

---

### Post by dannyboy79 on 2006-08-17
I would have to agree, if you are downloading torrents, you should use bittornado. it is easy to use, very fast, not nearly memory intensive as java based torrent program like azureus. Also, if you installed Xubuntu, why do you have all those "K" process sleeping. Did you install a bunch of programs that are for the KDE desktop environment. That's another reason why your computer slowed down tons. You need to look for applications that are actually for Xubuntu, not just go to synaptic and install any gnome or kde app you want. Anyway, I have Xubuntu and it screams on a Pentium MMX 266mhz with 128MB ram so. I haven't installed anything KDE and very little gnome stuff. Hope you get it figured out. Sorry I could be more help.

---

### Post by encompass on 2006-08-17
So what are you going to do?
If you need memory kill the process with the k button in top and type the PID and press enter. kinda crude but gets rid of it.

---

### Post by vaazu on 2006-08-17
ok thanks for help, but could anyone tell me how to use bittornado 0.3.15. I downloaded a file froma [https://launchpad.net/distros/ubuntu/+source/bittornado/0.3.15-2ubuntu1](https://launchpad.net/distros/ubuntu/+source/bittornado/0.3.15-2ubuntu1) because in synaptic there was only available version 0.3.13 and I need 0.3.15 because its not banned on the site I want to download. How can I get it working like the on that I downloaded from synaptic?

---

### Post by encompass on 2006-08-17
Why would they ban a bittorrent program... sounds like a magor download location.  What are you getting?
For the answer to your question... you can download the source and do it yourself.  Find the site by googling the product title.  Odds are the first link.
HIT: you can just type most things like gmail in the addressbar of firefox and it uses the I'm feeling lucky link to take you to the first result of a google search as the webpage.  try it out.

---

### Post by GeekSpeek'r on 2006-08-17
Do me a favor before you ditch..

do: 
top

within top do <ctrl> m

and post it

this will show us the memory hog

---

### Post by vaazu on 2006-08-18
> **GeekSpeek'r said:**
> Do me a favor before you ditch..

do: 
top

within top do <ctrl> m

and post it

this will show us the memory hog
```
top - 16:49:17 up 2 min,  2 users,  load average: 0.55, 0.42, 0.17
Tasks:  66 total,   1 running,  65 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.2% us,  0.0% sy,  0.0% ni, 96.8% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    256252k total,   201660k used,    54592k free,     4600k buffers
Swap:   746980k total,        0k used,   746980k free,   120252k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4247 root      15   0 29900  17m 6588 S  1.6  7.1   0:05.61 Xorg
 4806 vahur     15   0 47280  12m 7496 S  0.8  5.1   0:00.66 Terminal
 4826 vahur     16   0  2192 1080  856 R  0.8  0.4   0:00.01 top
    1 root      15   0  1568  532  460 S  0.0  0.2   0:01.83 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.10 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  112 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  113 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  115 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  114 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  702 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1803 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd

```

---

### Post by Thirsteh on 2006-08-18
Vaazu, it seems to me like you've neglected to mention the two most important things about this issue;

1. You say Xubuntu crashes 5-10 times every day, how does X/Xubuntu crash? Does X merely crash to console?
2. What are the contents of your Xorg logfile after a crash?

X.org or Ubuntu doesn't crash by running out of physical memory, hence the very existence of so-called "virtual" memory, also called swap. You have almost 800 megs of Swap space, and Ubuntu hasn't used a single byte, which means memory is not an issue. Linux handles memory in a different way than other operating systems -- having it say that 511mb of your 512mb RAM are in use is not (necessarily) a bad thing, similar to "Idle System Process" using 99% CPU in Windows.

---

### Post by orb9220 on 2006-08-18
Thirsteh might be on to something there. In what I have read in the forums constant crashes are related to two things.

Graphic drivers with ati topping the list of bugs and trying to use 868-smp and 64bit kernels which people became happy campers again after solving graphic card woes or rolling back to 386 kernel.

---

### Post by vaazu on 2006-08-18
1. The screen just freezes and goes black, the half bottom of the screen will go to little boxes with dfferent colours.
2. Do you mean xorg.conf? and what should i look for there after crash?
I dont have an ATI card, it´s nvidia.

---

### Post by Metacarpal on 2006-08-18
Are you by any chance connecting using a wireless card?

I'm running Ubuntu/gnome, and I have found that if I'm downloading a torrent - regardless of which client I use - and I try to access the 'net to do ANYTHING else, including checking email and downloading updates, my X session crashes after a random interval (sometimes 10 minutes, sometimes immediately).  For some reason, torrents don't play well with others over wireless...

---

### Post by vaazu on 2006-08-18
yes I am, but does this mean that if I want to use torrents I can´t use ubuntu?

---

### Post by Metacarpal on 2006-08-18
> **vaazu said:**
> yes I am, but does this mean that if I want to use torrents I can´t use ubuntu?

Doesn't mean you can't use Ubuntu, you just can't do anything else on the 'net while downloading the torrent. :( Kinda sucks, I know.

I recently updated my kernel (the core of Linux) to a version which is supposed to have better wireless support.  I've not tried torrenting since then...  I'll give it a try tonight and let you know what happens.

Unless the new kernel fixes the problem, the options are either to do torrents when not otherwise using the 'net (like when you're asleep), or connect to an ethernet line.

---

### Post by vaazu on 2006-08-18
OK, let me know what happens.

---

### Post by Thirsteh on 2006-08-18
> **vaazu said:**
> 1. The screen just freezes and goes black, the half bottom of the screen will go to little boxes with dfferent colours.

There is a very large chance that there is a problem with your NVIDIA card or your NVIDIA drivers. Try re-installing the drivers, check if the fan on the card is running, et cetera.

And no, sorry I wasn't specific enough, I meant the X.org logfile in /var/log/ -- I can't tell you the exact name because I don't remember, and I don't have access to a Linux machine at the moment.

---

### Post by Metacarpal on 2006-08-18
> **vaazu said:**
> OK, let me know what happens.

No joy.  Still freezes.

---

### Post by vaazu on 2006-08-19
I don´t think that the problem is in my nvidia frivers because it hasnt freezed once after removing torrent programs. I really need to use torrents while doing other things in web so I think i´ll try Debian.

---

### Post by Metacarpal on 2006-08-20
Best of luck to you!

If the torrents work under regular Debian, please let me know.  That would indicate that it's an Ubuntu-specific bug, which might help the devs track it down.

Thanks!

---

