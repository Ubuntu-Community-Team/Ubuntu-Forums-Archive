---
title: "freeradius"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by rugby82 on 2007-05-03
i have another problem!!!
when i launch freeradius server it give me this message!!!
[HTML]Starting - reading configuration files ...
reread_config:  reading radiusd.conf
Config:   including file: /etc/freeradius/proxy.conf
Config:   including file: /etc/freeradius/clients.conf
Config:   including file: /etc/freeradius/snmp.conf
Config:   including file: /etc/freeradius/eap.conf
Config:   including file: /etc/freeradius/sql.conf
 main: prefix = "/usr"
 main: localstatedir = "/var"
 main: logdir = "/var/log/freeradius"
 main: libdir = "/usr/lib/freeradius"
 main: radacctdir = "/var/log/freeradius/radacct"
 main: hostname_lookups = no
 main: max_request_time = 30
 main: cleanup_delay = 5
 main: max_requests = 1024
 main: delete_blocked_requests = 0
 main: port = 1812
 main: allow_core_dumps = no
 main: log_stripped_names = no
 main: log_file = "/var/log/freeradius/radius.log"
 main: log_auth = no
 main: log_auth_badpass = no
 main: log_auth_goodpass = no
 main: pidfile = "/var/run/freeradius/freeradius.pid"
 main: user = "freerad"
 main: group = "freerad"
 main: usercollide = no
 main: lower_user = "no"
 main: lower_pass = "no"
 main: nospace_user = "no"
 main: nospace_pass = "no"
 main: checkrad = "/usr/sbin/checkrad"
 main: proxy_requests = yes
 proxy: retry_delay = 5
 proxy: retry_count = 3
 proxy: synchronous = no
 proxy: default_fallback = yes
 proxy: dead_time = 120
 proxy: post_proxy_authorize = no
 proxy: wake_all_if_all_dead = no
 security: max_attributes = 200
 security: reject_delay = 1
 security: status_server = no
 main: debug_level = 0
read_config_files:  reading dictionary
read_config_files:  reading naslist
Using deprecated naslist file.  Support for this will go away soon.
read_config_files:  reading clients
read_config_files:  reading realms
There appears to be another RADIUS server running on the authentication port 1812
[/HTML]
what mean?

output of ps aux is [HTML]USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   1568   532 ?        S    12:44   0:01 init [2]
root         2  0.0  0.0      0     0 ?        SN   12:44   0:00 [ksoftirqd/0]
root         3  0.0  0.0      0     0 ?        S    12:44   0:00 [watchdog/0]
root         4  0.0  0.0      0     0 ?        S<   12:44   0:00 [events/0]
root         5  0.0  0.0      0     0 ?        S<   12:44   0:00 [khelper]
root         6  0.0  0.0      0     0 ?        S<   12:44   0:00 [kthread]
root         8  0.0  0.0      0     0 ?        S<   12:44   0:00 [kblockd/0]
root         9  0.0  0.0      0     0 ?        S<   12:44   0:00 [kacpid]
root       108  0.0  0.0      0     0 ?        S    12:44   0:00 [pdflush]
root       109  0.0  0.0      0     0 ?        S    12:44   0:00 [pdflush]
root       111  0.0  0.0      0     0 ?        S<   12:44   0:00 [aio/0]
root       110  0.0  0.0      0     0 ?        S    12:44   0:00 [kswapd0]
root       698  0.0  0.0      0     0 ?        S<   12:44   0:00 [kseriod]
root      1809  0.0  0.0      0     0 ?        S<   12:44   0:00 [scsi_eh_0]
root      1826  0.0  0.0      0     0 ?        S<   12:44   0:00 [khubd]
root      1897  0.0  0.0      0     0 ?        S    12:44   0:00 [kjournald]
root      2125  0.0  0.1   2432   920 ?        S<s  12:44   0:00 /sbin/udevd --droot      2951  0.0  0.0      0     0 ?        S    12:44   0:00 [shpchpd_event]root      2975  0.0  0.0      0     0 ?        S<   12:44   0:00 [kgameportd]
dhcp      3475  0.0  0.1   2336   792 ?        S<s  12:44   0:00 dhclient3 -pf /root      3800  0.0  0.2   2152  1192 ?        Ss   12:44   0:00 /usr/sbin/acpidroot      3916  0.0  0.0   1680   496 ?        Ss   12:44   0:00 /bin/dd bs 1 ifklog      3918  0.0  0.2   2396  1316 ?        Ss   12:44   0:00 /sbin/klogd -P
104       3937  0.0  0.1   2192   856 ?        Ss   12:44   0:00 /usr/bin/dbus-d108       3952  0.0  1.0   6760  5352 ?        Ss   12:44   0:01 /usr/sbin/hald
root      3953  0.0  0.1   2716   976 ?        S    12:44   0:00 hald-runner
108       3958  0.0  0.1   2004   792 ?        S    12:44   0:00 /usr/lib/hal/ha108       4008  0.0  0.1   2004   792 ?        S    12:44   0:00 /usr/lib/hal/ha108       4019  0.0  0.1   2008   816 ?        S    12:44   0:00 /usr/lib/hal/ha108       4020  0.0  0.1   2008   816 ?        S    12:44   0:00 /usr/lib/hal/ha108       4022  0.0  0.1   2008   816 ?        S    12:44   0:00 /usr/lib/hal/ha108       4023  0.0  0.1   2008   860 ?        S    12:44   0:00 /usr/lib/hal/haroot      4346  0.0  0.3  10908  1800 ?        Ss   12:44   0:00 /usr/sbin/gdm
root      4365  0.0  0.5  11348  2688 ?        S    12:44   0:00 /usr/sbin/gdm
root      4380  3.1  4.0  27328 20696 tty7     Rs+  12:44   0:52 /usr/bin/X :0 -hplip     4389  0.0  0.1  12872   920 ?        Ssl  12:45   0:00 /usr/sbin/hpiodhplip     4393  0.0  0.9   9412  4680 ?        S    12:45   0:00 python /usr/sbiroot      4472  0.0  0.0   1560   352 ?        Ss   12:45   0:00 /usr/sbin/inetdroot      4543  0.0  0.1   1968   708 ?        Ss   12:45   0:00 hcid: processinroot      4548  0.0  0.0   1612   452 ?        Ss   12:45   0:00 /usr/sbin/sdpd
root      4558  0.0  0.0      0     0 ?        S<   12:45   0:00 [krfcommd]
root      4571  0.0  0.0   1624   296 ?        Ss   12:45   0:00 /sbin/mdadm -F
freerad   4598  0.0  0.2  44316  1512 ?        Ssl  12:45   0:00 /usr/sbin/freerdaemon    4634  0.0  0.0   1800   392 ?        Ss   12:45   0:00 /usr/sbin/atd
root      4647  0.0  0.1   2120   844 ?        Ss   12:45   0:00 /usr/sbin/cron
root      4692  0.0  0.7  11796  3676 ?        Ss   12:45   0:00 /usr/sbin/apachwww-data  4731  0.0  0.4  11796  2268 ?        S    12:45   0:00 /usr/sbin/apachwww-data  4732  0.0  0.4  11796  2268 ?        S    12:45   0:00 /usr/sbin/apachwww-data  4733  0.0  0.4  11796  2268 ?        S    12:45   0:00 /usr/sbin/apachwww-data  4734  0.0  0.4  11796  2268 ?        S    12:45   0:00 /usr/sbin/apachwww-data  4735  0.0  0.4  11796  2268 ?        S    12:45   0:00 /usr/sbin/apachroot      4763  0.0  0.0   1564   496 tty1     Ss+  12:45   0:00 /sbin/getty 384root      4764  0.0  0.0   1560   492 tty2     Ss+  12:45   0:00 /sbin/getty 384root      4765  0.0  0.0   1560   492 tty3     Ss+  12:45   0:00 /sbin/getty 384root      4766  0.0  0.0   1560   492 tty4     Ss+  12:45   0:00 /sbin/getty 384root      4767  0.0  0.0   1564   496 tty5     Ss+  12:45   0:00 /sbin/getty 384root      4768  0.0  0.0   1560   492 tty6     Ss+  12:45   0:00 /sbin/getty 384giulio    4779  0.0  2.1  20788 11244 ?        Ss   12:45   0:00 x-session-managgiulio    4821  0.0  0.1   4336   688 ?        Ss   12:45   0:00 /usr/bin/ssh-aggiulio    4824  0.0  0.1   2708   648 ?        S    12:45   0:00 /usr/bin/dbus-lgiulio    4825  0.0  0.1   2192   940 ?        Ss   12:45   0:00 dbus-daemon --fgiulio    4827  0.0  0.8   6656  4136 ?        S    12:45   0:00 /usr/lib/libgcogiulio    4830  0.0  0.6   6512  3100 ?        Ss   12:45   0:00 /usr/lib/bonobogiulio    4834  0.0  0.1   2336   720 ?        S    12:45   0:00 /usr/bin/gnome-giulio    4836  0.0  1.9  28548 10204 ?        Sl   12:45   0:00 /usr/lib/controgiulio    4840  0.0  0.8   5932  4536 ?        SL   12:45   0:00 /usr/bin/esd -ngiulio    4847  0.0  0.0   2944   480 ?        Ss   12:45   0:00 /usr/bin/esd -ngiulio    4850  0.4  1.9  16388  9932 ?        Ss   12:45   0:06 /usr/bin/metacigiulio    4860  0.2  3.9  41492 20368 ?        Ssl  12:45   0:04 gnome-panel --sgiulio    4862  0.0  3.4  67660 17900 ?        Ssl  12:45   0:01 nautilus --no-dgiulio    4867  0.0  1.1  18464  5692 ?        Ss   12:45   0:00 gnome-volume-magiulio    4873  0.0  2.3  32392 12296 ?        Ss   12:45   0:00 update-notifiergiulio    4877  0.0  1.7  38920  8984 ?        Ss   12:45   0:00 gnome-cups-icongiulio    4882  0.0  0.7   8860  3976 ?        Sl   12:45   0:00 /usr/lib/gnome-giulio    4885  0.0  1.1  18824  5784 ?        Ss   12:45   0:00 gnome-power-mangiulio    4887  0.0  1.8  38944  9312 ?        Sl   12:45   0:00 /usr/lib/gnome-giulio    4901  0.0  0.1   2284   800 ?        S    12:45   0:00 /usr/lib/nautilgiulio    4910  0.0  2.3  32268 11948 ?        S    12:45   0:01 /usr/lib/gnome-giulio    4912  0.0  1.6  18568  8684 ?        S    12:45   0:00 /usr/lib/gnome-giulio    4914  0.0  2.3  33208 12228 ?        S    12:45   0:00 /usr/lib/gnome-giulio    4916  0.0  2.2  24664 11828 ?        S    12:45   0:00 /usr/lib/gnome-giulio    4927  0.0  0.6  16064  3248 ?        Ss   12:45   0:00 gnome-screensavroot      4996  0.0  0.5   6380  3016 ?        Ss   12:48   0:00 /usr/lib/bonoboroot      4998  0.1  1.0  11868  5172 ?        S    12:48   0:02 /usr/lib/at-spicupsys    5213  0.0  0.3   4208  1784 ?        SNs  12:50   0:00 /usr/sbin/cupsdgiulio    5344  0.0  0.3   4172  1672 ?        S    12:51   0:00 /bin/sh /usr/ligiulio    5355  2.0 18.8 202264 97004 ?        Sl   12:51   0:25 /usr/lib/openofgiulio    5403  0.0  1.8  27840  9540 ?        S    12:52   0:00 /usr/lib/notifisyslog    5692  0.0  0.1   1768   708 ?        SNs  12:55   0:00 /sbin/syslogd -giulio    5804  0.6  4.4  34772 22912 ?        Sl   12:59   0:05 wish /usr/bin/agiulio    5819  0.2  0.8  11332  4564 ?        S    13:00   0:01 /usr/lib/at-spigiulio    5861  3.9  9.8 133784 50916 ?        Sl   13:01   0:24 /usr/lib/firefogiulio    5866  0.0  0.0      0     0 ?        Z    13:02   0:00 [net] <defunct>giulio    5958  0.3  3.0  45920 15740 ?        Rl   13:05   0:01 gnome-terminal
giulio    5961  0.0  0.1   2284   680 ?        S    13:05   0:00 gnome-pty-helpegiulio    5962  0.0  0.6   5796  3348 pts/0    Ss   13:05   0:00 bash
giulio    6162  0.0  0.1   2392  1016 pts/0    R+   13:12   0:00 ps aux[/HTML] help me please

---

### Post by wirelessmonkey on 2007-05-03
Well, it looks like you do have another freeradius server running.... try 
sudo kill 4598   OR sudo killall freerdaemon
Then try restarting freeradius.


WM

---

### Post by rugby82 on 2007-05-10
thank you.....bye

---

