---
title: "Gnome terminal"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-05-26
When I input a command like, say, netstat, the output is so long that the terminal cuts off everything at the top, which doesn't make sense as I can't see what the first part of the output is...Is there a way to increase the output length or memory space or history something on the gnome terminal? (so that I can see the whole output)

---

### Post by Ek0nomik on 2007-05-26
Edit/Current Profile/Scrolling

---

### Post by Ek0nomik on 2007-05-26
You can also use grep to scan your output and only return the wanted results.

Ex:

```
sudo fdisk -l | grep sdb
```

This would only show lines of text with sdb, and could be useful if I only want to look at that drive.

Basically think of grep as a filter.

---

### Post by dbott67 on 2007-05-26
Or pipe the output to "more" (which pauses after 1 page of output).  Press the SPACE BAR to move to the next page:
```
dbott@feisty:~$ [COLOR=Red]**netstat | more**[/COLOR]
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        1      0 feisty.local:33642      192.168.1.2:netbios-ssn CLOSE_WAIT
tcp        1      0 feisty.local:33644      192.168.1.2:netbios-ssn CLOSE_WAIT
tcp6       0      0 ::ffff:192.168.1.10:ssh ns.stcatharines.li:2339 ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    7781     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    7996     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    15400    @/org/freedesktop/hal/udev_event
unix  12     [ ]         DGRAM                    15285    /dev/log
unix  2      [ ]         DGRAM                    94382
unix  3      [ ]         STREAM     CONNECTED     94379
unix  3      [ ]         STREAM     CONNECTED     94378
unix  3      [ ]         STREAM     CONNECTED     92849    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     92848
unix  3      [ ]         STREAM     CONNECTED     92735    /tmp/orbit-dbott/linc-47af-0-3ce35105e7a67
unix  3      [ ]         STREAM     CONNECTED     92734
unix  3      [ ]         STREAM     CONNECTED     92731    /tmp/orbit-dbott/linc-150e-0-34608aab87474
unix  3      [ ]         STREAM     CONNECTED     92730
unix  3      [ ]         STREAM     CONNECTED     92719    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     92718
unix  3      [ ]         STREAM     CONNECTED     76970    /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     76969
unix  2      [ ]         STREAM                   68068
unix  3      [ ]         STREAM     CONNECTED     54912    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     54911
unix  3      [ ]         STREAM     CONNECTED     52131    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     52130
unix  3      [ ]         STREAM     CONNECTED     52129    @/tmp/dbus-NOLcvcczKq
unix  3      [ ]         STREAM     CONNECTED     52128
unix  3      [ ]         STREAM     CONNECTED     52127    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     52126
unix  3      [ ]         STREAM     CONNECTED     52125    /tmp/orbit-dbott/linc-7ca1-0-45642054c6dbb
unix  3      [ ]         STREAM     CONNECTED     52124
unix  3      [ ]         STREAM     CONNECTED     52121    /tmp/orbit-dbott/linc-150e-0-34608aab87474
unix  3      [ ]         STREAM     CONNECTED     19374
unix  3      [ ]         STREAM     CONNECTED     19373    /tmp/orbit-dbott/linc-1520-0-165a828f8466b
--More--

```-Dave

---

### Post by arijarot on 2007-05-26
Thank you guys! 

(what does "pipe" mean, Dave?)

---

### Post by Bachstelze on 2007-05-26
It means redirecting the output of a command to the input of another, like this :

```
netstat | less
```

---

### Post by arijarot on 2007-05-26
> **HymnToLife said:**
> It means redirecting the output of a command to the input of another, like this :

```
netstat | less
```

Thanks:)

---

### Post by dbott67 on 2007-05-26
> **arijarot said:**
> Thank you guys! 

(what does "pipe" mean, Dave?)

It means "take the output of the first command and send it as input to the second command".

Suppose I have a really large file and I want to look for all the instances of the word "foo", I would pipe the output of the file to grep and then have grep locate the term:

```
cat /path/to/file | grep foo
```So, if I wanted to list all processes, I could use the following command:
```
dbott@feisty:~$ [COLOR=Red]**ps aux**[/COLOR]
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   2912  1848 ?        Ss   May22   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    May22   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   May22   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    May22   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   May22   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   May22   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   May22   0:00 [kthread]
root        30  0.0  0.0      0     0 ?        S<   May22   0:00 [kblockd/0]
root        31  0.0  0.0      0     0 ?        S<   May22   0:00 [kacpid]
root        32  0.0  0.0      0     0 ?        S<   May22   0:00 [kacpi_notify]
root       110  0.0  0.0      0     0 ?        S<   May22   0:00 [kseriod]
root       131  0.0  0.0      0     0 ?        S    May22   0:00 [pdflush]
root       132  0.0  0.0      0     0 ?        S    May22   0:00 [pdflush]
root       133  0.0  0.0      0     0 ?        S<   May22   0:00 [kswapd0]
root       134  0.0  0.0      0     0 ?        S<   May22   0:00 [aio/0]
root      1933  0.0  0.0      0     0 ?        S<   May22   0:01 [ata/0]
root      1934  0.0  0.0      0     0 ?        S<   May22   0:00 [ata_aux]
root      1937  0.0  0.0      0     0 ?        S<   May22   0:00 [scsi_eh_0]
root      1938  0.0  0.0      0     0 ?        S<   May22   0:00 [scsi_eh_1]
root      1940  0.0  0.0      0     0 ?        S<   May22   0:00 [ksuspend_usbd]
root      1941  0.0  0.0      0     0 ?        S<   May22   0:00 [khubd]
root      2219  0.0  0.0      0     0 ?        S<   May22   0:01 [kjournald]
root      2419  0.0  0.1   2872  1216 ?        S<s  May22   0:00 /sbin/udevd --daemon
dbott     2677  0.0  1.5  53844 14108 ?        Sl   May24   2:15 beep-media-player
root      3321  0.0  0.0      0     0 ?        S<   May22   0:00 [kgameportd]
root      3849  0.0  0.0      0     0 ?        S<   May22   0:00 [kjournald]
root      4154  0.0  0.0   1648   508 tty4     Ss+  May22   0:00 /sbin/getty 38400 tty4
root      4155  0.0  0.0   1648   508 tty5     Ss+  May22   0:00 /sbin/getty 38400 tty5
root      4158  0.0  0.0   1648   508 tty2     Ss+  May22   0:00 /sbin/getty 38400 tty2
root      4160  0.0  0.0   1648   508 tty3     Ss+  May22   0:00 /sbin/getty 38400 tty3
root      4161  0.0  0.0   1652   512 tty1     Ss+  May22   0:00 /sbin/getty 38400 tty1
root      4162  0.0  0.0   1652   512 tty6     Ss+  May22   0:00 /sbin/getty 38400 tty6
root      4406  0.0  0.1   2260  1176 ?        Ss   May22   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4512  0.0  0.0   1700   660 ?        Ss   May22   0:00 /sbin/syslogd
root      4568  0.0  0.0   1796   528 ?        Ss   May22   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4570  0.0  0.1   2424  1372 ?        Ss   May22   0:00 /sbin/klogd -P /var/run/klogd/kmsg
103       4591  0.0  0.1   2976  1172 ?        Ss   May22   0:01 /usr/bin/dbus-daemon --system
107       4607  0.0  0.4   5456  3760 ?        Ss   May22   0:02 /usr/sbin/hald
root      4608  0.0  0.1   2872  1016 ?        S    May22   0:00 hald-runner
107       4614  0.0  0.0   2108   904 ?        S    May22   0:00 hald-addon-keyboard: listening on /dev/input/event1
107       4615  0.0  0.0   2104   896 ?        S    May22   0:00 hald-addon-keyboard: listening on /dev/input/event4
107       4616  0.0  0.0   2104   896 ?        S    May22   0:00 hald-addon-keyboard: listening on /dev/input/event5
107       4619  0.0  0.0   2104   888 ?        S    May22   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       4629  0.0  0.1   3040  1220 ?        S    May22   0:11 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      4643  0.0  0.0   1936   840 ?        Ss   May22   0:01 /usr/sbin/dhcdbd --system
root      4658  0.0  0.2  12332  1964 ?        Ssl  May22   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
avahi     4676  0.0  0.1   2796  1404 ?        Ss   May22   0:00 avahi-daemon: registering [feisty.local]
avahi     4677  0.0  0.0   2664   460 ?        Ss   May22   0:00 avahi-daemon: chroot helper
root      4693  0.0  0.1   3052  1264 ?        Ss   May22   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      4706  0.0  0.0   2864   800 ?        Ss   May22   0:00 /usr/bin/system-tools-backends
root      4707  0.0  0.1   2720  1228 ?        S    May22   0:00 dbus-daemon --session --print-address --nofork
root      4744  0.0  0.1  12296  1412 ?        Ss   May22   0:00 /usr/sbin/gdm
root      4762  0.0  0.2  12676  2496 ?        S    May22   0:00 /usr/sbin/gdm
root      4765  1.7  6.9  76460 62548 tty7     SLs+ May22  97:07 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
dhcp      4789  0.0  0.1   2456  1212 ?        S    May22   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
root      4842  0.0  0.0   6416   836 ?        Ss   May22   0:00 /usr/sbin/hpiod
hplip     4866  0.0  0.5   9980  4888 ?        S    May22   0:00 python /usr/sbin/hpssd
root      4945  0.0  0.1   6104  1360 ?        Ss   May22   0:00 /sbin/mount.smbfs //192.168.1.2/Music /home/dbott/music -o rw noexec nosuid nodev user credentials /root/.credentials uid 1000 umask
root      4952  0.0  0.0      0     0 ?        S<   May22   0:02 [smbiod]
root      4956  0.0  0.1   6100  1360 ?        Ss   May22   0:00 /sbin/mount.smbfs //192.168.1.2/Data /home/dbott/data -o rw noexec nosuid nodev user credentials /root/.credentials uid 1000 umask 0
root      4959  0.0  0.1   6104  1360 ?        Ss   May22   0:00 /sbin/mount.smbfs //192.168.1.2/Archive /home/dbott/archive1 -o rw noexec nosuid nodev user credentials /root/.credentials uid 1000
root      4971  0.0  0.4   7888  4368 ?        S    May22   0:00 python /usr/sbin/denyhosts --daemon --config=/etc/denyhosts.conf --config=/etc/denyhosts.conf
root      5016  0.0  0.1   6040  1276 ?        Ss   May22   0:17 /usr/sbin/nmbd -D
root      5018  0.0  0.2   9292  2240 ?        Ss   May22   0:00 /usr/sbin/smbd -D
root      5026  0.0  0.1   9292  1044 ?        S    May22   0:00 /usr/sbin/smbd -D
root      5038  0.0  0.1   5084   972 ?        Ss   May22   0:00 /usr/sbin/sshd
root      5087  0.0  0.1   2696  1004 ?        Ss   May22   0:00 /usr/sbin/hcid -x -s
root      5104  0.0  0.0      0     0 ?        S<   May22   0:00 [krfcommd]
daemon    5139  0.0  0.0   1908   420 ?        Ss   May22   0:00 /usr/sbin/atd
root      5153  0.0  0.0   2284   900 ?        Ss   May22   0:00 /usr/sbin/cron
root      5209  0.0  0.5  13212  5260 ?        Ss   May22   0:03 /usr/sbin/apache2 -k start
www-data  5210  0.0  0.3  12452  3276 ?        S    May22   0:00 /usr/sbin/apache2 -k start
www-data  5212  0.0  0.4 234552  4096 ?        Sl   May22   0:00 /usr/sbin/apache2 -k start
www-data  5214  0.0  0.4 234552  4100 ?        Sl   May22   0:00 /usr/sbin/apache2 -k start
dbott     5345  0.0  1.2  30852 11696 ?        Ssl  May22   0:00 /usr/bin/gnome-session
dbott     5384  0.0  0.0   4256   572 ?        Ss   May22   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
dbott     5387  0.0  0.0   2660   636 ?        S    May22   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
dbott     5388  0.0  0.1   2852  1076 ?        Ss   May22   0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --session
dbott     5390  0.0  0.4   6944  4440 ?        S    May22   0:01 /usr/lib/libgconf2-4/gconfd-2 6
dbott     5393  0.0  0.1   2752  1008 ?        S    May22   0:00 /usr/bin/gnome-keyring-daemon
dbott     5395  0.0  1.1  29928 10228 ?        Sl   May22   0:15 /usr/lib/control-center/gnome-settings-daemon
dbott     5402  0.0  0.0   1716   484 ?        Ss   May22   0:00 /bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
dbott     5403  0.0  0.3   4688  2992 ?        S    May22   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
dbott     5408  0.0  0.3  39716  3220 ?        Ssl  May22   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=21
dbott     5413  0.0  0.6  15844  5468 ?        S    May22   0:01 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=17
dbott     5414  0.0  1.1  17600 10508 ?        S    May22   1:41 /usr/bin/metacity --sm-client-id=default0
dbott     5417  0.0  2.7  66504 25020 ?        S    May22   2:17 gnome-panel --sm-client-id default1
dbott     5423  0.0  3.4 103692 31264 ?        S    May22   0:18 nautilus --no-default-window --sm-client-id default2
dbott     5428  0.0  0.3   8512  3540 ?        S    May22   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
dbott     5429  0.0  0.5  19068  4896 ?        Ss   May22   0:01 gnome-volume-manager --sm-client-id default4
dbott     5431  0.0  1.4  53944 12956 ?        S    May22   0:02 update-notifier
dbott     5440  0.0  1.3  85904 11788 ?        S    May22   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=21
dbott     5456  0.0  1.1  68472 10064 ?        Sl   May22   0:00 /usr/lib/evolution/2.10/evolution-alarm-notify
dbott     5475  0.0  1.5  53136 13744 ?        S    May22   0:04 nm-applet --sm-disable
dbott     5478  0.0  0.9  49500  8404 ?        S    May22   4:44 gnome-cups-icon --sm-client-id default3
dbott     5479  0.0  0.6  50896  6296 ?        Ss   May22   0:03 gnome-power-manager
dbott     5492  0.0  0.0   2460   888 ?        S    May22   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
dbott     5496  0.0  1.0  51000  9568 ?        S    May22   0:00 /usr/lib/gnome-applets/drivemount_applet2 --oaf-activate-iid=OAFIID:GNOME_DriveMountApplet_Factory --oaf-ior-fd=22
dbott     5504  0.0  1.0  36672  9620 ?        Sl   May22   0:00 /usr/lib/evolution/2.10/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf
dbott     5507  0.0  1.4  54848 13312 ?        S    May22   0:11 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=33
dbott     5531  0.0  0.6  58512  6332 ?        Sl   May22   0:00 /usr/lib/evolution/evolution-data-server-1.10 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=31
dbott     5569  0.0  1.1  49976 10848 ?        S    May22   0:14 /usr/lib/notification-daemon/notification-daemon
dbott     5573  0.0  0.2  16112  2452 ?        Ss   May22   2:10 gnome-screensaver
cupsys   13821  0.0  0.2   4712  2088 ?        SNs  May25   1:09 /usr/sbin/cupsd
dbott    18351  0.3 10.0 209580 91140 ?        Sl   07:15   1:03 /usr/lib/firefox/firefox-bin
nxadmin  19952  0.0  0.1   3048  1320 ?        S    May24   0:00 /usr/bin/esd -nobeeps
root     22536  0.0  0.2   7876  2408 ?        Ss   09:05   0:00 sshd: dbott [priv]
dbott    22550  0.0  0.1   8032  1668 ?        S    09:05   0:00 sshd: dbott@pts/0
dbott    22551  0.0  0.3   5624  3148 pts/0    Ss   09:05   0:00 -bash
root     28354  0.0  0.2   7880  2380 ?        Ss   11:44   0:00 sshd: nx [priv]
nx       28359  0.0  0.1   8032  1564 ?        S    11:44   0:00 sshd: nx@notty
nx       28360  0.0  2.7  27216 25184 ?        Ss   11:44   0:00 nxserver -c /usr/NX/bin/nxserver --login
nx       28372  0.0  0.2   5140  2252 ?        S    11:44   0:00 /usr/NX/bin/nxssh -nxservermode -l nxadmin localhost -p 22 -x -2 -i /usr/NX/etc/keys/node.localhost.id_dsa -o PubkeyAuthentication y
root     28373  0.0  0.2   7840  2308 ?        Ss   11:44   0:00 sshd: nxadmin [priv]
nxadmin  28375  0.0  0.1   7840  1444 ?        S    11:44   0:00 sshd: nxadmin@notty
nxadmin  28376  0.0  1.2  12900 11476 ?        Ss   11:44   0:01 /usr/NX/bin/nxnode
nxadmin  28393  0.6  4.2  54080 38276 ?        S    11:44   0:10 /usr/NX/bin/nxagent -D -options /home/nxadmin/.nx/C-feisty-1027-33264FD7F93BDF7DCE07E4F761A63E1C/options -name NX - nxadmin@feisty:1
nx       28396  0.0  1.6  27200 14844 ?        S    11:44   0:00 nxserver -c /usr/NX/bin/nxserver --login
nx       28397  0.0  0.1   5136  1648 ?        S    11:44   0:00 /usr/NX/bin/nxssh -B -E
nxadmin  28399  0.0  0.7  13040  7240 ?        S    11:44   0:00 /usr/NX/bin/nxnode
nxadmin  28411  0.0  1.2  30888 11656 ?        Sl   11:44   0:00 gnome-session
nxadmin  28414  0.0  0.0   2664   632 ?        S    11:44   0:00 /usr/bin/dbus-launch --exit-with-session gnome-session
nxadmin  28415  0.0  0.1   2852  1012 ?        Ss   11:44   0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 6 --session
nxadmin  28417  0.0  0.4   6892  4376 ?        S    11:44   0:00 /usr/lib/libgconf2-4/gconfd-2 5
nxadmin  28420  0.0  0.1   2756  1004 ?        S    11:44   0:00 /usr/bin/gnome-keyring-daemon
nxadmin  28422  0.0  1.1  30012 10300 ?        Sl   11:44   0:00 /usr/lib/control-center/gnome-settings-daemon
nxadmin  28436  0.0  1.0  16176  9092 ?        S    11:44   0:00 /usr/bin/metacity --sm-client-id=default0
nxadmin  28438  0.1  2.0  62740 18660 ?        S    11:44   0:02 gnome-panel --sm-client-id default1
nxadmin  28439  0.0  2.0  96340 18508 ?        S    11:44   0:01 nautilus --no-default-window --sm-client-id default2
nxadmin  28444  0.0  0.3  39724  3148 ?        Ssl  11:44   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
nxadmin  28446  0.0  0.3   8508  3492 ?        S    11:44   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
nxadmin  28447  0.0  0.5  19060  4924 ?        Ss   11:44   0:00 gnome-volume-manager --sm-client-id default4
nxadmin  28453  0.0  1.4  53872 12988 ?        S    11:44   0:00 update-notifier
nxadmin  28455  0.0  1.0  27340  9560 ?        Sl   11:44   0:00 /usr/lib/evolution/2.10/evolution-alarm-notify
nxadmin  28460  0.0  1.2  51152 11376 ?        S    11:44   0:00 nm-applet --sm-disable
nxadmin  28461  0.1  0.9  48464  8356 ?        S    11:44   0:01 gnome-cups-icon --sm-client-id default3
nxadmin  28467  0.0  0.7  50952  6576 ?        Ss   11:44   0:00 gnome-power-manager
nxadmin  28505  0.0  0.4  16212  4392 ?        Ss   11:44   0:00 gnome-screensaver
nxadmin  28529  0.0  1.4  54896 13172 ?        S    11:45   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=23
nxadmin  28543  0.0  0.0   2460   880 ?        S    11:45   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
nxadmin  28552  0.0  1.1  49448 10428 ?        S    11:45   0:00 /usr/lib/notification-daemon/notification-daemon
dbott    30483  0.0  0.1   2560   996 pts/0    R+   12:11   0:00 ps aux
dbott    31905  0.0  3.6  87904 33384 ?        Sl   May24   0:05 mono /usr/lib/tomboy/Tomboy.exe

```WOW! THAT LIST IS HUGE!  What if I only want to see processes that [COLOR=Red]dbott[/COLOR] is using?
```
dbott@feisty:~$ ps aux | grep dbott
dbott     2677  0.0  1.5  53844 14108 ?        Sl   May24   2:15 beep-media-player
root      4945  0.0  0.1   6104  1360 ?        Ss   May22   0:00 /sbin/mount.smbfs //192.168.1.2/Music /home/dbott/music -o rw noexec nosuid nodev user credentials /root/.credentials uid 1000 umask 000
root      4956  0.0  0.1   6100  1360 ?        Ss   May22   0:00 /sbin/mount.smbfs //192.168.1.2/Data /home/dbott/data -o rw noexec nosuid nodev user credentials /root/.credentials uid 1000 umask 000
root      4959  0.0  0.1   6104  1360 ?        Ss   May22   0:00 /sbin/mount.smbfs //192.168.1.2/Archive /home/dbott/archive1 -o rw noexec nosuid nodev user credentials /root/.credentials uid 1000 umask 000
dbott     5345  0.0  1.2  30852 11696 ?        Ssl  May22   0:00 /usr/bin/gnome-session
dbott     5384  0.0  0.0   4256   572 ?        Ss   May22   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
dbott     5387  0.0  0.0   2660   636 ?        S    May22   0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
dbott     5388  0.0  0.1   2852  1076 ?        Ss   May22   0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --session
dbott     5390  0.0  0.4   6944  4440 ?        S    May22   0:01 /usr/lib/libgconf2-4/gconfd-2 6
dbott     5393  0.0  0.1   2752  1008 ?        S    May22   0:00 /usr/bin/gnome-keyring-daemon
dbott     5395  0.0  1.1  29928 10228 ?        Sl   May22   0:15 /usr/lib/control-center/gnome-settings-daemon
dbott     5402  0.0  0.0   1716   484 ?        Ss   May22   0:00 /bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
dbott     5403  0.0  0.3   4688  2992 ?        S    May22   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
dbott     5408  0.0  0.3  39716  3220 ?        Ssl  May22   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=21
dbott     5413  0.0  0.6  15844  5468 ?        S    May22   0:01 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=17
dbott     5414  0.0  1.1  17600 10508 ?        S    May22   1:41 /usr/bin/metacity --sm-client-id=default0
dbott     5417  0.0  2.7  66504 25020 ?        S    May22   2:17 gnome-panel --sm-client-id default1
dbott     5423  0.0  3.4 103692 31264 ?        S    May22   0:18 nautilus --no-default-window --sm-client-id default2
dbott     5428  0.0  0.3   8512  3540 ?        S    May22   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
dbott     5429  0.0  0.5  19068  4896 ?        Ss   May22   0:01 gnome-volume-manager --sm-client-id default4
dbott     5431  0.0  1.4  53944 12956 ?        S    May22   0:02 update-notifier
dbott     5440  0.0  1.3  85904 11788 ?        S    May22   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=21
dbott     5456  0.0  1.1  68472 10064 ?        Sl   May22   0:00 /usr/lib/evolution/2.10/evolution-alarm-notify
dbott     5475  0.0  1.5  53136 13744 ?        S    May22   0:04 nm-applet --sm-disable
dbott     5478  0.0  0.9  49500  8404 ?        S    May22   4:44 gnome-cups-icon --sm-client-id default3
dbott     5479  0.0  0.6  50896  6296 ?        Ss   May22   0:03 gnome-power-manager
dbott     5492  0.0  0.0   2460   888 ?        S    May22   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
dbott     5496  0.0  1.0  51000  9568 ?        S    May22   0:00 /usr/lib/gnome-applets/drivemount_applet2 --oaf-activate-iid=OAFIID:GNOME_DriveMountApplet_Factory --oaf-ior-fd=22
dbott     5504  0.0  1.0  36672  9620 ?        Sl   May22   0:00 /usr/lib/evolution/2.10/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=30
dbott     5507  0.0  1.4  54848 13312 ?        S    May22   0:11 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=33
dbott     5531  0.0  0.6  58512  6332 ?        Sl   May22   0:00 /usr/lib/evolution/evolution-data-server-1.10 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=31
dbott     5569  0.0  1.1  49976 10848 ?        S    May22   0:14 /usr/lib/notification-daemon/notification-daemon
dbott     5573  0.0  0.2  16112  2452 ?        Ss   May22   2:10 gnome-screensaver
dbott    18351  0.3 10.0 209580 91140 ?        Sl   07:15   1:03 /usr/lib/firefox/firefox-bin
root     22536  0.0  0.2   7876  2408 ?        Ss   09:05   0:00 sshd: dbott [priv]
dbott    22550  0.0  0.1   8032  1668 ?        S    09:05   0:00 sshd: dbott@pts/0
dbott    22551  0.0  0.3   5624  3148 pts/0    Ss   09:05   0:00 -bash
dbott    30640  0.0  0.1   2560   996 pts/0    R+   12:13   0:00 ps aux
dbott    30641  0.0  0.0   2880   748 pts/0    R+   12:13   0:00 grep dbott
dbott    31905  0.0  3.6  87904 33384 ?        Sl   May24   0:05 mono /usr/lib/tomboy/Tomboy.exe

```Okay, that's better. Now, what if I only want to see processes run by [COLOR=Red]dbott[/COLOR] that contain the word [COLOR=Red]tomboy[/COLOR]:
```
dbott@feisty:~$ [COLOR=Red]**ps aux | grep dbott | grep tomboy**[/COLOR]
dbott    31905  0.0  3.6  87904 33384 ?        Sl   May24   0:05 mono /usr/lib/tomboy/Tomboy.exe

```Hope this helps.

-Dave

---

### Post by arijarot on 2007-05-26
That does help. Thanks for the quick tutorial, Dave;)

---

### Post by dbott67 on 2007-05-26
No problem.

-Dave

---

