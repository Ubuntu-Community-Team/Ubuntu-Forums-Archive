---
title: "[SOLVED] still need help"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by japephillips on 2008-02-11
i had a post yesterday, lost pages back, [http://ubuntuforums.org/showthread.php?p=4308149#post4308149](http://ubuntuforums.org/showthread.php?p=4308149#post4308149)
about something dialling out via modem to ppp during ubuntu 7.10 boot and got little help. 

after disconnecting the unrequested connection via toolbar/network the machine would not reconnectI later unless i reset but then it would dial again...

. i have part solved it myself by working out finally how to turn off 'updater' from 'sessions' as the way i was told to use did not work (via sys/admin). That is a bug i think. Anyway now i can indeed once again connect at will but something STILL dials up during boot, also ignoring the modem setting of mute speaker.

I do not want *anything* dialling out without my control. Does anyone here know enough to at least tell me where to look and STOP this?

---

### Post by dstew on 2008-02-11
Probably you have a script that runs during system initialization that dials. Look in the System --> Administration --> Services window and see if there is anything suspicious there. It is easy to uncheck services (which are started by scripts) and restart to see if you can find one that is causing this behavior. You can also look directly in the scripts directory /etc/init.d and see what is there.

---

### Post by japephillips on 2008-02-11
thanks for responding, when i type /etc/init.d into the terminal it just says it is a dir and does nothing
i don't know these commands yet, how to use terminal


under services there is anacron and atd as action schedulers, crash report, klogd, sysklogd, avahi,scren, dbus but i do not know how to look deeper into them

what if i turn off atd?

under the system log what kicks in during boot calls itself (after all the kernel messages) laptop chat [4262]

---

### Post by spiderbatdad on 2008-02-11
could you post your /etc/wvdial.conf file...you may want to exclude username, password.

---

### Post by japephillips on 2008-02-11
umm, I would if I knew how, I typed /etc/wvdial.conf into terminal and it said 'permission denied!

I am really new at this and running out of ideas and wil power! I really cannot spend many more days configuring a PC and tying up my sole phone line researching just because I want Linux and a lean mean machine.

---

### Post by spiderbatdad on 2008-02-11
you can do
Code:

cat /etc/wvdial.conf

or you can navigate to it with Places>>Computer>>File System>>etc...then scroll to the bottom and click wvdial.conf

Also. are you using gnome-ppp? How do you launch the connection manually...in terminal?
What dstew said about System>>Administration>>Services may be the simple solution.

Sorry both posts going now!

---

### Post by japephillips on 2008-02-11
this is all it said

root@j-laptop:/home/j# cat /etc/init.d
cat: /etc/init.d: Is a directory
root@j-laptop:/home/j# /etc/init.d

root@j-laptop:/home/j# cat /etc/wvdial.conf
[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes


I don't know what gnome ppp is, 
i set this up using toolbar/network/manual config and to connect i just click on that same place which has a connect to dialup tag, i got that far after a week of hell by downloading and installing hsf drivers

well i posted what is in services above but have no idea what they mean or how to go farther there to see what they do

i went also via places/computer/files and the initd folder is empty and there is no folder for wvconf despite my checking 'show hidden files'

i will have to disconnect now and do some real life stuff then check in in a couple of hours, appreciate your help

---

### Post by dstew on 2008-02-11
/etc/init.d is a directory that contains scripts. You can look into it with the command```
ls -l /etc/init.d
```That probably won't help you though, unless you recognize the name what is causing the problem.

My guess is that your system is configured to try to connect with your internet service provider at boot-up. It is probably running a script to start the point-to-point-protocol daemon, which is named **pppd**. Look in your Services window to see if you can find this, or look in the /etc/init.d directory for it. If it is there, we can probably disable it, so that it does not run at boot-up.

---

### Post by japephillips on 2008-02-11
root@j-laptop:/home/j# ls -l /etc/init.d
total 408
-rwxr-xr-x 1 root root 2701 2007-08-16 00:33 acpid
-rwxr-xr-x 1 root root  762 2007-08-31 12:48 acpi-support
-rwxr-xr-x 1 root root 9534 2007-09-04 12:52 alsa-utils
-rwxr-xr-x 1 root root 1084 2007-03-05 17:38 anacron
-rwxr-xr-x 1 root root 1667 2007-05-23 22:59 apmd
-rwxr-xr-x 1 root root 2793 2007-10-14 19:48 apparmor
-rwxr-xr-x 1 root root 3024 2007-05-14 16:28 apport
-rwxr-xr-x 1 root root  969 2007-02-21 00:41 atd
-rwxr-xr-x 1 root root 2460 2007-10-05 01:02 avahi-daemon
-rwxr-xr-x 1 root root 6557 2007-10-03 18:54 bluetooth
-rwxr-xr-x 1 root root 3597 2007-10-04 21:17 bootclean
-rwxr-xr-x 1 root root 2121 2007-10-04 21:17 bootlogd
-rwxr-xr-x 1 root root 1768 2007-10-04 21:17 bootmisc.sh
-rwxr-xr-x 1 root root 1383 2007-05-19 01:47 brltty
-rwxr-xr-x 1 root root 2887 2007-10-04 21:17 checkfs.sh
-rwxr-xr-x 1 root root 9875 2007-10-04 21:17 checkroot.sh
-rwxr-xr-x 1 root root 2941 2007-08-04 08:21 consolekit
-rwxr-xr-x 1 root root 6355 2007-05-30 22:29 console-screen.sh
-rwxr-xr-x 1 root root 1612 2007-05-02 21:41 console-setup
-rwxr-xr-x 1 root root 1761 2006-12-21 01:46 cron
-rwxr-xr-x 1 root root 1937 2007-10-15 21:11 cupsys
-rwxr-xr-x 1 root root 4192 2007-10-05 21:44 dbus
-rwxr-xr-x 1 root root 1497 2007-06-13 00:46 dhcdbd
-rwxr-xr-x 1 root root 1223 2007-06-22 14:55 dns-clean
-rwxr-xr-x 1 root root 3136 2007-10-15 20:39 gdm
-rwxr-xr-x 1 root root 6607 2007-10-01 11:01 glibc.sh
-rwxr-xr-x 1 root root 2294 2007-10-09 04:46 hal
-rwxr-xr-x 1 root root 1228 2007-10-04 21:17 halt
-rwxr-xr-x 1 root root 5137 2005-04-21 20:10 hdparm
-rwxr-xr-x 1 root root  909 2007-10-04 21:17 hostname.sh
-rwxr-xr-x 1 root root 3576 2007-09-30 10:43 hotkey-setup
lrwxrwxrwx 1 root root   15 2008-02-10 16:06 hsf -> /usr/sbin/rchsf
-rwxr-xr-x 1 root root 4569 2007-10-03 14:48 hwclockfirst.sh
-rwxr-xr-x 1 root root 4568 2007-10-03 14:48 hwclock.sh
-rwxr-xr-x 1 root root 1304 2007-06-03 08:48 keyboard-setup
-rwxr-xr-x 1 root root  944 2007-10-04 21:17 killprocs
-rwxr-xr-x 1 root root 1752 2007-09-18 06:54 klogd
-rwxr-xr-x 1 root root 2285 2007-09-19 09:01 laptop-mode
-rwxr-xr-x 1 root root  632 2007-07-13 22:57 libpam-foreground
-rwxr-xr-x 1 root root  349 2007-10-15 21:33 linux-restricted-modules-common
-rwxr-xr-x 1 root root  748 2006-01-24 05:47 loopback
-rwxr-xr-x 1 root root 1050 2007-07-29 05:52 makedev
-rwxr-xr-x 1 root root 1399 2007-10-06 02:40 module-init-tools
-rwxr-xr-x 1 root root  596 2007-10-04 21:17 mountall-bootclean.sh
-rwxr-xr-x 1 root root 2430 2007-10-04 21:17 mountall.sh
-rwxr-xr-x 1 root root 1465 2007-10-04 21:17 mountdevsubfs.sh
-rwxr-xr-x 1 root root 1460 2007-10-04 21:17 mountkernfs.sh
-rwxr-xr-x 1 root root  594 2007-10-04 21:17 mountnfs-bootclean.sh
-rwxr-xr-x 1 root root 1244 2007-10-04 21:17 mountoverflowtmp
-rwxr-xr-x 1 root root 2689 2007-10-04 21:17 mtab.sh
-rwxr-xr-x 1 root root 1772 2007-05-08 20:33 networking
-rwxr-xr-x 1 root root  860 2005-10-29 12:48 nvidia-kernel
-rwxr-xr-x 1 root root 2351 2007-03-08 08:45 pcmciautils
-rwxr-xr-x 1 root root 4108 2006-12-19 11:35 powernowd
-rwxr-xr-x 1 root root  177 2006-12-19 11:35 powernowd.early
-rwxr-xr-x 1 root root  375 2007-10-05 05:56 pppd-dns
-rwxr-xr-x 1 root root 1208 2007-07-31 18:13 procps.sh
-rwxr-xr-x 1 root root 8191 2007-10-04 21:17 rc
-rwxr-xr-x 1 root root  522 2007-10-04 21:17 rc.local
-rwxr-xr-x 1 root root  117 2007-10-04 21:17 rcS
-rwxr-xr-x 1 root root 1492 2007-10-12 22:08 readahead
-rwxr-xr-x 1 root root 1957 2007-10-12 22:08 readahead-desktop
-rw-r--r-- 1 root root 1335 2007-10-04 21:17 README
-rwxr-xr-x 1 root root  692 2007-10-04 21:17 reboot
-rwxr-xr-x 1 root root 1000 2007-10-04 21:17 rmnologin
-rwxr-xr-x 1 root root 4945 2007-08-18 11:24 rsync
-rwxr-xr-x 1 root root  714 2007-07-27 01:56 screen
-rwxr-xr-x 1 root root  975 2007-10-04 21:17 sendsigs
-rwxr-xr-x 1 root root  585 2007-10-04 21:17 single
-rwxr-xr-x 1 root root 4215 2007-10-04 21:17 skeleton
-rwxr-xr-x 1 root root 5369 2007-09-30 10:07 sl-modem-daemon
-rwxr-xr-x 1 root root  510 2007-10-04 21:17 stop-bootlogd
-rwxr-xr-x 1 root root  647 2007-10-04 21:17 stop-bootlogd-single
-rwxr-xr-x 1 root root  864 2007-10-12 22:08 stop-readahead
-rwxr-xr-x 1 root root 3369 2007-09-18 06:54 sysklogd
-rwxr-xr-x 1 root root 2471 2007-10-06 01:48 udev
-rwxr-xr-x 1 root root  706 2007-10-06 01:48 udev-finish
-rwxr-xr-x 1 root root 3511 2007-10-04 21:17 umountfs
-rwxr-xr-x 1 root root 1833 2007-10-04 21:17 umountnfs.sh
-rwxr-xr-x 1 root root 1439 2007-10-04 21:17 umountroot
-rwxr-xr-x 1 root root 1815 2007-10-04 21:17 urandom
-rwxr-xr-x 1 root root 2814 2007-10-15 19:20 usplash
-rwxr-xr-x 1 root root  820 2007-09-19 19:50 vbesave
-rwxr-xr-x 1 root root 1939 2007-10-04 21:17 waitnfs.sh
-rwxr-xr-x 1 root root 1626 2007-09-25 04:35 wpa-ifupdown
-rwxr-xr-x 1 root root 1843 2007-07-05 00:55 x11-common
-rwxr-xr-x 1 root root  503 2007-09-16 12:05 xserver-xorg-input-wacom
root@j-laptop:/home/j# 
 

no pppd in services window


root@j-laptop:/home/j#  ls -l /etc/wvdial.conf
-rw-r----- 1 root dialout 66 2007-10-16 09:30 /etc/wvdial.conf



and i just found this event when poking around in var/log under daemon.log but no idea what or why ...

Feb 12 11:58:25 j-laptop NetworkManager: <info>  Activating dialup device ppp0 via Modem (ppp0) ... 
Feb 12 11:58:25 j-laptop NetworkManager: <WARN>  nm_system_activate_dialup(): Couldn't activate dialup device ppp0 via Modem (ppp0) - 134874984

---

### Post by japephillips on 2008-02-11
well i am still very lost .... the damn thing still tries to dial out all day, noisily, despite disconnecting the phone lead. it stops when by using network manager applet i turn of, 'disable' network, but then it will not dial out at all. so it is obviously a network connection default setting somewhere and that is where I am lost.

can i undo/uninstall the network manager and use some other configuration method, maybe a different network manager and a different ppp setup?

this is probably a basic setting somewhere you take for granted but is beyond me despite poking around
i have other small probs like power management errors i can live with for now
and i am starting to like ubuntu but this has taken a good few days too many

i will give it another 24 hours and then have to go back to XP (shudder) and antiviruses and firewalls and all the crap i don't want or need, lol

---

### Post by dstew on 2008-02-11
> -rwxr-xr-x 1 root root 375 2007-10-05 05:56 pppd-dnsIt is probably this script. To de-activate it, enter this on a command line```
 sudo update-rc.d -f pppd-dns remove
```Maybe that will do it.

EDIT: Going to bed now. See you tomorrow.

---

### Post by spiderbatdad on 2008-02-11
there is gnome-ppp or kppp, but getting a dial-up to work in the first place can be so difficult in Linux. I think you're lucky it's working. You might look for a wvdial or gnome-ppp tutorial...it is pretty simple to set up, but gnome-ppp had to be patched for gusty. It is a graphical frontend for wvdial, which runs in the terminal ```
man wvdial
```for more info. Basically the gnome-ppp wrote semicolons into the /etc/wvdial.conf file, and this caused the llines to be seen as commented out in Gutsy. There is a gnome-pppfixedforgutsy available. I don't know how good it is.

You may be able to connect from the terminal by running ```
wvdialconf

```  then edit /etc/wvdial.conf to include your username, password, and the phone number.```
gksu gedit /etc/wvdial.conf
``` save the file. Then return to the terminal and run```
wvdial
``` ctrl-c to disconnect, if by some miracle you connect.

The graphical frontends may be easier to use, but you should confirm the info they wrtie to /etc/wvdial.conf.

Supposedly kppp works better than gnome-ppp.

Here's a how-to I used to get started:[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

gnome-ppp and kppp are both in synaptic.

---

### Post by spiderbatdad on 2008-02-11
btw you should have eth0 disabled when using a modem.  only suggesting the above clients as a last resort, since you have it working with pppconfig. maybe dstew's latest script will work for you.

---

### Post by japephillips on 2008-02-11
i want to thank you both, i am too brain dead to go further today,

i will spend a couple of days playing with it and your ideas/help before I give up!
maybe re-install and resetup a different route

 i have an old box with a 700 celeron processor running XP stored in the shed, it is smooth running and secure because I stripped so much crap off it in five years and has all my years and years of Win stuff on it, i shall bring that back in the house and use that for 'net access while I explore linux on this laptop, hopefully end up wiht this laptop configured and then I can sort through years of docs and pics, setup a basic linux on the old box and GET RID OF MICROSOFT ONCE AND FOR ALL

this is my third go at installing and running linux distros in the last two year - incredibly frustrating but it is certainly getting better and more sophisticated. i get frustrated and even angry and then remember people like you are making a big effort so it behooves me to try harder

such a shame, in order to replace Windows, it has to get more like windows, at least in terms of user friendliness and hardware setup. maybe the best hope is the slow growth that is finally seeing manufacturers load Linux OS

keep it up folks
jape

---

### Post by japephillips on 2008-02-12
just a quick one, turned the machine on, after ppdns remove - well, i am talking here on the connection it still made, lol
will try kppp next

---

### Post by japephillips on 2008-02-12
Well I just totally removed 'network manager' from the startup, The 'network configure' in 7.10 as installed seems to need network on/enabled to connect via modem but I couldn't work out all the loopback/eth0 stuff so I took a punt and just removed it and downloaded and installed Kppp. Took a while to find it in the 'bin' and setup an applet for it but then  - easy setup, a grahical interface, a connection icon and more. It found the modem instantly, shows all the commands and more so it works as I wish without a failure ... yet

I think this is solved, Many, many thanks to you folks for support, Now, the power management ... nah, another day ...

---

### Post by dstew on 2008-02-12
Great. Amazing what a good night's sleep and a cup of coffee can do for you! Would you please also mark the thread as Solved (in your Thread Tools menu).

---

