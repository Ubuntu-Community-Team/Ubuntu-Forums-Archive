---
title: "Error starting gnome settings daemon after diabling startup services"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by ture_atlantis on 2008-02-14
I have done a fresh install of Ubuntu 7.10 Gusty.  I have recently been recieving this error:

[I]
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.[/I]

The only things I have done between the install and having this problem are:

1. Disable boot services
2. Install eclipse

Can anyone give me a list of services/runlevels - as i think i disabled something improtant.  Thanks.

---

### Post by ashmew2 on 2008-02-14
Which boot services have you disabled ? Have you disabled all of them  ? 

Check whether you can open things like System > Administration > Network ??
If yes , you need to start dbus.Use the command :

sudo /etc/init.d/dbus start 

Also Add this to the Startup list .

---

### Post by ture_atlantis on 2008-02-14
That is my problem, I dont remember which services I disabled.  I know DBUS was not one of them...  Here is the list of services that are enabled/disabled... 

```
acpi-support 1:off      2:on    3:on    4:on    5:on
acpid        1:off      2:on    3:on    4:on    5:on
alsa-utils   0:off      6:off
anacron      1:off      2:on    3:on    4:on    5:on
apmd         1:off      2:on    3:on    4:on    5:on
apparmor     S:on
apport       0:off      1:off   2:on    3:on    4:on    5:on    6:off
atd          1:off      2:on    3:on    4:on    5:on
avahi-daemon 0:off      1:off   2:on    3:on    4:on    5:on    6:off
bluetooth    1:off      2:on    3:on    4:on    5:on
bootclean   
bootlogd    
brltty       S:on
console-setu S:on
consolekit   0:off      1:off   2:on    3:on    4:on    5:on    6:off
cron         1:off      2:on    3:on    4:on    5:on
cupsys       1:off      2:on    3:on    4:on    5:on
dbus         1:off      2:on    3:on    4:on    5:on
dhcdbd       0:off      1:off   2:on    3:on    4:on    5:on    6:off
dns-clean    S:on
gdm          0:off      1:off   2:on    3:on    4:on    5:on    6:off
hal          1:off      2:on    3:on    4:on    5:on
halt         0:on
hdparm      
hotkey-setup 1:off      2:on    3:on    4:on    5:on
keyboard-set S:on
killprocs    1:on
klogd        1:off      2:on    3:on    4:on    5:on
laptop-mode  0:off      1:off   2:on    3:on    4:on    5:on    6:off
libpam-foreg S:on
linux-restri 0:on       6:on    S:on
loopback     S:on
makedev      1:off      2:on    3:on    4:on    5:on
module-init- S:on
mountoverflo 0:off      6:off   S:on
networking   S:on
nvidia-kerne 1:off      2:on    3:on    4:on    5:on
pcmciautils  S:on
powernowd    1:off      2:on    3:on    4:on    5:on
powernowd.ea 2:on
pppd-dns     S:on
rc.local     2:on       3:on    4:on    5:on
readahead    S:on
readahead-de S:on
reboot       6:on
rmnologin    2:on       3:on    4:on    5:on
rsync        1:off      2:off   3:off   4:off   5:off
screen       S:on
sendsigs     0:on       6:on
single       1:on
ssh          1:off      2:on    3:on    4:on    5:on
stop-bootlog
stop-bootlog
stop-readahe 2:on
sysklogd     1:off      2:on    3:on    4:on    5:on
tomcat5.5    0:off      1:off   2:off   3:off   4:off   5:off   6:off
udev         S:on
udev-finish  S:on
umountfs     0:on       6:on
umountroot   0:on       6:on
urandom      0:on       6:on    S:on
usplash      0:off      1:off   2:on    3:on    4:on    5:on    6:off
vbesave      2:on       3:on    4:on    5:on
vmware       0:off      2:off   3:off   5:off   6:off
wpa-ifupdown 0:on       6:on
x11-common   S:on
xserver-xorg 2:on       3:on    4:on    5:on

```

---

### Post by ture_atlantis on 2008-02-14
The service that I disabled was 'rsync' 

When I re-enabled that, no more error.

---

