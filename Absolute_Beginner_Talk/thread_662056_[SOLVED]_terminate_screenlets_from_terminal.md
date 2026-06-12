---
title: "[SOLVED] terminate screenlets from terminal?"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by lian1238 on 2008-01-08
How can I use the gnome-terminal to kill screenlets? The screenlets are *.py files so I guess I need to do something to python? I'm trying to make a button to switch from "eye-candy" to "performance" and vice versa, and I need to kill the screenlets. I don't know how to put the commands together yet, though. I'm trying to find that out. Thanks for any info.

---

### Post by p_quarles on 2008-01-08
You can get a list of the process names for the screenlets by running:
```
ps aux | grep *.py
```
To end them:
```
killall *example*.py
```
for each process name.

---

### Post by lian1238 on 2008-01-09
I got this:
```

lian@lian-laptop:~$ ps aux | grep *.py
lian      8846  0.0  0.0   2972   808 pts/0    R+   03:07   0:00 grep *.py

```

I also searched through the processes in the System Monitor but cannot find any *.py processes, while I surely have the screenlets running. Any thoughts?

---

### Post by p_quarles on 2008-01-09
Can you post the entire output of
```
ps aux
```
without the grep filter?

---

### Post by lian1238 on 2008-01-09
Here it is:
```

lian@lian-laptop:~$ ps aux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2952  1856 ?        Ss   02:14   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   02:14   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   02:14   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        SN   02:14   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   02:14   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   02:14   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        SN   02:14   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S<   02:14   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S<   02:14   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S<   02:14   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S<   02:14   0:00 [khelper]
root        31  0.0  0.0      0     0 ?        S<   02:14   0:00 [kblockd/0]
root        32  0.0  0.0      0     0 ?        S<   02:14   0:00 [kblockd/1]
root        33  0.0  0.0      0     0 ?        S<   02:14   0:00 [kacpid]
root        34  0.0  0.0      0     0 ?        S<   02:14   0:00 [kacpi_notify]
root       141  0.0  0.0      0     0 ?        S<   02:14   0:00 [kseriod]
root       169  0.0  0.0      0     0 ?        S    02:14   0:00 [pdflush]
root       170  0.0  0.0      0     0 ?        S    02:14   0:00 [pdflush]
root       171  0.0  0.0      0     0 ?        S<   02:14   0:00 [kswapd0]
root       222  0.0  0.0      0     0 ?        S<   02:14   0:00 [aio/0]
root       223  0.0  0.0      0     0 ?        S<   02:14   0:00 [aio/1]
root      2111  0.0  0.0      0     0 ?        S<   02:14   0:00 [ksuspend_usbd]
root      2112  0.0  0.0      0     0 ?        S<   02:14   0:00 [khubd]
root      2130  0.0  0.0      0     0 ?        S<   02:14   0:00 [ata/0]
root      2131  0.0  0.0      0     0 ?        S<   02:14   0:00 [ata/1]
root      2132  0.0  0.0      0     0 ?        S<   02:14   0:00 [ata_aux]
root      2194  0.0  0.0      0     0 ?        S<   02:14   0:01 [scsi_eh_0]
root      2195  0.0  0.0      0     0 ?        S<   02:14   0:00 [scsi_eh_1]
root      2462  0.0  0.0      0     0 ?        S<   02:14   0:00 [kjournald]
root      2664  0.0  0.1   3052  1400 ?        S<s  02:15   0:00 /sbin/udevd --daemon
root      3571  0.0  0.0      0     0 ?        S<   02:15   0:00 [kpsmoused]
root      3622  0.0  0.0      0     0 ?        S<   02:15   0:00 [tifm]
root      3667  0.0  0.0      0     0 ?        S<   02:15   0:00 [pccardd]
root      3821  0.0  0.0      0     0 ?        S<   02:15   0:00 [ipw3945/0]
root      3825  0.0  0.0      0     0 ?        S<   02:15   0:00 [ipw3945/1]
root      3826  0.0  0.0      0     0 ?        S<   02:15   0:00 [ipw3945/0]
root      3827  0.0  0.0      0     0 ?        S<   02:15   0:00 [ipw3945/1]
root      3887  0.0  0.0   1744   372 ?        S<   02:15   0:00 /sbin/ipw3945d-2.6.22-14-generic --quiet
root      4229  0.0  0.1   4108  1464 ?        Ss   02:15   0:02 /sbin/mount.ntfs /dev/sda6 /media/BackUp -o rw,umask=007,gid=46
root      4232  0.0  0.1   3924  1148 ?        Ss   02:15   0:01 /sbin/mount.ntfs /dev/sda5 /media/Downloads -o rw,umask=007,gid=46
root      4235  0.3  0.1   3924  1156 ?        Ss   02:15   0:15 /sbin/mount.ntfs /dev/sda7 /media/Misc -o rw,umask=007,gid=46
root      4238  0.0  0.0   3788   960 ?        Ss   02:15   0:00 /sbin/mount.ntfs /dev/sda1 /media/WinXP -o rw,umask=007,gid=46
daemon    4378  0.0  0.0   1812   504 ?        Ss   02:15   0:00 /sbin/portmap
statd     4397  0.0  0.0   1880   720 ?        Ss   02:15   0:00 /sbin/rpc.statd
root      4524  0.0  0.0   1692   512 tty4     Ss+  02:15   0:00 /sbin/getty 38400 tty4
root      4525  0.0  0.0   1696   520 tty5     Ss+  02:15   0:00 /sbin/getty 38400 tty5
root      4527  0.0  0.0   1696   520 tty2     Ss+  02:15   0:00 /sbin/getty 38400 tty2
root      4529  0.0  0.0   1696   520 tty3     Ss+  02:15   0:00 /sbin/getty 38400 tty3
root      4531  0.0  0.0   1692   516 tty1     Ss+  02:15   0:00 /sbin/getty 38400 tty1
root      4532  0.0  0.0   1696   520 tty6     Ss+  02:15   0:00 /sbin/getty 38400 tty6
root      4793  0.0  0.1   2432  1320 ?        Ss   02:15   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4822  0.0  0.0      0     0 ?        S<   02:15   0:00 [kondemand/0]
root      4823  0.0  0.0      0     0 ?        S<   02:15   0:00 [kondemand/1]
syslog    4913  0.0  0.0   1916   732 ?        Ss   02:15   0:00 /sbin/syslogd -u syslog
root      4965  0.0  0.0   1840   540 ?        S    02:15   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4967  0.0  0.1   2532  1400 ?        Ss   02:15   0:00 /sbin/klogd -P /var/run/klogd/kmsg
103       4988  0.0  0.1   3032  1184 ?        Ss   02:15   0:00 /usr/bin/dbus-daemon --system
root      5004  0.0  0.2  12560  2100 ?        Ssl  02:15   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
root      5018  0.0  0.1   3280  1276 ?        Ss   02:15   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      5031  0.0  0.0   3084   812 ?        Ss   02:15   0:00 /usr/bin/system-tools-backends
root      5032  0.0  0.1   2776  1260 ?        S    02:15   0:00 dbus-daemon --session --print-address --nofork
107       5051  0.0  0.3   5632  3704 ?        Ss   02:15   0:01 /usr/sbin/hald
root      5052  0.0  0.0   3096  1028 ?        S    02:15   0:00 hald-runner
107       5131  0.0  0.0   2164   900 ?        S    02:15   0:00 hald-addon-keyboard: listening on /dev/input/event1
107       5132  0.0  0.0   2164   896 ?        S    02:15   0:00 hald-addon-keyboard: listening on /dev/input/event4
root      5134  0.0  0.1   3156  1112 ?        S    02:15   0:00 /usr/lib/hal/hald-addon-cpufreq
107       5135  0.0  0.0   2164   884 ?        S    02:15   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       5136  0.0  0.0   2164   896 ?        S    02:15   0:00 hald-addon-keyboard: listening on /dev/input/event5
107       5137  0.0  0.0   2160   892 ?        S    02:15   0:00 hald-addon-keyboard: listening on /dev/input/event6
107       5138  0.0  0.0   2164   896 ?        S    02:15   0:00 hald-addon-keyboard: listening on /dev/input/event7
root      5186  0.0  0.2   5808  2200 ?        Ss   02:15   0:00 /usr/sbin/cupsd
107       5206  0.0  0.1   3260  1184 ?        S    02:15   0:01 hald-addon-storage: polling /dev/scd0 (every 2 sec)
root      5226  0.0  0.0   1752   528 ?        S    02:15   0:00 /bin/sh /usr/bin/mysqld_safe
mysql     5266  0.0  1.5 126916 16140 ?        Sl   02:15   0:00 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --port=3306 --socket=/var/run/mysqld/mysqld.sock
root      5267  0.0  0.0   1680   552 ?        S    02:15   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root      5432  0.0  0.0      0     0 ?        S    02:15   0:00 [lockd]
root      5433  0.0  0.0      0     0 ?        S<   02:15   0:00 [rpciod/0]
root      5434  0.0  0.0      0     0 ?        S<   02:15   0:00 [rpciod/1]
root      5438  0.0  0.0      0     0 ?        S<   02:15   0:00 [nfsd4]
root      5439  0.0  0.0      0     0 ?        S    02:15   0:00 [nfsd]
root      5440  0.0  0.0      0     0 ?        S    02:15   0:00 [nfsd]
root      5441  0.0  0.0      0     0 ?        S    02:15   0:00 [nfsd]
root      5442  0.0  0.0      0     0 ?        S    02:15   0:00 [nfsd]
root      5443  0.0  0.0      0     0 ?        S    02:15   0:00 [nfsd]
root      5444  0.0  0.0      0     0 ?        S    02:15   0:00 [nfsd]
root      5445  0.0  0.0      0     0 ?        S    02:15   0:00 [nfsd]
root      5446  0.0  0.0      0     0 ?        S    02:15   0:00 [nfsd]
root      5450  0.0  0.0   2532   364 ?        Ss   02:15   0:00 /usr/sbin/rpc.mountd
root      5475  0.0  0.1   6424  1352 ?        Ss   02:15   0:00 /usr/sbin/nmbd -D
root      5477  0.0  0.2   9900  2252 ?        Ss   02:15   0:00 /usr/sbin/smbd -D
root      5525  0.0  0.2   7572  2136 ?        Ssl  02:15   0:00 /usr/sbin/console-kit-daemon
avahi     5612  0.0  0.1   2732  1388 ?        Ss   02:15   0:00 avahi-daemon: running [lian-laptop.local]
avahi     5613  0.0  0.0   2732   456 ?        Ss   02:15   0:00 avahi-daemon: chroot helper
root      5614  0.0  0.0   9900   912 ?        S    02:15   0:00 /usr/sbin/smbd -D
root      5628  0.0  0.0   1996   752 ?        Ss   02:15   0:00 /usr/sbin/dhcdbd --system
root      5648  0.0  0.1   2924  1184 ?        Ss   02:15   0:00 /usr/sbin/hcid -x -s
root      5660  0.0  0.0   2772  1012 ?        S    02:15   0:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5661  0.0  0.1   2840  1228 ?        S    02:15   0:00 /usr/lib/bluetooth/bluetoothd-service-audio
root      5670  0.0  0.0      0     0 ?        S<   02:15   0:00 [krfcommd]
root      5702  0.0  0.1  13260  1444 ?        Ss   02:15   0:00 /usr/sbin/gdm
root      5705  0.0  0.2  13684  2872 ?        S    02:15   0:00 /usr/sbin/gdm
root      5708  5.3  7.1  93656 73896 tty7     SLs+ 02:15   3:59 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
ntp       5734  0.0  0.1   4132  1284 ?        Ss   02:15   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 110:120 -g
daemon    5768  0.0  0.0   1964   432 ?        Ss   02:15   0:00 /usr/sbin/atd
root      5782  0.0  0.0   2332   908 ?        Ss   02:15   0:00 /usr/sbin/cron
root      5846  0.0  0.0   1544   172 ?        S    02:15   0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth0
root      5860  0.0  0.0   1792   456 ?        Ss   02:15   0:00 /usr/bin/vmnet-natd -d /var/run/vmnet-natd-8.pid -m /var/run/vmnet-natd-8.mac -c /etc/vmware/vmnet8/nat/nat.conf
root      5889  0.0  0.0   1536   168 ?        S    02:15   0:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet8.pid /dev/vmnet8 vmnet8
root      5891  0.0  0.0   1536   164 ?        S    02:15   0:00 /usr/bin/vmnet-netifup -d /var/run/vmnet-netifup-vmnet1.pid /dev/vmnet1 vmnet1
root      5911  0.0  0.0   1860   356 ?        Ss   02:15   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet1/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet1/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet1.pid vmnet1
root      5912  0.0  0.0   1856   356 ?        Ss   02:15   0:00 /usr/bin/vmnet-dhcpd -cf /etc/vmware/vmnet8/dhcpd/dhcpd.conf -lf /etc/vmware/vmnet8/dhcpd/dhcpd.leases -pf /var/run/vmnet-dhcpd-vmnet8.pid vmnet8
root      5913  0.0  0.6  21568  6236 ?        Ss   02:15   0:00 /usr/sbin/apache2 -k start
lian      5996  0.0  0.7  27972  7480 ?        Ssl  02:15   0:00 x-session-manager
www-data  6000  0.0  0.3  21568  3892 ?        S    02:15   0:00 /usr/sbin/apache2 -k start
www-data  6001  0.0  0.3  21568  3868 ?        S    02:15   0:00 /usr/sbin/apache2 -k start
www-data  6002  0.0  0.3  21568  3868 ?        S    02:15   0:00 /usr/sbin/apache2 -k start
www-data  6003  0.0  0.3  21568  3360 ?        S    02:15   0:00 /usr/sbin/apache2 -k start
www-data  6004  0.0  0.3  21568  3360 ?        S    02:15   0:00 /usr/sbin/apache2 -k start
lian      6039  0.0  0.0   4432   544 ?        Ss   02:15   0:00 /usr/bin/ssh-agent x-session-manager
lian      6041  0.0  0.4   6912  4176 ?        S    02:15   0:01 /usr/lib/libgconf2-4/gconfd-2 6
lian      6044  0.0  0.0   5016   648 ?        S    02:15   0:00 /usr/bin/gnome-keyring-daemon
lian      6046  0.0  0.1   3100  1328 ?        Ss   02:15   0:01 dbus-daemon --fork --print-address 18 --print-pid 20 --session
lian      6048  0.0  1.1  51592 12400 ?        Sl   02:15   0:01 /usr/lib/gnome-control-center/gnome-settings-daemon
lian      6054  0.0  0.0   1752   536 ?        S    02:15   0:00 /bin/sh /usr/bin/compiz --sm-client-id default0
lian      6056  0.1  2.0  46476 21572 ?        S    02:15   0:07 gnome-panel --sm-client-id default1
lian      6058  0.2  1.8  79876 18620 ?        S    02:15   0:10 nautilus --no-default-window --sm-client-id default2
lian      6062  0.0  0.4  19624  5152 ?        Ss   02:15   0:00 gnome-volume-manager --sm-client-id default4
lian      6064  0.0  0.3  40948  3140 ?        Ssl  02:15   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
lian      6139  0.0  0.3   8728  3464 ?        S    02:15   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
lian      6145  0.1  0.8  17176  9280 ?        S    02:15   0:06 /usr/bin/emerald --replace
lian      6146  0.3  2.3  32228 23940 ?        S    02:15   0:15 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --loose-binding --sm-client-id default0 ccp
lian      6147  0.0  0.6  19500  6868 ?        S    02:15   0:00 vino-session --sm-client-id default5
lian      6151  0.0  0.5  13580  5484 ?        S    02:15   0:00 bluetooth-applet
lian      6153  2.7  1.8  28540 18644 ?        S    02:15   2:01 python /usr/local/share/screenlets/Diskusage/DiskusageScreenlet.py > /dev/null
lian      6163  0.0  1.2  34428 12612 ?        S    02:15   0:00 update-notifier
lian      6166  0.0  0.2  16616  2804 ?        Ss   02:15   0:04 gnome-screensaver
lian      6167  0.0  2.3  80716 24064 ?        Sl   02:15   0:01 pidgin
lian      6177  0.0  0.9  68096 10036 ?        Sl   02:15   0:00 /usr/lib/evolution/2.12/evolution-alarm-notify
lian      6178  1.1  1.5  26164 16336 ?        S    02:15   0:53 python /usr/local/share/screenlets/CPU_Meter/CPU_MeterScreenlet.py > /dev/null
lian      6180  0.0  0.7  27324  7640 ?        SNl  02:15   0:02 trackerd
lian      6183  0.0  1.7  40028 18220 ?        S    02:15   0:00 cairo-dock
lian      6185  4.6  2.2  33884 23684 ?        S    02:15   3:27 python /usr/local/share/screenlets/WallpaperClock/WallpaperClockScreenlet.py > /dev/null
lian      6186  0.0  1.0  43072 10764 ?        S    02:15   0:00 nm-applet --sm-disable
lian      6189  0.0  1.1  22972 11760 ?        S    02:15   0:00 python /usr/share/system-config-printer/applet.py
lian      6191  0.0  0.8  39140  8320 ?        Ss   02:15   0:00 gnome-power-manager
lian      6194  0.5  0.1  10228  1976 ?        S    02:15   0:22 conky
lian      6206  0.0  0.0   2660   896 ?        S    02:15   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
lian      6209 11.8  4.8 102492 49964 ?        Sl   02:15   8:44 ktorrent
lian      6221  0.0  0.5  25812  5852 ?        Ss   02:16   0:00 kdeinit Running...        
lian      6238  0.0  0.9  36588  9496 ?        Sl   02:16   0:00 /usr/lib/evolution/2.12/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_CalFactory:1.2 --oaf-ior-fd=21
lian      6242  0.0  0.4  25632  4916 ?        S    02:16   0:00 dcopserver [kdeinit] --n  
lian      6253  0.0  0.7  26468  7240 ?        S    02:16   0:00 klauncher [kdeinit]       
lian      6258  0.0  0.7  67756  7532 ?        Sl   02:16   0:00 /usr/lib/evolution/evolution-data-server-1.12 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_CalFactory:1.2 --oaf-ior-fd=22
lian      6295  0.0  1.0  22560 11088 ?        S    02:16   0:00 /usr/lib/gnome-applets/cpufreq-applet --oaf-activate-iid=OAFIID:GNOME_CPUFreqApplet_Factory --oaf-ior-fd=23
lian      6297  0.0  0.8  20152  8404 ?        S    02:16   0:02 /usr/lib/gnome-applets/multiload-applet-2 --oaf-activate-iid=OAFIID:GNOME_MultiLoadApplet_Factory --oaf-ior-fd=31
lian      6309  0.0  1.0  28632 10612 ?        S    02:16   0:01 kded [kdeinit]            
lian      6438  0.0  1.0  22484 11280 ?        S    02:16   0:00 /usr/lib/gnome-applets/gnome-keyboard-applet --oaf-activate-iid=OAFIID:GNOME_KeyboardApplet_Factory --oaf-ior-fd=29
lian      6713  0.0  1.2  30160 13324 ?        S    02:16   0:00 kio_uiserver [kdeinit]    
lian      7025  0.0  2.0  71372 21320 ?        Sl   03:06   0:01 gnome-terminal
lian      7153  0.0  0.0   2664   736 ?        S    03:06   0:00 gnome-pty-helper
lian      7156  0.0  0.3   5804  3168 pts/0    Ss   03:06   0:00 bash
lian      7331  0.0  1.2  44120 13104 ?        Sl   02:16   0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=30
lian      9149  8.1  4.6 193772 47656 ?        SLl  02:16   5:56 rhythmbox
www-data  9608  0.0  0.3  21568  3360 ?        S    02:16   0:00 /usr/sbin/apache2 -k start
lian     11586  0.0  0.7  52596  7496 ?        S    03:16   0:00 kio_http [kdeinit] http   
lian     11754  0.0  1.1  23804 12372 ?        S    02:17   0:00 python /usr/local/share/screenlets-manager/screenlets-daemon.py
lian     12204  0.2  3.5 114392 36776 ?        Sl   02:17   0:12 python -u /usr/local/share/screenlets/NowPlaying/NowPlayingScreenlet.py
lian     13022  2.7  4.7  65700 49088 ?        S    03:00   0:49 konqueror [kdeinit] --si  
lian     13426  0.0  0.6  26708  6292 ?        S    03:00   0:00 kio_file [kdeinit] file   
lian     19402  0.3  2.1  42840 21728 ?        S    03:18   0:02 /usr/bin/python /usr/bin/ccsm
lian     23573  0.0  1.1  20976 11496 ?        S    02:20   0:00 /usr/lib/notification-daemon/notification-daemon
lian     25702  0.0  0.7  53488  7328 ?        S    03:20   0:00 kio_http [kdeinit] http   
lian     25707  0.0  0.7  53488  7348 ?        S    03:20   0:00 kio_http [kdeinit] http   
lian     25847  0.0  0.7  53488  7328 ?        S    03:20   0:00 kio_http [kdeinit] http   
lian     29888  0.0  0.0   2620  1000 pts/0    R+   03:29   0:00 ps aux
lian@lian-laptop:~$ 

```

---

### Post by p_quarles on 2008-01-09
Hmm. Not sure why the previous command I gave you didn't work -- I see several screenlets running on python in that output. You might have better results with:
```
ps aux | grep python
```
You can easily end all of those screenlets by running:
```
killall python
```

---

### Post by lian1238 on 2008-01-09
```

lian@lian-laptop:~$ ps aux | grep python
lian     19177  0.2  1.1  23792 12360 ?        S    04:26   0:00 python /usr/local/share/screenlets-manager/screenlets-daemon.py
lian     19181  6.1  2.2  33748 23444 ?        S    04:26   0:03 python -u /usr/local/share/screenlets/WallpaperClock/WallpaperClockScreenlet.py
lian     19184  1.7  2.5  80116 26284 ?        Sl   04:26   0:00 python -u /usr/local/share/screenlets/NowPlaying/NowPlayingScreenlet.py
lian     19200  0.9  1.6  27020 16852 ?        S    04:26   0:00 python -u /usr/local/share/screenlets/Pidgin/PidginScreenlet.py
lian     19204  2.0  1.5  26180 16352 ?        S    04:27   0:00 python -u /usr/local/share/screenlets/CPU_Meter/CPU_MeterScreenlet.py
lian     19560  5.0  1.7  28284 18528 ?        S    04:27   0:01 python -u /usr/local/share/screenlets/Diskusage/DiskusageScreenlet.py
lian     21171  0.0  0.0   2976   772 pts/0    S+   04:27   0:00 grep python

```
Python seems to be running only for the screenlets. No harm in killing python, but "killall python" actually kills random screenlets and also not all of them. I had to do it four times to get them all. I tried to repeat that, and got them in two times. How random is that!
```

lian@lian-laptop:~$ killall python
lian@lian-laptop:~$ killall python
lian@lian-laptop:~$ killall python
lian@lian-laptop:~$ killall python
lian@lian-laptop:~$ killall python
python: no process killed
...
...
lian@lian-laptop:~$ killall python
lian@lian-laptop:~$ killall python
lian@lian-laptop:~$ killall python
python: no process killed

```

Is there a way to target each screenlet and kill it?

---

### Post by p_quarles on 2008-01-09
Sure:
```
killall 19177
```
would end the first one listed. You can run the killall command with the PID (the second field in the output of ps aux). If you were to make a script to do this, you would need to use the entire process name:
```
killall python /usr/local/share/screenlets-manager/screenlets-daemon.py
```

---

### Post by mister_pink on 2008-01-09
Try this:

---

### Post by lian1238 on 2008-01-10
**p_quarles**:
I tried to do this:
```

lian@lian-laptop:~/Desktop$ ps aux | grep python
lian      6196  2.5  1.7  28272 18396 ?        S    14:38   0:22 python /usr/local/share/screenlets/Diskusage/DiskusageScreenlet.py > /dev/null
lian      6209  1.0  1.5  26176 16336 ?        S    14:38   0:09 python /usr/local/share/screenlets/CPU_Meter/CPU_MeterScreenlet.py > /dev/null
lian      6217  4.4  1.4  25676 15328 ?        S    14:38   0:39 python /usr/local/share/screenlets/WallpaperClock/WallpaperClockScreenlet.py > /dev/null
lian      6218  0.1  2.7  90428 28420 ?        S    14:38   0:01 python /usr/local/share/screenlets/NowPlaying/NowPlayingScreenlet.py > /dev/null
lian      6220  0.0  1.1  22964 11748 ?        S    14:38   0:00 python /usr/share/system-config-printer/applet.py
lian     22518  0.0  0.0   2976   780 pts/0    S+   14:53   0:00 grep python
lian@lian-laptop:~/Desktop$ killall 6196
6196: no process killed

```

Am I correct to believe that ```
killall python /usr/local/share/screenlets-manager/screenlets-daemon.py
``` would try to kill two processes, python and the screenlets-daemon.py? I tried:
```

lian@lian-laptop:~$ killall python /usr/local/share/screenlets-manager/screenlets-daemon.py
/usr/local/share/screenlets-manager/screenlets-daemon.py: no process killed

```
It killed python, which killed all the screenlets, then it tried to kill the daemon, but "no process killed". I'd rather not killall python because that would kill every other process which uses python, and the interpreter if it is running.

**mister_pink**:
I got this:
```

lian@lian-laptop:~$ chmod +x ~/Desktop/killScreenlets.sh 
lian@lian-laptop:~$ ~/Desktop/killScreenlets.sh 
Killed all 0 .py

```

---

### Post by mister_pink on 2008-01-10
Ill try again! Those "-e"s should've been capital e's. If you just kill things with py in the name it kills panel applets too which I don't suppose you want.

Edit: Changed the script a bit.

---

### Post by lian1238 on 2008-01-10
Thank you, **mister_pink**!
Your script actually killed all the screenlets but echoes "Error".
When there are no screenlets running, it echoes "Killed all 0 .py". Anywho, it works! That's all that matters.

Could you also tell me how to write a script to do the opposite? i.e. to run the screenlets
Muchly appreciated!

---

### Post by mister_pink on 2008-01-10
Hmm, dunno why it does that. You can ignore it anyway, this was just hacked out of another script I was working on, it says error if it thinks theres any left running. If you open it in a text editor and add "sleep 1" on a line after "done" it should be ok. I think it might just take a second to kill them all. To make a script that runs them you should just need something like: 

```
#!/bin/bash

/usr/local/share/screenlets/Diskusage/DiskusageScreenlet.py > /dev/null&
/usr/local/share/screenlets/CPU_Meter/CPU_MeterScreenlet.py > /dev/null&
/usr/local/share/screenlets/WallpaperClock/WallpaperClockScreenlet.py > /dev/null&
/usr/local/share/screenlets/NowPlaying/NowPlayingScreenlet.py > /dev/null&
```

Edit: You could put these all in one script if you wanted, that toggles between the two...

Edit2: Ignore this for a minute, I'll edit if I work out a way that actually works! I tried typing that for one of my screenlets and python just complains a lot!

Edit3: Alright... try this!

---

### Post by lian1238 on 2008-01-10
Wow, it works great!
I still got the "Error" so I changed "sleep 1" to "sleep 2" and now it shows correctly. The NowPlayingScreenet takes a while to close.
But after running the script to run the screenlets, about 5 seconds later, "object not accessible" appears at the terminal prompt. Then it keeps reappearing about every 30 seconds. That's fixed when I created a launcher to the script.
This is a superb script! I added other screenlets as well, like Pidgin and Clock, (easily)!
You were a great help. A big thank you! You :guitar:!

---

