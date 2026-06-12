---
title: "Is Ubuntu supposed to be clunky?"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by MNOB07 on 2006-05-16
P3 1Ghz
256MB RAM
Integrated SiS video and audio

The computer is running very slow... I was expecting close to Windows 2000 performance or better... but this isn't. Possible that something funky is up such as the harddrive in PIO mode? I don't know how I would check for that kind of thing though.

---

### Post by Popcorn on 2006-05-16
1 GHZ processor isn't doing you any good. I myself set the system down to 256Mb Ram and it runs smooth with a fresh install for me. 

Matt

---

### Post by Lord Illidan on 2006-05-16
[quote=MNOB07]P3 1Ghz
256MB RAM
Integrated SiS video and audio

The computer is running very slow... I was expecting close to Windows 2000 performance or better... but this isn't. Possible that something funky is up such as the harddrive in PIO mode? I don't know how I would check for that kind of thing though.[/quote]

To check for DMA/PIO...

run ```
sudo hdparm /dev/hd*
```

To enable it:
```
sudo hdparm -d1 /dev/hda
``` or hdb,hdc,hdd - depends on your system.

You might want to use XFCE instead of gnome.

```
sudo apt-get install xubuntu-desktop
```

---

### Post by MNOB07 on 2006-05-16
what was that last command supposed to do?

I just got this:

E: Couldn't find package xubuntu-desktop

---

### Post by Jagot on 2006-05-16
The last command installs Xubuntu, which uses XFCE rather than GNOME and requires less resources, thus running better on older systems.  It is in the universe repository which you may need to enable, which is why you're getting the error message.  You can find instructions here:

[http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse](http://help.ubuntu.com/starterguide/C/ch02.html#addinguniverse)
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by Sef on 2006-05-16
Try upping the ram.  I have a P3 1.3 celeron with 512 memory, and it is fast.

---

### Post by az on 2006-05-16
[QUOTE=MNOB07] I was expecting close to Windows 2000 performance or better... but this isn't. [/QUOTE]

Ubuntu beats windows XP most of the time, but windows 2000 is somewhat faster than XP.

---

### Post by kane77 on 2006-05-17
I'm running ubuntu on AMD Duron 1 GHz, 256MB RAM and it's working fine (certainly faster than winXP) even with many gdesklets installed...

---

### Post by azmansell on 2006-05-17
Im running ubuntu on a celeron 733, with 256mb ram, onboard video (as i cant get the voodoo 3 working) and a 10gb harddrive!

beat that!!!

it does run a little clunky but no more than XP (cough) did. Im just saving to upgrade now, i will definiately be keeeping ubuntu though!

---

### Post by azmansell on 2006-05-17
[QUOTE=Lord Illidan]To check for DMA/PIO...

run ```
sudo hdparm /dev/hd*
```

To enable it:
```
sudo hdparm -d1 /dev/hda
``` or hdb,hdc,hdd - depends on your system.

You might want to use XFCE instead of gnome.

```
sudo apt-get install xubuntu-desktop
```[/QUOTE]

Ive installed xubuntu desktop and rebooted but the gnome desktop is still coming up? do i need to do more?

cheers in advance

---

### Post by Jagot on 2006-05-17
[QUOTE=azmansell]Ive installed xubuntu desktop and rebooted but the gnome desktop is still coming up? do i need to do more?[/QUOTE]

At the gdm log in screen there should be a menu called 'Session' just below where you enter your username/password.  Click that and it will allow you to select Xubuntu, or it may just be labelled as XFCE - can't remember.  Then log in as normal.

---

### Post by jethro10 on 2006-05-17
[QUOTE=Sef]Try upping the ram.  I have a P3 1.3 celeron with 512 memory, and it is fast.[/QUOTE]
I would concur.
I had a 2.6Ghz processor with 256Mb memory and it was a dog.
512Mb saved the day, perhaps 5 times as quick, maybe more. The memory monitor shows 300-400Mb in use most of the time.

1Gb memory has made no discernable difference from 512Mb 

Jeff

---

### Post by azmansell on 2006-05-17
[QUOTE=Jagot]At the gdm log in screen there should be a menu called 'Session' just below where you enter your username/password.  Click that and it will allow you to select Xubuntu, or it may just be labelled as XFCE - can't remember.  Then log in as normal.[/QUOTE]

cheers, ive got it working now, although there are a couple of problems.

the panel at the bottom wont let me do anything with it, i cant change the desktop background and there is a grey bar across the top which i assume is a panel but dosent do anything or even let me right click on it

any ideas?

---

### Post by dmizer on 2006-05-17
i think there are other issues at work with your machine.  my daily ubuntu laptop is a cranky old nec 1ghz pIII with 256meg of ram and it runs faster than win2000 or xp.

try pasting the output of dmesg ... if you see alot of errors in there, it is likely a source of some of your problem.  it took me a while to sort out all of the little issues that were eating my system resources, but once i got it all worked out, it runs fast enough to use at work daily.

i've used xfce only once or twice and really didn't care for it.  i use icewm at home on a 600mhz pIII laptop.

but again, i think you might be taking a wrong approach to this.  your system should be fine with ubuntu + gnome.

---

### Post by Mustard on 2006-05-17
I'd be curious if a swap partition exists.

---

### Post by perce on 2006-05-17
Ubuntu should be able to run smoothly on your computer: it does on mine which is older. You could check if some program is taking a huge portion of the CPU time or of the memory. Go to a terminal and type
ps aux
then post the output on the forum, maybe someone will help you to understand what's going on. 

To see if you have swap partition (as suggested by Mustard) go to a terminal and type 
cat /proc/swaps

---

### Post by stansz on 2006-05-17
xfce is ugly....lol 

i like icewm better..,(vector) on my old laptop..runs smooth so far..

but nothing beats gnome....kde doesnt come close in my opinon 

but it eats up ram like mad .....so for those less fortunate...then i like icewm over xcfe

---

### Post by azmansell on 2006-05-19
sorry i havent been on for a couple of days...
here are the details of ps aux:

azmansell@ubuntu:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.1  0.1   1560   476 ?        S    10:20   0:02 init [2]
root         2  0.0  0.0      0     0 ?        SN   10:20   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S<   10:20   0:00 [events/0]
root         4  0.0  0.0      0     0 ?        S<   10:20   0:00 [khelper]
root         5  0.0  0.0      0     0 ?        S<   10:20   0:00 [kthread]
root         7  0.0  0.0      0     0 ?        S<   10:20   0:00 [kacpid]
root        69  0.0  0.0      0     0 ?        S<   10:20   0:00 [kblockd/0]
root        95  0.0  0.0      0     0 ?        S    10:20   0:00 [pdflush]
root        96  0.0  0.0      0     0 ?        S    10:20   0:00 [pdflush]
root        98  0.0  0.0      0     0 ?        S<   10:20   0:00 [aio/0]
root        97  0.0  0.0      0     0 ?        S    10:20   0:00 [kswapd0]
root       683  0.0  0.0      0     0 ?        S    10:20   0:00 [kseriod]
root      2293  0.0  0.0      0     0 ?        S    10:20   0:00 [khubd]
root      3795  0.0  0.0      0     0 ?        S    10:20   0:00 [kjournald]
root      3933  0.0  0.1   1656   424 ?        S<s  10:20   0:00 udevd --daemon
root      6556  0.0  0.2   2696   708 ?        Ss   10:21   0:00 pppd call adslsroot      6671  0.0  0.0      0     0 ?        S    10:21   0:00 [kIrDAd]
root      6707  0.0  0.0      0     0 ?        S    10:21   0:00 [kgameportd]
root      7393  0.0  0.2   1820   644 ?        Ss   10:21   0:00 /usr/sbin/acpidsyslog    7408  0.0  0.2   1776   700 ?        Ss   10:21   0:00 /sbin/syslogd -root      7425  0.0  0.1   1556   384 ?        Ss   10:21   0:00 /bin/dd bs 1 ifklog      7427  0.0  0.6   2456  1564 ?        Ss   10:21   0:00 /sbin/klogd -P
105       7440  0.0  0.4   2152  1028 ?        Ss   10:21   0:00 /usr/bin/dbus-dhal       7453  0.0  1.4   5068  3676 ?        Ss   10:21   0:01 /usr/sbin/hald
hal       7458  0.0  0.2   1864   592 ?        S    10:21   0:00 hald-addon-acpihal       7467  0.0  0.2   1868   628 ?        S    10:21   0:00 hald-addon-storhal       7469  0.0  0.2   1864   628 ?        S    10:21   0:00 hald-addon-storcupsys    7500  0.0  1.2   6324  3216 ?        Ss   10:21   0:00 /usr/sbin/cupsdhplip     7523  0.0  0.4  12616  1160 ?        Ssl  10:21   0:00 /usr/sbin/hpiodhplip     7532  0.0  2.0   8852  5260 ?        S    10:21   0:00 python /usr/sbiroot      7737  0.0  0.2   2592   732 ?        Ss   10:21   0:00 /usr/bin/kdm
root      7749 16.9 16.9  56776 43384 ?        S    10:21   4:57 /usr/X11R6/bin/root      7750  0.0  0.3   1920   776 ?        Ss   10:21   0:00 hcid: processinroot      7756  0.0  0.2   1604   516 ?        Ss   10:21   0:00 /usr/sbin/sdpd
root      7762  0.0  0.4   3220  1104 ?        S    10:21   0:00 -:0
root      7767  0.0  0.0      0     0 ?        S<   10:21   0:00 [krfcommd]
daemon    7807  0.0  0.2   1760   620 ?        Ss   10:21   0:00 /usr/sbin/atd
root      7820  0.0  0.2   1824   680 ?        Ss   10:21   0:00 /usr/sbin/cron
root      7857  0.0  0.1   1552   404 tty1     Ss+  10:21   0:00 /sbin/getty 384root      7862  0.0  0.1   1552   404 tty2     Ss+  10:21   0:00 /sbin/getty 384root      7865  0.0  0.1   1552   404 tty3     Ss+  10:21   0:00 /sbin/getty 384root      7868  0.0  0.1   1556   404 tty4     Ss+  10:21   0:00 /sbin/getty 384root      7869  0.0  0.1   1552   404 tty5     Ss+  10:21   0:00 /sbin/getty 384root      7874  0.0  0.1   1552   404 tty6     Ss+  10:21   0:00 /sbin/getty 3841000      7892  0.0  0.2   4144   576 ?        Ss   10:23   0:00 /bin/sh /usr/bi1000      7933  0.0  0.2   3140   720 ?        Ss   10:23   0:00 /usr/bin/ssh-ag1000      7936  0.0  0.2   2572   608 ?        S    10:23   0:00 /usr/bin/dbus-l1000      7937  0.0  0.2   2028   628 ?        Ss   10:23   0:00 dbus-daemon --f1000      7965  0.0  3.3  24648  8672 ?        Ss   10:23   0:00 kdeinit Running1000      7968  0.0  3.1  23840  8100 ?        S    10:23   0:00 dcopserver [kde1000      7970  0.0  3.6  25484  9404 ?        S    10:23   0:00 klauncher [kdei1000      7973  0.3  5.0  29564 12936 ?        S    10:23   0:05 kded [kdeinit]
1000      7975  0.2  0.5   2720  1312 ?        S    10:23   0:03 /usr/lib/gamin/1000      7985  3.4  2.4  40396  6236 ?        S    10:24   0:55 /usr/bin/artsd
1000      7987  0.0  3.9  25896 10052 ?        S    10:24   0:00 kaccess [kdeini1000      7988  0.0  0.5   4288  1476 ?        S    10:24   0:00 /usr/bin/ivman
1000      7989  0.0  0.1   1540   284 ?        S    10:24   0:00 kwrapper ksmser1000      7991  0.0  3.9  26096 10104 ?        S    10:24   0:00 ksmserver [kdei1000      8000  1.0  5.0  28128 12924 ?        S    10:24   0:16 kwin [kdeinit]
1000      8011  0.3  4.9  35100 12720 ?        S    10:24   0:05 knotify [kdeini1000      8023  1.2  6.3  37528 16136 ?        S    10:24   0:20 kdesktop [kdein1000      8030  1.1  6.7  32072 17236 ?        S    10:24   0:19 kicker [kdeinit1000      8043  0.1  4.2  27164 10836 ?        S    10:24   0:01 kbluetoothd --d1000      8045  0.3  4.4  26876 11472 ?        S    10:24   0:05 klipper [kdeini1000      8047  0.3  5.7  29412 14672 ?        S    10:24   0:06 kmix [kdeinit]
1000      8048  0.5  4.7  68264 12068 ?        Sl   10:24   0:08 /usr/lib/evolut1000      8054 23.3 14.5  86252 37152 ?        SL   10:24   6:12 /usr/lib/amarok1000      8055  0.8  6.1  54160 15632 ?        Sl   10:24   0:14 gaim --session
1000      8056  0.1  4.2  26368 10816 ?        S    10:24   0:02 kdesu -u root -1000      8058  0.0  1.4   6396  3676 ?        S    10:24   0:00 /usr/lib/gconf21000      8059  0.1  4.1  26364 10712 ?        S    10:24   0:02 kdesu -u root -1000      8061  0.0  1.9  16244  5024 ?        S    10:24   0:00 /usr/bin/kdesudroot      8063  0.0  0.2   2168   664 pts/1    Ss+  10:24   0:00 /usr/bin/sudo -root      8068  0.0  0.3   2168   824 pts/2    Ss+  10:24   0:00 /usr/bin/sudo -1000      8072  0.0  0.9   6272  2504 ?        Ss   10:24   0:00 /usr/lib/bonobo1000      8128  0.0  2.0  16460  5360 ?        S    10:25   0:00 /usr/bin/kdesudroot      8135  0.0  0.1   1760   488 pts/3    Ss+  10:25   0:00 /usr/bin/kdesu_root      8139  0.8  5.4  31632 13992 ?        Ssl  10:25   0:13 firestarter --sroot      8159  0.0  0.7   6416  1856 ?        S    10:25   0:00 /usr/lib/gconf21000      8245  0.0  2.0  16460  5360 ?        S    10:25   0:00 /usr/bin/kdesudroot      8251  0.0  0.1   1760   488 pts/4    Ss+  10:25   0:00 /usr/bin/kdesu_root      8270  0.5  5.3  39648 13752 ?        Ssl  10:25   0:08 nautilus --sm-c1000      8297  0.0  1.2  73532  3288 ?        Sl   10:25   0:00 /usr/lib/evolut1000      8343  0.5  4.6  36536 12024 ?        Sl   10:25   0:08 /usr/lib/evolutroot      8431  0.1  0.4   2588  1032 ?        S    10:25   0:01 /usr/lib/gamin/root      8436  0.0  1.1   6272  2824 ?        Ss   10:25   0:00 /usr/lib/bonoboroot      8468  0.0  1.3   8340  3400 ?        Sl   10:25   0:00 /usr/lib/gnome-root      8543  0.0  0.2   2276   724 ?        S    10:25   0:00 /usr/lib/nautil1000      8638  0.0  2.3  32696  6052 ?        Ss   10:30   0:00 /usr/bin/artsd
1000      8705  0.1  5.4  28556 13844 ?        S    10:39   0:01 kio_uiserver [k1000      8707  0.0  3.7  24932  9552 ?        S    10:39   0:00 kio_file [kdein1000      8711  0.8  8.9  38076 23000 ?        S    10:39   0:06 konqueror [kdei1000      8722 16.6 14.9 105464 38176 ?        Sl   10:40   1:46 /usr/lib/mozill1000      8775  3.1  8.1  50212 20844 ?        Sl   10:46   0:09 gnome-terminal
1000      8779  0.0  0.2   2280   716 ?        S    10:46   0:00 gnome-pty-helpe1000      8780  0.0  0.8   4508  2124 pts/5    Ss   10:46   0:00 bash
1000      8803  0.0  0.4   2760  1032 pts/5    R+   10:51   0:00 ps aux

and these are the swap details:

azmansell@ubuntu:~$ cat /proc/swaps
Filename                                Type            Size    Used    Priority/dev/hda5                               partition       441748  72928   -1
azmansell@ubuntu:~$

---

### Post by azmansell on 2006-05-19
[QUOTE=stansz]xfce is ugly....lol 

i like icewm better..,(vector) on my old laptop..runs smooth so far..

but nothing beats gnome....kde doesnt come close in my opinon 

but it eats up ram like mad .....so for those less fortunate...then i like icewm over xcfe[/QUOTE]

how do i go about getting this for a tester?, ive looked at screenshots.. it looks nice

---

### Post by dmizer on 2006-05-19
it's not difficult.  since it's so small, it will be easy to just add it onto your current load.  if you don't like it you can take it off through synaptic later.

try: sudo apt-get update && sudo apt-get install icewm

btw ... any time you are considering adding software, you can open up synaptic and use the search function to look for the program name.  just put a checkmark in the square next to the package and then click "apply".

once you've loaded icewm, you can select it from the menu in your logon screen.

---

### Post by ductruffe on 2006-05-19
I am running a full install of Ubuntu 5.10 on a P2 266mhz with 96mb ram and some sort of on board video. Its running gnome (basically because I couldnt get other window managers to work properly for what I wanted) runs firefox etc fine for me and is being used as a F@H machine.

Sure its slow, but it does the job and is bearable for word proccessing and the like, so Im not sure exactly what your comparing your 1ghz "choppy" performance to.

I have run a full install of windows XP on a 266mhz with 64mb ram, and yes, it was fine but did experience crashes when running lots of windows.

---

### Post by azmansell on 2006-05-19
[QUOTE=dmizer]it's not difficult.  since it's so small, it will be easy to just add it onto your current load.  if you don't like it you can take it off through synaptic later.

try: sudo apt-get update && sudo apt-get install icewm

btw ... any time you are considering adding software, you can open up synaptic and use the search function to look for the program name.  just put a checkmark in the square next to the package and then click "apply".

once you've loaded icewm, you can select it from the menu in your logon screen.[/QUOTE]


cheers for that ive given it a try but prefer kde or xfce. i have some new problems now though and dont know what has caused them!!

the whole system (whether i log in with gnome, xfce or kde) has slowed to a crawl and the harddisk is going like the clappers. its really weird as, apart from installing icewm, i havent done anything bar rebooting.

also in xfce, the panel has dissappeared completely, the wallpaper wont change and the grey bar at the top does nothing. wont even let me right click... weird, i think my system is posessed!!

---

### Post by gr0kzer0 on 2006-05-19
My box has a 450 MHz processor, 156 MB of RAM and a 4 GB hard disk.  Its an old Win98 vintage) Compaq Presario 1246 laptop.  I use the xubuntu-desktop mostly, but occasionally use gnome.  It's not super-fast, but when using xfce it isn't really a dog.  Ang it is old, so what can I expect, right?

Trying to use OOo on such a system is, of course, a joke - it would need half an hour just to load!  But the only office app I use is word processing, ans abiword came with xubuntu-desktop, so i removed OOo from the system.  This freed up quite a bit of hard disk space.

I tried removing gnome from the box, but this seemed to cause problems, so I reinstalled it.  Is it possible to get rid of gnome? This would free up loads of disk space.  But I want to continue using Rhythmbox (the music player that came with xfce is a joke, imho)

---

### Post by gr0kzer0 on 2006-05-19
> also in xfce, the panel has dissappeared completely, the wallpaper wont change and the grey bar at the top does nothing. wont even let me right click... weird, i think my system is posessed!!

If you click on xfce menu (the little mouse), then Settings, then Desktop Settings, there should be a box where you can add/change where the system looks for picture files to use as wallpaper.  I've added a "pix" sub-directory to my home directory where I keep all my image files.

> the whole system (whether i log in with gnome, xfce or kde) has slowed to a crawl and the harddisk is going like the clappers. its really weird as, apart from installing icewm, i havent done anything bar rebooting.

That sounds more like a hardware issue to me than anything to do with ubuntu.  You sure your box isn't screwed?

---

### Post by azmansell on 2006-05-19
[QUOTE=gr0kzer0]If you click on xfce menu (the little mouse), then Settings, then Desktop Settings, there should be a box where you can add/change where the system looks for picture files to use as wallpaper.  I've added a "pix" sub-directory to my home directory where I keep all my image files.



That sounds more like a hardware issue to me than anything to do with ubuntu.  You sure your box isn't screwed?[/QUOTE]

trouble is i havent got an xfce menu. basically the whole desktop is empty with the default background and a blank grey bar across the top. no menus or anything. i am currently opening programs with the right click to give me the application menu.

is there a "take screenshot" command in terminal i can use? ill be able to show you what i mean if i can do that.

cheers

---

### Post by azmansell on 2006-05-19
[QUOTE=azmansell]trouble is i havent got an xfce menu. basically the whole desktop is empty with the default background and a blank grey bar across the top. no menus or anything. i am currently opening programs with the right click to give me the application menu.

is there a "take screenshot" command in terminal i can use? ill be able to show you what i mean if i can do that.

cheers[/QUOTE]

i got it, this is what my desktop looks like:

[[IMG]http://i2.photobucket.com/albums/y5/azmansell/th_myscreen.jpg[/IMG]](http://i2.photobucket.com/albums/y5/azmansell/myscreen.jpg)


the wallpaper i have set is differnet to the one displaying, i have chosen "mac style" for the top bar yet nothing changes. and there is no xfce menu at all. ive tried everything (i think!)
even un and re- installed the desktop etc

---

