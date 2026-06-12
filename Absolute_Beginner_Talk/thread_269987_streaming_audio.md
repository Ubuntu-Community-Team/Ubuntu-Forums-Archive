---
title: "streaming audio"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by quanct on 2006-10-02
my streaming video works, my audio doesn't. for example, i can see the videos on youtube, but i can't hear them! and my regular audio for totem works fine. what is wrong?

---

### Post by klytu on 2006-10-02
> **quanct said:**
> my streaming video works, my audio doesn't. for example, i can see the videos on youtube, but i can't hear them! and my regular audio for totem works fine. what is wrong?

Are you using Firefox web browser? Is it just the specific site youtube that is not playing sound (I think that's based on Macromedia Flash ...) or do you have no sound on any streaming video when browsing?

---

### Post by quanct on 2006-10-02
> **klytu said:**
> Are you using Firefox web browser? Is it just the specific site youtube that is not playing sound (I think that's based on Macromedia Flash ...) or do you have no sound on any streaming video when browsing?

Yes, I'm using Firefox. 

And, no, I don't have sound on any streaming videos, for example, those on google video. Is that also based on Macromedia?

---

### Post by klytu on 2006-10-02
> **quanct said:**
> Yes, I'm using Firefox. 

And, no, I don't have sound on any streaming videos, for example, those on google video. Is that also based on Macromedia?

I think Google video is also based on Macromedia Flash. The reason for the question is that if you can get streaming sound on other web sites but just not for Flash specifically, there may be a different solution than if you can't get streaming sound in general in Firefox. 

It is generally best to go step by step when troubleshooting sound issues. A good guide can be found [here]("http://ubuntuforums.org/showthread.php?t=205449"). 

If you already have the package alsa-oss installed, for general streaming sound issues in Firefox you can try this:

```
sudo gedit /etc/firefox/firefoxrc
```

Change this line:

```
FIREFOX_DSP="none"
```

to this

```
FIREFOX_DSP="aoss"
```

save and restart Firefox and see if that helps.

If the problem is just with Flash videos and not general streaming sound in Firefox, there might be another sound process running that conflicts with the way Flash outputs sound. To troubleshoot this possibility you can try:

```
ps -ef
```

and try "kill"ing the process(es) that may be in conflict. If you need help trying any of this, post back and I'll try to help you.

---

### Post by quanct on 2006-10-02
> **klytu said:**
> 

If the problem is just with Flash videos and not general streaming sound in Firefox, there might be another sound process running that conflicts with the way Flash outputs sound. To troubleshoot this possibility you can try:

```
ps -ef
```

and try "kill"ing the process(es) that may be in conflict. If you need help trying any of this, post back and I'll try to help you.

How do I know which processes to kill?

---

### Post by klytu on 2006-10-02
> **quanct said:**
> How do I know which processes to kill?

Post the output of 

```
ps -ef
``` 

and I'll help you figure it out.

---

### Post by The Geoff on 2006-10-02
I'm having exactly the same problem - I'd used the fix involving gedit, which worked but then stopped.  I've tried it again in case something had changed (sorry, still used to Windows! *blush*), but no.




ps -ef output:



UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Oct02 ?        00:00:01 init [2]
root         2     1  0 Oct02 ?        00:00:00 [ksoftirqd/0]
root         3     1  0 Oct02 ?        00:00:00 [watchdog/0]
root         4     1  0 Oct02 ?        00:00:00 [events/0]
root         5     1  0 Oct02 ?        00:00:00 [khelper]
root         6     1  0 Oct02 ?        00:00:00 [kthread]
root         8     6  0 Oct02 ?        00:00:00 [kblockd/0]
root         9     6  0 Oct02 ?        00:00:00 [kacpid]
root       119     6  0 Oct02 ?        00:00:00 [pdflush]
root       120     6  0 Oct02 ?        00:00:00 [pdflush]
root       122     6  0 Oct02 ?        00:00:00 [aio/0]
root       121     1  0 Oct02 ?        00:00:00 [kswapd0]
root       709     6  0 Oct02 ?        00:00:00 [kseriod]
root      1808     6  0 Oct02 ?        00:00:00 [khubd]
root      1886     1  0 Oct02 ?        00:00:00 [kjournald]
root      2113     1  0 Oct02 ?        00:00:00 /sbin/udevd --daemon
root      2877     1  0 Oct02 ?        00:00:00 [shpchpd_event]
root      2972     6  0 Oct02 ?        00:00:00 [kgameportd]
dhcp      3158     1  0 Oct02 ?        00:00:00 dhclient3 -pf /var/run/dhclient.root      3804     1  0 Oct02 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/evesyslog    3897     1  0 Oct02 ?        00:00:00 /sbin/syslogd -u syslog
root      3923     1  0 Oct02 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /vklog      3925     1  0 Oct02 ?        00:00:00 /sbin/klogd -P /var/run/klogd/kmroot      4250     1  0 Oct02 ?        00:00:00 /usr/sbin/gdm
root      4262  4250  0 Oct02 ?        00:00:00 /usr/sbin/gdm
root      4284  4262  5 Oct02 tty7     00:07:44 /usr/bin/X :0 -br -audit 0 -authhplip     4291     1  0 Oct02 ?        00:00:00 /usr/sbin/hpiod
hplip     4297     1  0 Oct02 ?        00:00:00 python /usr/sbin/hpssd
cupsys    4344     1  0 Oct02 ?        00:00:00 /usr/sbin/cupsd
104       4387     1  0 Oct02 ?        00:00:00 /usr/bin/dbus-daemon --system
108       4402     1  0 Oct02 ?        00:00:01 /usr/sbin/hald
root      4403  4402  0 Oct02 ?        00:00:00 hald-runner
108       4408  4403  0 Oct02 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
108       4464  4403  0 Oct02 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard108       4474  4403  0 Oct02 ?        00:00:01 /usr/lib/hal/hald-addon-storage
108       4475  4403  0 Oct02 ?        00:00:01 /usr/lib/hal/hald-addon-storage
dictd     4486     1  0 Oct02 ?        00:00:00 dictd 1.10.2: 0/0
root      4660     1  0 Oct02 ?        00:00:00 /bin/sh /usr/bin/mysqld_safe
mysql     4728  4660  0 Oct02 ?        00:00:00 /usr/sbin/mysqld --basedir=/usr
root      4729  4660  0 Oct02 ?        00:00:00 logger -p daemon.err -t mysqld_sroot      4837     1  0 Oct02 ?        00:00:00 /usr/sbin/nmbd -D
root      4839     1  0 Oct02 ?        00:00:00 /usr/sbin/smbd -D
root      4845  4839  0 Oct02 ?        00:00:00 /usr/sbin/smbd -D
nobody    4847     1  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
nobody    4848  4847  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
nobody    4849  4847  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
nobody    4850  4847  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
nobody    4858  4847  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
nobody    4859  4847  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
nobody    4860  4847  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
nobody    4861  4847  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
nobody    4862  4847  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
nobody    4863  4847  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
nobody    4864  4847  0 Oct02 ?        00:00:00 /usr/sbin/tinyproxy
root      4927     1  0 Oct02 ?        00:00:00 hcid: processing events
root      4931     1  0 Oct02 ?        00:00:00 /usr/sbin/sdpd
root      4946     1  0 Oct02 ?        00:00:00 [krfcommd]
root      4959     1  0 Oct02 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadmdaemon    4993     1  0 Oct02 ?        00:00:00 /usr/sbin/atd
root      5006     1  0 Oct02 ?        00:00:00 /usr/sbin/cron
root      5051     1  0 Oct02 ?        00:00:00 /usr/sbin/apache2 -k start -DSSLroot      5120     1  0 Oct02 tty1     00:00:00 /sbin/getty 38400 tty1
root      5121     1  0 Oct02 tty2     00:00:00 /sbin/getty 38400 tty2
root      5122     1  0 Oct02 tty3     00:00:00 /sbin/getty 38400 tty3
root      5123     1  0 Oct02 tty4     00:00:00 /sbin/getty 38400 tty4
root      5124     1  0 Oct02 tty5     00:00:00 /sbin/getty 38400 tty5
root      5125     1  0 Oct02 tty6     00:00:00 /sbin/getty 38400 tty6
www-data  5136  5051  0 Oct02 ?        00:00:00 /usr/sbin/apache2 -k start -DSSLwww-data  5137  5051  0 Oct02 ?        00:00:00 /usr/sbin/apache2 -k start -DSSLwww-data  5138  5051  0 Oct02 ?        00:00:00 /usr/sbin/apache2 -k start -DSSLwww-data  5139  5051  0 Oct02 ?        00:00:00 /usr/sbin/apache2 -k start -DSSLwww-data  5140  5051  0 Oct02 ?        00:00:00 /usr/sbin/apache2 -k start -DSSLgeoff     5150  4262  0 Oct02 ?        00:00:01 x-session-manager
geoff     5192  5150  0 Oct02 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbusgeoff     5195     1  0 Oct02 ?        00:00:00 /usr/bin/dbus-launch --exit-withgeoff     5196     1  0 Oct02 ?        00:00:00 dbus-daemon --fork --print-pid 8geoff     5198     1  0 Oct02 ?        00:00:01 /usr/lib/libgconf2-4/gconfd-2 5
geoff     5201     1  0 Oct02 ?        00:00:00 /usr/bin/gnome-keyring-daemon
geoff     5203     1  0 Oct02 ?        00:00:00 /usr/lib/bonobo-activation/bonobgeoff     5205     1  0 Oct02 ?        00:00:03 /usr/lib/control-center/gnome-segeoff     5208     1  0 Oct02 ?        00:00:13 /usr/bin/metacity --sm-client-idgeoff     5215     1  0 Oct02 ?        00:00:14 gnome-panel --sm-client-id defaugeoff     5217     1  0 Oct02 ?        00:00:03 nautilus --no-default-window --sgeoff     5221     1  0 Oct02 ?        00:00:00 gnome-volume-manager --sm-clientgeoff     5231     1  0 Oct02 ?        00:00:01 update-notifier
geoff     5237     1  0 Oct02 ?        00:00:01 gnome-cups-icon --sm-client-id dgeoff     5240     1  0 Oct02 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfsgeoff     5244     1  0 Oct02 ?        00:00:00 gnome-power-manager
geoff     5253     1  0 Oct02 ?        00:00:00 /usr/lib/gnome-applets/trashapplgeoff     5260     1  0 Oct02 ?        00:00:00 /usr/lib/nautilus-cd-burner/mappgeoff     5272     1  0 Oct02 ?        00:00:01 /usr/lib/gnome-panel/clock-applegeoff     5274     1  0 Oct02 ?        00:00:03 /usr/lib/gnome-applets/stickynotgeoff     5276     1  0 Oct02 ?        00:00:01 /usr/lib/gnome-applets/gweather-geoff     5291     1  0 Oct02 ?        00:00:03 gnome-screensaver
geoff     5454     1  9 Oct02 ?        00:11:33 /usr/lib/firefox/firefox-bin -a
geoff     5511     1  0 Oct02 ?        00:00:00 /usr/lib/evolution/evolution-datgeoff     5524     1  0 Oct02 ?        00:00:00 /usr/lib/evolution/2.6/evolutiongeoff     8401     1  0 01:00 ?        00:00:00 /bin/sh /usr/bin/mozilla-thundergeoff     8407  8401  0 01:00 ?        00:00:00 /bin/sh /usr/lib/mozilla-thundergeoff     8412  8407  0 01:00 ?        00:00:05 /usr/lib/mozilla-thunderbird/mozgeoff     8425  8412  0 01:00 ?        00:00:00 [netstat] <defunct>
geoff     8927     1 18 01:16 ?        00:00:00 gnome-terminal
geoff     8930  8927  0 01:16 ?        00:00:00 gnome-pty-helper
geoff     8931  8927  9 01:16 pts/0    00:00:00 bash
geoff     8949  8931  0 01:16 pts/0    00:00:00 ps -ef

---

### Post by quanct on 2006-10-02
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Oct01 ?        00:00:01 init [2]
root         2     1  0 Oct01 ?        00:00:00 [ksoftirqd/0]
root         3     1  0 Oct01 ?        00:00:00 [watchdog/0]
root         4     1  0 Oct01 ?        00:00:00 [events/0]
root         5     1  0 Oct01 ?        00:00:00 [khelper]
root         6     1  0 Oct01 ?        00:00:00 [kthread]
root         8     6  0 Oct01 ?        00:00:00 [kblockd/0]
root         9     6  0 Oct01 ?        00:00:00 [kacpid]
root       122     6  0 Oct01 ?        00:00:00 [pdflush]
root       123     6  0 Oct01 ?        00:00:00 [pdflush]
root       125     6  0 Oct01 ?        00:00:00 [aio/0]
root       124     1  0 Oct01 ?        00:00:00 [kswapd0]
root       712     6  0 Oct01 ?        00:00:00 [kseriod]
root      1807     6  0 Oct01 ?        00:00:00 [khubd]
root      1828     1  0 Oct01 ?        00:00:00 [khpsbpkt]
root      1853     1  0 Oct01 ?        00:00:00 [knodemgrd_0]
root      1928     1  0 Oct01 ?        00:00:00 [kjournald]
root      2157     1  0 Oct01 ?        00:00:00 /sbin/udevd --daemon
root      3091     1  0 Oct01 ?        00:00:00 [pccardd]
root      3092     1  0 Oct01 ?        00:00:00 [pccardd]
root      3756     6  0 Oct01 ?        00:00:00 [kacpid-work-0]
root      3981     1  0 Oct01 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      3983     1  0 Oct01 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
root      4302     1  0 Oct01 ?        00:00:00 /usr/sbin/gdm
root      4318  4302  0 Oct01 ?        00:00:00 /usr/sbin/gdm
root      4336  4318  1 Oct01 tty7     00:15:15 /usr/bin/X :0 -br -audit 0 -auth
hplip     4345     1  0 Oct01 ?        00:00:00 /usr/sbin/hpiod
hplip     4370     1  0 Oct01 ?        00:00:00 python /usr/sbin/hpssd
104       4443     1  0 Oct01 ?        00:00:01 /usr/bin/dbus-daemon --system
108       4458     1  0 Oct01 ?        00:00:02 /usr/sbin/hald
root      4459  4458  0 Oct01 ?        00:00:00 hald-runner
108       4464  4459  0 Oct01 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
108       4520  4459  0 Oct01 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
108       4528  4459  0 Oct01 ?        00:00:03 /usr/lib/hal/hald-addon-storage
108       4529  4459  0 Oct01 ?        00:00:02 /usr/lib/hal/hald-addon-storage
root      4568     1  0 Oct01 ?        00:00:00 /usr/sbin/powernowd -q
ntp       4613     1  0 Oct01 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.
root      4631     1  0 Oct01 ?        00:00:00 hcid: processing events
root      4639     1  0 Oct01 ?        00:00:00 /usr/sbin/sdpd
root      4654     1  0 Oct01 ?        00:00:00 [krfcommd]
root      4667     1  0 Oct01 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadm
daemon    4702     1  0 Oct01 ?        00:00:00 /usr/sbin/atd
root      4715     1  0 Oct01 ?        00:00:00 /usr/sbin/cron
root      4794     1  0 Oct01 tty1     00:00:00 /sbin/getty 38400 tty1
root      4795     1  0 Oct01 tty2     00:00:00 /sbin/getty 38400 tty2
root      4796     1  0 Oct01 tty3     00:00:00 /sbin/getty 38400 tty3
root      4797     1  0 Oct01 tty4     00:00:00 /sbin/getty 38400 tty4
root      4798     1  0 Oct01 tty5     00:00:00 /sbin/getty 38400 tty5
root      4799     1  0 Oct01 tty6     00:00:00 /sbin/getty 38400 tty6
chris     4814  4318  0 Oct01 ?        00:00:04 x-session-manager
chris     4856  4814  0 Oct01 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
chris     4859     1  0 Oct01 ?        00:00:00 /usr/bin/dbus-launch --exit-with
chris     4860     1  0 Oct01 ?        00:00:00 dbus-daemon --fork --print-pid 8
chris     4862     1  0 Oct01 ?        00:00:02 /usr/lib/libgconf2-4/gconfd-2 5
chris     4865     1  0 Oct01 ?        00:00:00 /usr/bin/gnome-keyring-daemon
chris     4867     1  0 Oct01 ?        00:00:00 /usr/lib/bonobo-activation/bonob
chris     4869     1  0 Oct01 ?        00:00:05 /usr/lib/control-center/gnome-se
root      4872  4613  0 Oct01 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.
chris     4875     1  0 Oct01 ?        00:00:00 /usr/bin/esd -nobeeps
chris     4881     1  0 Oct01 ?        00:00:00 /usr/bin/esd -nobeeps
chris     4884     1  0 Oct01 ?        00:01:39 metacity --sm-save-file 11597526
chris     4888     1  0 Oct01 ?        00:00:33 gnome-panel --sm-config-prefix /
chris     4890     1  0 Oct01 ?        00:00:30 nautilus --sm-config-prefix /nau
chris     4891     1  0 Oct01 ?        00:00:01 gnome-volume-manager --sm-config
chris     4897     1  0 Oct01 ?        00:00:02 update-notifier --sm-config-pref
chris     4901     1  0 Oct01 ?        00:00:01 gnome-cups-icon --sm-config-pref
chris     4904     1  0 Oct01 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs
chris     4919     1  0 Oct01 ?        00:00:01 /usr/lib/gnome-applets/trashappl
chris     4922     1  0 Oct01 ?        00:00:03 gnome-power-manager --sm-config-
chris     4926     1  0 Oct01 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapp
chris     4937     1  0 Oct01 ?        00:00:01 /usr/lib/gnome-applets/battstat-
chris     4939     1  0 Oct01 ?        00:00:04 /usr/lib/gnome-netstatus/gnome-n
chris     4941     1  0 Oct01 ?        00:00:02 /usr/lib/gnome-applets/mixer_app
chris     4943     1  0 Oct01 ?        00:00:01 /usr/lib/gnome-panel/clock-apple
chris     4962     1  0 Oct01 ?        00:00:06 gnome-screensaver
chris     5322     1  0 Oct01 ?        00:00:02 /usr/bin/artsd -F 10 -S 4096 -s
root      5674     1  0 Oct01 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
cupsys    5708     1  0 Oct01 ?        00:00:00 /usr/sbin/cupsd
syslog    5800     1  0 Oct01 ?        00:00:00 /sbin/syslogd -u syslog
root      6908     6  0 Oct01 ?        00:00:00 [kacpid-work-1]
root      6909     6  0 Oct01 ?        00:00:00 [kacpid-work-2]
root      6910     6  0 Oct01 ?        00:00:00 [kacpid-work-3]
root      6911     6  0 Oct01 ?        00:00:00 [kacpid-work-4]
root      6912     6  0 Oct01 ?        00:00:00 [kacpid-work-5]
root      6913     6  0 Oct01 ?        00:00:00 [kacpid-work-6]
chris     6947     1  0 Oct01 ?        00:00:05 /usr/lib/notification-daemon/not
root      7646     6  0 09:54 ?        00:00:00 [ipw2200/0]
dhcp      7835     1  0 09:55 ?        00:00:00 dhclient3 -pf /var/run/dhclient.
dhcp      8576     1  0 10:03 ?        00:00:00 dhclient3 -pf /var/run/dhclient.
root      9165     6  0 10:24 ?        00:00:00 [kacpid-work-7]
chris    11325     1  0 11:21 ?        00:00:00 mplayer -wid 0x1a2119f -xy 320 -
chris    11326     1  0 11:21 ?        00:00:00 mplayer -wid 0x1a2124d -xy 320 -
chris    11327 11325  0 11:21 ?        00:00:00 mplayer -wid 0x1a2119f -xy 320 -
chris    11328 11326  0 11:21 ?        00:00:00 mplayer -wid 0x1a2124d -xy 320 -
chris    19309     1  3 15:27 ?        00:04:48 /usr/lib/firefox/firefox-bin -a
chris    19342     1  0 15:28 ?        00:00:05 gnome-terminal
chris    19343 19342  0 15:28 ?        00:00:00 gnome-pty-helper
chris    19344 19342  0 15:28 pts/0    00:00:00 bash
chris    22793     1 23 17:34 ?        00:00:14 totem file:///home/chris/Desktop
chris    22836 19344  0 17:35 pts/0    00:00:00 ps -ef

---

### Post by klytu on 2006-10-02
Quanct:

Try first

```
sudo killall artsd
```

restart firefox and see if streaming sound is OK.

If not then try

```
sudo killall esd
```

restart firefox and check streaming sound. 

If this works, the problem may occur again later and you'll need to do the same thing again if it does. I was able to work around this particular problem by not using system sounds in Gnome and by turning off sound on KDE apps that run in Gnome. If I figure out a better way, I'll post it.

Geoff:

I didn't see any obvious (to me) sound process conflicts in your output. I had updated to Dapper from Breezy. In Breezy I had NO sound problems whatsoever. A lot of recurring sound issues I had in Dapper cleared up when I reinstalled the sound subsystem. The procedure is mentioned in the link I posted earlier, which may be of help to you:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Sambie on 2006-10-03
> **klytu said:**
> Quanct:

Try first

```
sudo killall artsd
```

restart firefox and see if streaming sound is OK.

If not then try

```
sudo killall esd
```

restart firefox and check streaming sound. 

If this works, the problem may occur again later and you'll need to do the same thing again if it does. I was able to work around this particular problem by not using system sounds in Gnome and by turning off sound on KDE apps that run in Gnome. If I figure out a better way, I'll post it.

Geoff:

I didn't see any obvious (to me) sound process conflicts in your output. I had updated to Dapper from Breezy. In Breezy I had NO sound problems whatsoever. A lot of recurring sound issues I had in Dapper cleared up when I reinstalled the sound subsystem. The procedure is mentioned in the link I posted earlier, which may be of help to you:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

thank you so much! you've helped to solve my problem :)

thanks again!

---

### Post by quanct on 2006-10-03
> **klytu said:**
> Quanct:

Try first

```
sudo killall artsd
```

restart firefox and see if streaming sound is OK.

If not then try

```
sudo killall esd
```

restart firefox and check streaming sound. 

If this works, the problem may occur again later and you'll need to do the same thing again if it does. I was able to work around this particular problem by not using system sounds in Gnome and by turning off sound on KDE apps that run in Gnome. If I figure out a better way, I'll post it.

Geoff:

I didn't see any obvious (to me) sound process conflicts in your output. I had updated to Dapper from Breezy. In Breezy I had NO sound problems whatsoever. A lot of recurring sound issues I had in Dapper cleared up when I reinstalled the sound subsystem. The procedure is mentioned in the link I posted earlier, which may be of help to you:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

It worked! Thank you so much!!

---

### Post by The Geoff on 2006-10-20
I've no idea how or why, but my problem has been solved by installing the Flash9 beta.  Plugin problem I'm guessing, but it works now.

---

