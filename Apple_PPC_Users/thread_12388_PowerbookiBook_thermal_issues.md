---
title: "Powerbook/iBook thermal issues?"
date: 2005-01-24
forum: Apple PPC Users
---

### Post by Viro on 2005-01-24
I've been running Ubuntu Linux solely for a week now on my Powerbook, using it for everything from DVD playing, to writing code, emailing to running my neural network simulations.

One thing that I have come to realize is that the laptop runs much hotter than it did when I was running OS X. The left palm rest (above the hard drive) seems to get really hot. So does the CPU area. Is this normal for laptops running Linux? Or is there something that I need to set?

I've currently got the powernowd daemon running, and my CPU speed is set to half for most of the time until CPU usage goes above 90%. The hard drive also spins down. I hear it spinning up and down, so I know that isn't the problem.

So anyone able to shed any light on why my laptop is running hot? Does anyone else have a similar experience?

---

### Post by port7 on 2005-01-24
Yep I get that too, it gets quite hot on the left of the trackpad.

I have an 800Mhz G3

---

### Post by SunTzu on 2005-01-24
I have a 15" G4 powerbook and I've been running ubuntu for for about 2 weeks and it did get real hot once for about an hour and has not done it since. Not sure if thats good or bad. I have done the update and upgrade: (#apt-get update) and (# apt-get upgrade) but I'm not sure if that was the solution to the problem.

---

### Post by Viro on 2005-01-24
Glad to see it's not just me, but it is slightly disconcerting to see my laptop going so hot. Hope it doesn't shorten the lifespan of my laptop. 

Now I wonder how to go about fixing it? I don't remember stock Debian ever making my hard drive so hot.

---

### Post by TekMate on 2005-01-24
I have the opposite problem my PowerBook 867mhz runs cool under Linux but runs too hot to touch under Panther.

---

### Post by Viro on 2005-01-25
Have you configured the spindown time of the hard drive? Also, what about the CPU scaling? Is there anything else you did?

---

### Post by newfontherock on 2005-01-27
Hi Viro, 

I have similar issues with my iBook G4 933.  I'm a little scared to use my iBook with ubuntu because it does get so hot.  And the fan (which never makes its presence known in OS X) is very noisy.  So I think I'll have to wait for the next release before using ubuntu again.

---

### Post by jerome bettis on 2005-01-27
[IMG]http://www.targus.com/us/product_images/PA248U_accessories_b.jpg[/IMG] 
[http://www.targus.com/us/product_details.asp?sku=PA248U](http://www.targus.com/us/product_details.asp?sku=PA248U)


cool to the touch with a 7200 rpm hard drive

---

### Post by adamw on 2005-01-28
I have more difficulties with my laptop getting hot with Mac OS X, but mainly when playing DVDs and doing source code compiles.  Of course this is easily fixeable on OS X by setting my processor to "reduced" if I get too worried about the fan spinning up and the overheating.  Not sure how to do this yet on Ubuntu, but then again I haven't needed to.  My laptop runs a lot cooler and I get roughly 60% more battery life when I run Ubuntu.

---

### Post by Viro on 2005-01-28
[QUOTE=adamw]I have more difficulties with my laptop getting hot with Mac OS X, but mainly when playing DVDs and doing source code compiles.  Of course this is easily fixeable on OS X by setting my processor to "reduced" if I get too worried about the fan spinning up and the overheating.  Not sure how to do this yet on Ubuntu, but then again I haven't needed to.  My laptop runs a lot cooler and I get roughly 60% more battery life when I run Ubuntu.[/QUOTE]
 That's all well and good. But my laptop runs hotter and I'm very interested to know what settings you have hence the point of this thread ;).

For those who have cool (as in temperature wise :)) laptops, please do a ps -A and post that listing so we can see what services you're running. Also, tell us if you did anything extra like spindown the hard drive, put on CPU throttling, etc. Model of the laptop will be helpful too.

---

### Post by TekMate on 2005-01-28
Mine runs cool this is my output.

tekmate@TiBook:~ $ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:03 events/0
    4 ?        00:00:00 khelper
   20 ?        00:00:00 kblockd/0
   36 ?        00:00:00 pdflush
   37 ?        00:00:00 pdflush
   38 ?        00:00:00 kswapd0
   39 ?        00:00:00 aio/0
  193 ?        00:00:00 kjournald
  262 ?        00:00:00 udevd
  922 ?        00:00:00 khpsbpkt
 1726 ?        00:00:00 khubd
 2092 ?        00:00:00 pccardd
 2175 ?        00:00:00 knodemgrd_0
 2378 ?        00:00:00 portmap
 2653 ?        00:00:00 syslogd
 2664 ?        00:00:00 klogd
 2745 ?        00:00:00 apmd
 2769 ?        00:00:03 cupsd
 2789 ?        00:00:00 dbus-daemon-1
 2793 ?        00:00:03 hald
 2813 ?        00:00:00 famd
 2827 ?        00:00:00 inetd
 2848 ?        00:00:13 pbbuttonsd
 2921 ?        00:00:00 cardmgr
 2942 ?        00:00:00 eth1
 3127 ?        00:00:00 master
 3143 ?        00:00:00 qmgr
 3193 ?        00:00:00 powernowd
 3205 ?        00:00:00 mdadm
 3216 ?        00:00:00 atd
 3227 ?        00:00:00 cron
 3241 ?        00:00:00 gdm
 3251 ?        00:00:00 gdm
 3276 tty1     00:00:00 getty
 3285 tty2     00:00:00 getty
 3286 tty3     00:00:00 getty
 3287 tty4     00:00:00 getty
 3288 tty5     00:00:00 getty
 3289 tty6     00:00:00 getty
 3381 ?        00:00:00 dhclient3
 3452 ?        00:02:19 XFree86
 3719 ?        00:00:01 x-session-manag
 3765 ?        00:00:00 ssh-agent
 3768 ?        00:00:00 dbus-launch
 3769 ?        00:00:00 dbus-daemon-1
 3771 ?        00:00:03 gconfd-2
 3774 ?        00:00:00 gnome-keyring-d
 3776 ?        00:00:00 esd
 3778 ?        00:00:00 bonobo-activati
 3780 ?        00:00:01 gnome-settings-
 3790 ?        00:00:01 xscreensaver
 3814 ?        00:00:01 gnome-smproxy
 3816 ?        00:00:08 metacity
 3824 ?        00:00:03 gnome-panel
 3826 ?        00:00:03 nautilus
 3828 ?        00:00:00 gnome-volume-ma
 3834 ?        00:00:02 gnome-cups-icon
 3835 ?        00:00:00 gnome-cups-icon
 3837 ?        00:00:00 nautilus
 3838 ?        00:00:00 nautilus
 3841 ?        00:00:00 gnome-vfs-daemo
 3842 ?        00:00:00 gnome-vfs-daemo
 3843 ?        00:00:00 gnome-vfs-daemo
 3847 ?        00:00:00 mapping-daemon
 3848 ?        00:00:00 nautilus
 3849 ?        00:00:00 nautilus
 3850 ?        00:00:00 nautilus
 3851 ?        00:00:00 nautilus
 3853 ?        00:00:06 wnck-applet
 3855 ?        00:00:00 trashapplet
 3856 ?        00:00:00 trashapplet
 3857 ?        00:00:00 trashapplet
 3858 ?        00:00:00 trashapplet
 3860 ?        00:00:01 clock-applet
 3863 ?        00:00:01 mixer_applet2
 3865 ?        00:00:00 battstat-applet
 3867 ?        00:00:06 wireless-applet
 3869 ?        00:00:00 notification-ar
 4353 ?        00:07:32 firefox-bin
 4381 ?        00:00:00 firefox-bin
 4382 ?        00:00:06 firefox-bin
 4386 ?        00:00:04 firefox-bin
 5165 ?        00:00:00 pickup
 5207 ?        00:00:07 soffice.bin
 5232 ?        00:00:00 soffice.bin
 5233 ?        00:00:00 soffice.bin
 5234 ?        00:00:00 soffice.bin
 5235 ?        00:00:00 getstyle-gnome
 5236 ?        00:00:00 soffice.bin
 5239 ?        00:00:00 soffice.bin
 5807 ?        00:00:00 firefox-bin
 6316 ?        00:00:00 firefox-bin
 6317 ?        00:00:00 firefox-bin
 6318 ?        00:00:00 firefox-bin
 6319 ?        00:00:00 firefox-bin
 6320 ?        00:00:00 firefox-bin
 6336 ?        00:00:00 gnome-terminal
 6339 ?        00:00:00 gnome-pty-helpe
 6340 pts/0    00:00:00 bash
 6341 ?        00:00:00 gnome-terminal
 6342 ?        00:00:00 gnome-terminal
 6347 pts/0    00:00:00 ps

---

### Post by adamw on 2005-01-29
Here it is (1.5 ghz powerbook):
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:02 events/0
    4 ?        00:00:00 khelper
   26 ?        00:00:00 kblockd/0
   42 ?        00:00:00 pdflush
   43 ?        00:00:00 pdflush
   44 ?        00:00:00 kswapd0
   45 ?        00:00:00 aio/0
  199 ?        00:00:00 kjournald
  268 ?        00:00:00 udevd
  835 ?        00:00:00 thermostat
  918 ?        00:00:00 khpsbpkt
 1770 ?        00:00:00 pccardd
 1831 ?        00:00:00 khubd
 2585 ?        00:00:00 knodemgrd_0
 2825 ?        00:00:00 dhclient3
 2837 ?        00:00:00 portmap
 3150 ?        00:00:00 syslogd
 3185 ?        00:00:00 klogd
 3247 ?        00:00:00 apmd
 3268 ?        00:00:00 battery-stats-c
 3276 ?        00:00:00 cpudynd
 3282 ?        00:00:00 cupsd
 3303 ?        00:00:00 dbus-daemon-1
 3307 ?        00:00:00 hald
 3326 ?        00:00:00 dictd
 3332 ?        00:00:00 distccd
 3333 ?        00:00:00 distccd
 3372 ?        00:00:00 famd
 3406 ?        00:00:00 ikeyd
 3419 ?        00:00:00 inetd
 3428 ?        00:00:00 distccd
 3438 ?        00:00:00 pbbuttonsd
 3476 ?        00:00:00 cardmgr
 3515 ?        00:00:00 distccd
 3578 ?        00:00:00 master
 3580 ?        00:00:00 pickup
 3581 ?        00:00:00 qmgr
 3614 ?        00:00:00 powernowd
 3627 ?        00:00:00 rpc.statd
 3638 ?        00:00:00 mdadm
 3649 ?        00:00:00 cfsd
 3654 ?        00:00:00 atd
 3667 ?        00:00:00 cron
 3690 ?        00:00:00 bacula-sd
 3692 ?        00:00:00 bacula-sd
 3694 ?        00:00:00 bacula-sd
 3706 ?        00:00:00 rpciod
 3707 ?        00:00:00 lockd
 3710 ?        00:00:00 apache
 3717 ?        00:00:00 apache
 3718 ?        00:00:00 apache
 3719 ?        00:00:00 apache
 3720 ?        00:00:00 apache
 3721 ?        00:00:00 apache
 3722 ?        00:00:00 bacula-fd
 3723 ?        00:00:00 bacula-fd
 3725 ?        00:00:00 bacula-fd
 3731 ?        00:00:00 bacula-dir
 3732 ?        00:00:00 bacula-dir
 3734 ?        00:00:00 bacula-dir
 3735 ?        00:00:00 bacula-dir
 3740 ?        00:00:00 gdm
 3750 ?        00:00:00 gdm
 3763 tty1     00:00:00 getty
 3764 tty2     00:00:00 getty
 3765 tty3     00:00:00 getty
 3766 tty4     00:00:00 getty
 3767 tty5     00:00:00 getty
 3832 ?        00:00:05 XFree86
 3861 tty6     00:00:00 getty
 3974 ?        00:00:00 x-session-manag
 4020 ?        00:00:00 ssh-agent
 4023 ?        00:00:00 dbus-launch
 4024 ?        00:00:00 dbus-daemon-1
 4026 ?        00:00:01 gconfd-2
 4029 ?        00:00:00 gnome-keyring-d
 4031 ?        00:00:00 esd
 4033 ?        00:00:00 bonobo-activati
 4035 ?        00:00:00 gnome-settings-
 4045 ?        00:00:00 xscreensaver
 4069 ?        00:00:00 gnome-smproxy
 4071 ?        00:00:00 metacity
 4079 ?        00:00:00 gnome-panel
 4081 ?        00:00:00 nautilus
 4083 ?        00:00:00 gnome-volume-ma
 4089 ?        00:00:00 gnome-cups-icon
 4090 ?        00:00:00 nautilus
 4091 ?        00:00:00 nautilus
 4093 ?        00:00:00 gnome-vfs-daemo
 4094 ?        00:00:00 gnome-vfs-daemo
 4095 ?        00:00:00 gnome-vfs-daemo
 4096 ?        00:00:00 gnome-cups-icon
 4102 ?        00:00:00 mapping-daemon
 4103 ?        00:00:00 nautilus
 4104 ?        00:00:00 nautilus
 4105 ?        00:00:00 nautilus
 4106 ?        00:00:00 nautilus
 4107 ?        00:00:00 nautilus
 4109 ?        00:00:00 wnck-applet
 4111 ?        00:00:00 mixer_applet2
 4113 ?        00:00:00 notification-ar
 4115 ?        00:00:00 clock-applet
 4119 ?        00:00:01 battstat-applet
 4257 ?        00:00:13 epiphany
 4261 ?        00:00:00 epiphany
 4262 ?        00:00:00 epiphany
 4263 ?        00:00:00 epiphany
 4297 ?        00:00:00 trivial-rewrite
 4323 ?        00:00:00 epiphany
 4324 ?        00:00:00 epiphany
 4325 ?        00:00:00 epiphany
 4338 ?        00:00:00 gnome-terminal
 4339 ?        00:00:00 gnome-pty-helpe
 4340 pts/0    00:00:00 bash
 4341 ?        00:00:00 gnome-terminal
 4342 ?        00:00:00 gnome-terminal
 4346 ?        00:00:00 gnome-cups-icon
 4347 pts/0    00:00:00 ps

---

### Post by chele on 2005-01-29
[QUOTE=Viro]That's all well and good. But my laptop runs hotter and I'm very interested to know what settings you have hence the point of this thread ;).

For those who have cool (as in temperature wise :)) laptops, please do a ps -A and post that listing so we can see what services you're running. Also, tell us if you did anything extra like spindown the hard drive, put on CPU throttling, etc. Model of the laptop will be helpful too.[/QUOTE]This one runs hotter then I like. It's a powerbook II, 550MHz, running Hoary, kernel:
~$ uname -a
Linux ti 2.6.10-2-powerpc #1 Thu Jan 27 15:20:15 UTC 2005 ppc GNU/Linux

Looks like at least part of the issue is the fact that powernowd is not running.```

~$ powernowd
powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens
Go away, you are not root. Only root can run me.
~$ sudo powernowd
Password:
powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens
powernowd: Found 1 cpu:
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
Couldn't open file: No such file or directory
couldn't open govn's file for writing: No such file or directory
Couldn't get per-cpu data: Illegal seek
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.5/v2.6 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: clemej@alum.rpi.edu
public@ti:~$ lsmod | grep cpu
cpufreq_userspace       5644  0
cpufreq_ondemand        7964  0
cpufreq_powersave       1984  0
~$ cat /etc/fstab | grep sysfs
~$
``` So, what is sysfs and how does one use it? And why is it not already configured?

---

### Post by chele on 2005-01-29
[QUOTE=chele] So, what is sysfs and how does one use it? And why is it not already configured?[/QUOTE]Never mind:

:~$ mount | grep sysfs
sysfs on /sys type sysfs (rw)

So sysfs in running, just not listed in fstab.

 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)

Is that it then? What is the correct cpufreq driver for a G4 PPC?

---

### Post by Viro on 2005-01-30
Those are the right drivers for the G4. Did you do what he suggested (i.e. check error messages in dmesg)?
> 
pgoh@komek:~ $ dmesg | tail


That should give you any errors that powernowd encountered.

---

### Post by chele on 2005-01-30
[QUOTE=Viro]Those are the right drivers for the G4. Did you do what he suggested (i.e. check error messages in dmesg)?

That should give you any errors that powernowd encountered.[/QUOTE]I'm not seeing any errors from dmesg related to powernowd or cpufreq. However, on the boot screen there is a note:

* Starting powernowd...
* CPU frequency scaling not supported                                                        [ok]

The * before CPU is orange, not red or white. I assume that means it's an information message, rather then something critical?

By the way, there is no /sys/devices/system/cpu/cpu0/cpufreq file on the system.

---

### Post by Viro on 2005-01-30
What kind of powerbook are you using? AFAIK all G4 processors should support frequency scaling. If you have time, do a "cat /proc/cpuinfo" and show us the output.

---

### Post by chele on 2005-01-30
[QUOTE=Viro]What kind of powerbook are you using? AFAIK all G4 processors should support frequency scaling. If you have time, do a "cat /proc/cpuinfo" and show us the output.[/QUOTE]:~$ cat /proc/cpuinfo
processor       : 0
cpu             : 7450, altivec supported
clock           : 550MHz
revision        : 2.1 (pvr 8000 0201)
bogomips        : 546.81
machine         : PowerBook3,3
motherboard     : PowerBook3,3 MacRISC2 MacRISC Power Macintosh
detected as     : 72 (PowerBook Titanium II)
pmac flags      : 0000000b
L2 cache        : 256K unified
memory          : 512MB
pmac-generation : NewWorld

Some more searching on the web shows that as recently as kernel 2.6.8 there was no cpufreq support for this cpu :-(

Bugzilla Bug 132422 – Overheat of PowerBook Titanium II due to lake of cpufreq support [https://bugzilla.redhat.com/beta/show_bug.cgi?id=132422](https://bugzilla.redhat.com/beta/show_bug.cgi?id=132422)

An older discussion on debian-powerpc: cpufreq on TiBook II [http://lists.debian.org/debian-powerpc/2003/07/msg00526.html](http://lists.debian.org/debian-powerpc/2003/07/msg00526.html)

And it appears, from my experience here, that the patch listed in the redhat bug report has not made it into the current kernel. Oh, my poor machine....

---

### Post by Viro on 2005-01-30
Try compiling a kernel yourself? :). You gotta do it sometime and this is as good a reason as any.

---

### Post by mpg on 2005-02-23
[QUOTE=TekMate]I have the opposite problem my PowerBook 867mhz runs cool under Linux but runs too hot to touch under Panther.[/QUOTE]

I have to say that the same happens to me when working under OSX: lately my iBook G4 12 inch started overheating seriously in the left palm rest area. The bottom of the machine is too hot to touch and the fan seems to come on quite rarely and erratically (two days ago it never worked, now it started working after the area became uncomfortably hot).
I ran an extended hardware test and all is fine, and by the way, no overheating while running the tests, and the fan starts and stop at the "corerct" times!
So this would seem to point out that the culprit, at least in my case, is something loaded during startup of OSX.
Alas, after starting I have no processes gobbling up large amounts of CPU times, yet the darn thing keeps overheating! (so it does not seem to come from high CPU or HD activity, either).
This kind of problem moreover is reported in a few other forums (try googling iBook overheating palm ... or hand) not concerned with Linux.
I am not that techinically advanced, and I have no idea if the fan in the iBook is regulated via hardware or software, in this last case, could there be a conflict (i.e. with some "bad" driver) resulting in diminished temperature control capacity? :? 

Sorry for not giving a very knowledgeable contribution to the discussion, but I hope that knowing that this is happening in other instances (i.e. under OSX) and under which conditions could be useful to somebody in solving their problem by helping them look in the right place.

Regards,
Marco

---

### Post by gruepig on 2005-02-23
I've also noticed that my iBook (white iBook G3) runs much hotter in Ubuntu (and Debian) than in OS X.  As for concrete numbers, hddtemp reports a temperature of 40-45C after about half an hour of fairly light use.  Is this within an acceptable range, or should I be concerned?

---

### Post by Xappe on 2005-03-09
I suffer from the same problem. hddtemp gives about 45-50C after half an hour or so, and I hardly ever hear the fans...

would appriciate some help on this issue.

ibook g3 700

---

### Post by Viro on 2005-03-09
I've found a way to get the fans to turn on slightly earlier. It's pretty much a hack and requires you to change some code in the kernel, so unless you're really really concerned about heat, I don't think it's worth bothering.

By default, the CPU fan comes on when the temperature hits 50 C. This has been debated upon in the Debian mailing lists and they seem to have stuck with this value. If you changed the value to 45, like I have, the fans come on sooner and try to bring the temperature down. After doing it, my fans are on most of the time, probably because the CPU doesn't go down much further than 48 C. I guess 50 is alright and there is nothing that can be done about it.

---

### Post by adamw on 2005-03-09
I take back what I said earlier.  I think my powerbook runs cooler because the chip runs at 1.5 ghz, and then underclocks to 750 mhz and powers up the fan when it gets hot.  Even at 750 mhz it can handle idle processing which allows it to cool down pretty quickly.  Using the movie player or doing a build makes it heat up very hot, however.

---

### Post by solidether on 2005-03-25
to keep the machine running on lower noise as used from os x, read the powernowd manual (`man powernowd`) and adjust your local settings in /etc/defaults/powernowd. (for example: OPTIONS="-m 3 -u 95 -l 50 -p 3000 -q") 
also have a look at the files in /sys/devices/temperatures/* (they tell you some temperatures and fanspeeds), which are controlled by the module "therm_adt746x" (this is loaded in /etc/modules.conf - check `modinfo therm_adt746x` to adjust some settings, i use 'therm_adt746x limit_adjust=5 fan_speed=32' in /etc/modules).
good luck & noiseless computing,
;-)
solidether

---

### Post by ast3risk on 2006-05-11
okay, so i have read through this thread, and i too am having the same heat problem. Currently my fan runs nonstop with ubuntu and it has never done that in OSX. I am running an ibook g4 1ghz i think. anyway, what are my option?

change the powernowd settings
compile my own kernel?

im just trying to get a sense of what I am going to do. this is such a problem, that I am thinking of waiting till my next computer to go to ubuntu. i had a 1gig thinkpad, and ubuntu ran perfectly, no wireless problems, no mousefreeze after suspend, etc. has support for ppc in ubuntu gone down or waht?

---

### Post by Netsensei on 2007-03-03
I was wondering wether or not this problem has been solved.

I have an iBook G4 1,2Ghz with a 60Gb disk and 768Mb DDR ram

This week, I installed ubuntu edgy (6.10) on my machine in dual boot with OSX 10.4. Apart from the annoying bugs that plague suspend and sleep function, I noticed that my machine gets hot. I'm not even doing anything: it just shows the desktop. When I bother to do anything, either surfing, mailing or some other common desktop work, it *really* gets hot. And I'm not even trying to consider installing beryl or those other nice 3D desktop thingies...

I checked my temps with hddtemp and /sys/devices/temperatures: 

- My hard disk runs at 40C  going up to 45C when I'm using apt or something. The disk is located, I believe, in the lower left corner of the ibook so that explains why that area is getting so hot.
- CPU/GPU temperatures go up to between 53C and 55C.

Powernowd daemon is working out of the box together with the term_adx modules to control the fans. Which, by the way, really start spinning very loudly. I could turn them down, but i'd rather have noisy iBook then a fried iBook.

Either way, it just gets very hot very quickly. When I reboot back in OSX, my iBook cools down quite quickly. No problems in OSX.

Apart from the obvious suspend bugs, a very hot iBook is holding me completly from switching to linux on my iBook. It's a shame because ubuntu looks great and has a lot of software that can be very easily installed. Unlike OSX.

Can someone please give me pointers here? Is this going to be fixed in Feisty? Is this a kernel issue that needs fixing?

---

