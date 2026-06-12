---
title: "MySql problem (please help)"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by ev5unleash1 on 2007-09-14
Hi, I have recently moved my server from Windows to Ubuntu Linux 7.04. I have everything working but when I tried to install phpbb on my server it kept saying that my server did not support this type of connection or something. But I have MySql working and I even tried portmysql. I have also tried reinstalling both and restarting services and I have the user name and pass in correctly. Any ideas why it's not working?

Details

Ubuntu Linux 7.04
Webmin with
Apache (neweset version)
MySql 5
Portsql 7

I'm really about to give up and go back to windows but I really don't wanna have to do that please help

---

### Post by llamakc on 2007-09-14
Cut/paste the error you're receiving.

---

### Post by ev5unleash1 on 2007-09-14
An error has occurred during installation 
The PHP configuration on your server doesn't support the database type that you chose 




That was the error from PHP BB

---

### Post by llamakc on 2007-09-14
Are you installing phpbb from the repositories?

Check the output of "ps -aux" from the terminal and make sure that MySQL is running.

Have you installed php5-mysql yet?

---

### Post by ev5unleash1 on 2007-09-14
Any ideas?

---

### Post by llamakc on 2007-09-14
> **ev5unleash1 said:**
> Any ideas?

Ideas about what? You gotta answer the questions first.

---

### Post by ev5unleash1 on 2007-09-14
I get the output

> ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.2   2908   572 ?        Ss   Sep10   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S    Sep10   0:00 [migration/0]
root         3  0.0  0.0      0     0 ?        SN   Sep10   0:00 [ksoftirqd/0]
root         4  0.0  0.0      0     0 ?        S    Sep10   0:00 [watchdog/0]
root         5  0.0  0.0      0     0 ?        S<   Sep10   0:00 [events/0]
root         6  0.0  0.0      0     0 ?        S<   Sep10   0:00 [khelper]
root         7  0.0  0.0      0     0 ?        S<   Sep10   0:00 [kthread]
root        30  0.0  0.0      0     0 ?        S<   Sep10   0:00 [kblockd/0]
root        31  0.0  0.0      0     0 ?        S<   Sep10   0:00 [kacpid]
root        32  0.0  0.0      0     0 ?        S<   Sep10   0:00 [kacpi_notify]
root       111  0.0  0.0      0     0 ?        S<   Sep10   0:00 [kseriod]
root       132  0.0  0.0      0     0 ?        S    Sep10   0:00 [pdflush]
root       133  0.0  0.0      0     0 ?        S    Sep10   0:00 [pdflush]
root       134  0.0  0.0      0     0 ?        S<   Sep10   0:00 [kswapd0]
root       135  0.0  0.0      0     0 ?        S<   Sep10   0:00 [aio/0]
root       954  0.0  0.1   1712   444 ?        S    Sep12   0:00 /bin/sh /usr/bin/mysqld_safe
mysql      990  0.0  2.3 127112  5728 ?        Sl   Sep12   1:31 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --socket=/var/run/mysqld/mysqld.sock
root       992  0.0  0.1   1636   468 ?        S    Sep12   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
www-data   997  0.0  1.4  17856  3716 ?        S    Sep11   0:00 /usr/sbin/apache2 -k start
www-data   998  0.0  1.5  17856  3744 ?        S    Sep11   0:00 /usr/sbin/apache2 -k start
root      1936  0.0  0.0      0     0 ?        S<   Sep10   0:00 [ksuspend_usbd]
root      1937  0.0  0.0      0     0 ?        S<   Sep10   0:00 [khubd]
root      1959  0.0  0.0      0     0 ?        S<   Sep10   0:00 [ata/0]
root      1960  0.0  0.0      0     0 ?        S<   Sep10   0:00 [ata_aux]
root      2082  0.0  0.0      0     0 ?        S<   Sep10   0:00 [scsi_eh_0]
root      2083  0.0  0.0      0     0 ?        S<   Sep10   0:00 [scsi_eh_1]
postgres  2142  0.0  0.8  19232  2000 ?        S    Sep12   0:00 /usr/lib/postgresql/8.1/bin/postmaster -D /var/lib/postgresql/8.1/main -c config_file=/etc/postgresql/8.1/main/postgresql.conf
postgres  2144  0.0  0.4  19232  1024 ?        S    Sep12   0:02 postgres: writer process                                                                                                      
postgres  2145  0.0  0.2  10012   708 ?        S    Sep12   0:00 postgres: stats buffer process                                                                                                
postgres  2146  0.0  0.2   9168   656 ?        S    Sep12   0:00 postgres: stats collector process                                                                                             
root      2275  0.0  0.0      0     0 ?        D<   Sep10   0:02 [kjournald]
root      2474  0.0  0.1   2868   420 ?        S<s  Sep10   0:00 /sbin/udevd --daemon
root      3362  0.0  0.0      0     0 ?        S<   Sep10   0:00 [kpsmoused]
root      3435  0.0  0.0      0     0 ?        S<   Sep10   0:00 [kgameportd]
nobody    3534  0.0  0.4   2768  1004 ?        Ss   Sep13   0:00 proftpd: (accepting connections)
daemon    3925  0.0  0.1   1764   268 ?        Ss   Sep10   0:00 /sbin/portmap
root      4070  0.0  0.1   1648   432 tty4     Ss+  Sep10   0:00 /sbin/getty 38400 tty4
root      4071  0.0  0.1   1652   432 tty5     Ss+  Sep10   0:00 /sbin/getty 38400 tty5
root      4076  0.0  0.1   1648   432 tty2     Ss+  Sep10   0:00 /sbin/getty 38400 tty2
root      4077  0.0  0.1   1652   432 tty3     Ss+  Sep10   0:00 /sbin/getty 38400 tty3
root      4080  0.0  0.1   1652   432 tty1     Ss+  Sep10   0:00 /sbin/getty 38400 tty1
root      4090  0.0  0.1   1648   432 tty6     Ss+  Sep10   0:00 /sbin/getty 38400 tty6
root      4321  0.0  0.2   2260   640 ?        Ss   Sep10   0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      4427  0.0  0.2   1704   620 ?        Ds   Sep10   0:06 /sbin/syslogd
root      4484  0.0  0.1   1796   420 ?        Ss   Sep10   0:17 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      4486  0.0  0.1   2428   444 ?        Ss   Sep10   0:04 /sbin/klogd -P /var/run/klogd/kmsg
103       4507  0.0  0.3   2848   852 ?        Ss   Sep10   0:00 /usr/bin/dbus-daemon --system
107       4523  0.0  1.0  10448  2620 ?        Ss   Sep10   0:03 /usr/sbin/hald
root      4524  0.0  0.3   2876   884 ?        S    Sep10   0:00 hald-runner
107       4530  0.0  0.3   2100   788 ?        S    Sep10   0:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       4538  0.0  0.3   2100   744 ?        S    Sep10   0:00 hald-addon-keyboard: listening on /dev/input/event1
107       4547  0.0  0.2   2104   740 ?        S    Sep10   0:00 hald-addon-keyboard: listening on /dev/input/event4
107       4550  0.0  0.2   2104   740 ?        S    Sep10   0:00 hald-addon-keyboard: listening on /dev/input/event5
107       4553  0.0  0.2   2100   740 ?        S    Sep10   0:00 hald-addon-keyboard: listening on /dev/input/event6
107       4567  0.0  0.3   2104   836 ?        S    Sep10   0:00 hald-addon-storage: polling /dev/scd0
root      4581  0.0  0.2   1940   712 ?        Ss   Sep10   0:04 /usr/sbin/dhcdbd --system
root      4596  0.0  0.5  12324  1376 ?        Ssl  Sep10   0:00 /usr/sbin/NetworkManager --pid-file /var/run/NetworkManager/NetworkManager.pid
avahi     4613  0.0  0.3   2768   848 ?        Ss   Sep10   0:01 avahi-daemon: registering [eserver.local]
avahi     4614  0.0  0.0   2672   204 ?        Ss   Sep10   0:00 avahi-daemon: chroot helper
root      4631  0.0  0.3   3056   852 ?        Ss   Sep10   0:00 /usr/sbin/NetworkManagerDispatcher --pid-file /var/run/NetworkManager/NetworkManagerDispatcher.pid
root      4644  0.0  0.2   2868   580 ?        Ss   Sep10   0:00 /usr/bin/system-tools-backends
root      4645  0.0  0.3   2720   816 ?        S    Sep10   0:00 dbus-daemon --session --print-address --nofork
root      4691  0.0  0.2  12212   500 ?        Ss   Sep10   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      4694  0.0  0.5  12572  1276 ?        S    Sep10   0:00 /usr/sbin/gdm --config=/etc/gdm/gdm-cdd.conf
root      4697  0.0  4.1  24284 10364 tty7     Ss+  Sep10   3:02 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
bind      4761  0.0  0.8  30720  2024 ?        Ssl  Sep10   0:00 /usr/sbin/named -u bind
root      4928  0.0  0.3   6412   808 ?        Ss   Sep10   0:00 /usr/sbin/hpiod
hplip     4931  0.0  0.5   9988  1372 ?        S    Sep10   0:00 python /usr/sbin/hpssd
root      5021  0.0  0.0      0     0 ?        S    Sep10   0:00 [lockd]
root      5022  0.0  0.0      0     0 ?        S<   Sep10   0:00 [rpciod/0]
root      5023  0.0  0.0      0     0 ?        S<   Sep10   0:00 [nfsd4]
root      5024  0.0  0.0      0     0 ?        S    Sep10   0:00 [nfsd]
root      5025  0.0  0.0      0     0 ?        S    Sep10   0:00 [nfsd]
root      5026  0.0  0.0      0     0 ?        S    Sep10   0:00 [nfsd]
root      5027  0.0  0.0      0     0 ?        S    Sep10   0:00 [nfsd]
root      5028  0.0  0.0      0     0 ?        S    Sep10   0:00 [nfsd]
root      5029  0.0  0.0      0     0 ?        S    Sep10   0:00 [nfsd]
root      5030  0.0  0.0      0     0 ?        S    Sep10   0:00 [nfsd]
root      5031  0.0  0.0      0     0 ?        S    Sep10   0:00 [nfsd]
root      5035  0.0  0.0   2468   144 ?        Ss   Sep10   0:00 /usr/sbin/rpc.mountd
root      5059  0.0  0.1   1828   452 ?        Ss   Sep10   0:00 /usr/sbin/inetd
root      5076  0.0  0.3   6040   848 ?        Ss   Sep10   0:01 /usr/sbin/nmbd -D
root      5078  0.0  0.4   9296  1072 ?        Ss   Sep10   0:00 /usr/sbin/smbd -D
root      5086  0.0  0.0   9296   176 ?        S    Sep10   0:00 /usr/sbin/smbd -D
evan      5094  0.0  1.6  29952  4148 ?        Ssl  Sep10   0:00 x-session-manager
root      5102  0.0  0.1   5084   476 ?        Ss   Sep10   0:00 /usr/sbin/sshd
statd     5158  0.0  0.2   1840   548 ?        Ss   Sep10   0:00 /sbin/rpc.statd
root      5174  0.0  0.1   3648   340 ?        Ss   Sep10   0:00 /usr/sbin/rpc.idmapd
root      5205  0.0  0.2   2700   656 ?        Ss   Sep10   0:00 /usr/sbin/hcid -x -s
root      5229  0.0  0.0      0     0 ?        S<   Sep10   0:00 [krfcommd]
evan      5232  0.0  0.1   4252   268 ?        Ss   Sep10   0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
evan      5242  0.0  0.1   2660   432 ?        S    Sep10   0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
evan      5243  0.0  0.2   2852   620 ?        Ss   Sep10   0:00 /usr/bin/dbus-daemon --fork --print-pid 4 --print-address 8 --session
evan      5259  0.0  0.9   6596  2316 ?        S    Sep10   0:00 /usr/lib/libgconf2-4/gconfd-2 6
evan      5263  0.0  0.2   2756   664 ?        S    Sep10   0:00 /usr/bin/gnome-keyring-daemon
evan      5265  0.0  1.4  29280  3536 ?        Sl   Sep10   0:00 /usr/lib/control-center/gnome-settings-daemon
evan      5294  0.0  0.1   1716   416 ?        Ss   Sep10   0:00 /bin/sh -c /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
evan      5295  0.0  0.3   4960   896 ?        S    Sep10   0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 24
root      5299  0.0  0.9  17856  2376 ?        Ss   Sep10   0:04 /usr/sbin/apache2 -k start
www-data  5321  0.0  1.4  17988  3600 ?        S    Sep10   0:00 /usr/sbin/apache2 -k start
www-data  5322  0.0  1.4  17856  3672 ?        S    Sep10   0:00 /usr/sbin/apache2 -k start
www-data  5323  0.0  1.4  17856  3644 ?        S    Sep10   0:00 /usr/sbin/apache2 -k start
www-data  5324  0.0  1.4  17856  3684 ?        S    Sep10   0:00 /usr/sbin/apache2 -k start
www-data  5325  0.0  1.4  17856  3668 ?        S    Sep10   0:00 /usr/sbin/apache2 -k start
daemon    5378  0.0  0.1   1908   308 ?        Ss   Sep10   0:00 /usr/sbin/atd
evan      5392  0.0  2.5  16936  6408 ?        S    Sep10   0:02 /usr/bin/metacity --sm-client-id=default0
root      5393  0.0  0.3   2280   780 ?        Ss   Sep10   0:00 /usr/sbin/cron
evan      5418  0.0  3.7  40588  9252 ?        S    Sep10   0:04 gnome-panel --sm-client-id default1
evan      5428  0.0  7.0  83324 17412 ?        S    Sep10   0:07 nautilus --no-default-window --sm-client-id default2
evan      5460  0.0  1.0  18864  2508 ?        Ss   Sep10   0:00 gnome-volume-manager --sm-client-id default4
evan      5466  0.0  0.6  39560  1500 ?        Ssl  Sep10   0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=16
evan      5475  0.0  0.8   8476  2048 ?        S    Sep10   0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
evan      5500  0.0  0.7   5096  1800 ?        S    Sep10   0:00 /usr/lib/gnome-user-share/gnome-user-share
evan      5501  0.0  2.9  33188  7196 ?        S    Sep10   0:00 update-notifier
evan      5512  0.0  0.4   9044  1160 ?        Ss   Sep10   0:03 /usr/sbin/apache2 -f /usr/share/gnome-user-share/dav_user.conf -C Listen 1789
evan      5513  0.0  1.5  35036  3836 ?        Sl   Sep10   0:00 /usr/lib/evolution/2.10/evolution-alarm-notify
evan      5514  0.0  0.2   9044   684 ?        S    Sep10   0:00 /usr/sbin/apache2 -f /usr/share/gnome-user-share/dav_user.conf -C Listen 1789
evan      5517  0.0  2.0  28764  4976 ?        S    Sep10   0:24 nm-applet --sm-disable
evan      5518  0.0  1.3  31444  3248 ?        Ss   Sep10   0:08 gnome-power-manager
evan      5520  0.0  1.4  39972  3712 ?        S    Sep10   0:00 gnome-cups-icon --sm-client-id default3
evan      5522  0.0  0.2   2456   740 ?        S    Sep10   0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
evan      5536  0.0  1.8  62344  4536 ?        S    Sep10   0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=21
root      5539  0.0  2.1  10280  5280 ?        Ss   Sep10   0:01 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
evan      5590  0.0  1.2  30368  3164 ?        S    Sep10   0:00 /usr/bin/gnome-brightness-applet --oaf-activate-iid=OAFIID:GNOME_BrightnessApplet_Factory --oaf-ior-fd=22
evan      5599  0.0  2.2  40372  5588 ?        S    Sep10   0:06 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=23
evan      5607  0.0  1.3  16452  3344 ?        Ss   Sep10   0:01 gnome-screensaver
evan      5613  0.0  2.2  28128  5516 ?        S    Sep10   0:00 /usr/lib/notification-daemon/notification-daemon
www-data  5850  0.0  1.4  17856  3700 ?        S    Sep10   0:00 /usr/sbin/apache2 -k start
www-data  5851  0.0  1.4  17856  3656 ?        S    Sep10   0:00 /usr/sbin/apache2 -k start
www-data  5852  0.0  1.4  17856  3700 ?        S    Sep10   0:00 /usr/sbin/apache2 -k start
root      5876  0.0  0.3   2912   752 ?        S    08:58   0:00 hald-addon-hid-ups: listening on /dev/hiddev0
dhcp     16927  0.0  0.2   2452   608 ?        S    Sep11   0:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth0.leases -pf /var/run/dhclient.eth0.pid -q -e dhc_dbus=31 -d eth0
evan     20370  0.0  1.8  27504  4556 ?        S    Sep13   0:02 gksu gproftpd
root     20371  0.5  5.0  34044 12548 ?        Ss   Sep13   9:12 gproftpd
evan     21794  0.0  1.0  12896  2488 ?        S    Sep13   0:01 gksu gproftpd
root     21795  0.5  4.9  34076 12176 ?        Ss   Sep13   8:59 gproftpd
evan     22055  0.0  3.5  37504  8688 ?        S    Sep13   0:03 gedit file:///etc/proftpd/proftpd.conf
cupsys   24672  0.0  0.4   4712  1224 ?        SNs  Sep11   0:00 /usr/sbin/cupsd
root     28313  0.0  2.2  10412  5624 ?        S    22:33   0:00 /usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf
root     28341  0.3  4.0  14100 10000 ?        S    22:33   0:00 /usr/share/webmin/shell/index.cgi
root     28579  0.0  0.1   1716   488 ?        S    22:34   0:00 sh -c su root -c ps\ \-aux 2>&1
root     28580  0.0  0.4   2624  1040 ?        S    22:34   0:00 su root -c ps -aux
root     28581  0.0  0.4   2564  1000 ?        R    22:34   0:00 ps -aux

---

### Post by llamakc on 2007-09-14
My bad on suggesting using the "-" in front of the "aux". Normally it's just "ps aux" or whatever options you want to use. In the future you can type:

ps aux | grep mysql 

to be certain mysql is running.

The good news is that it is running.

So, did you or did you not install phpbb from the repositories (via apt-get or Synaptic)?

---

### Post by ev5unleash1 on 2007-09-14
No the Phpbb is a web app that runs though PHp and my sql for a fourm. It's not something that you install though the OS. It is a web install you just haveto supply the info about your server to install it. It just keeps giving me that message no matter what I do in the mysql config.

This is the output of the code you sent me

root       954  0.0  0.1   1712   444 ?        S    Sep12   0:00 /bin/sh /usr/bin/mysqld_safe
mysql      990  0.0  2.3 127112  5728 ?        Sl   Sep12   1:31 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --socket=/var/run/mysqld/mysqld.sock
root       992  0.0  0.1   1636   468 ?        S    Sep12   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root     30845  0.0  0.1   1716   492 ?        S    22:42   0:00 sh -c su root -c ps\ aux\ \|\ grep\ mysql\  2>&1
root     30846  0.0  0.4   2620  1036 ?        S    22:42   0:00 su root -c ps aux | grep mysql 
root     30847  0.0  0.5   3720  1256 ?        S    22:42   0:00 bash -c ps aux | grep mysql 
root     30849  0.0  0.2   3724   552 ?        R    22:42   0:00 bash -c ps aux | grep mysql

---

### Post by llamakc on 2007-09-14
> **ev5unleash1 said:**
> No the Phpbb is a web app that runs though PHp and my sql for a fourm. It's not something that you install though the OS. It is a web install you just haveto supply the info about your server to install it. It just keeps giving me that message no matter what I do in the mysql config.

This is the output of the code you sent me

root       954  0.0  0.1   1712   444 ?        S    Sep12   0:00 /bin/sh /usr/bin/mysqld_safe
mysql      990  0.0  2.3 127112  5728 ?        Sl   Sep12   1:31 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --skip-external-locking --socket=/var/run/mysqld/mysqld.sock
root       992  0.0  0.1   1636   468 ?        S    Sep12   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
root     30845  0.0  0.1   1716   492 ?        S    22:42   0:00 sh -c su root -c ps\ aux\ \|\ grep\ mysql\  2>&1
root     30846  0.0  0.4   2620  1036 ?        S    22:42   0:00 su root -c ps aux | grep mysql 
root     30847  0.0  0.5   3720  1256 ?        S    22:42   0:00 bash -c ps aux | grep mysql 
root     30849  0.0  0.2   3724   552 ?        R    22:42   0:00 bash -c ps aux | grep mysql

That's not true at all. Search Synaptic (or apt-get) for phpbb. It is already in the repositories. That's precisely why I asked you about how you were installing it. 

And it is not a 'web install'. It's software written in PHP that can use mysql for the database, and it provides a forum environment. I've installed it and admin'd it countless times.

So again, where did you get the phpbb software from, what version did you get, and have you already created the database that it needs?

---

### Post by ev5unleash1 on 2007-09-14
Yes, I have everything set up perfectly including databases, user names, passwords. But when I had the windows server and installed it from there it used to work why not now? and why can't i do it the same way?

---

### Post by llamakc on 2007-09-14
> **ev5unleash1 said:**
> Yes, I have everything set up perfectly including databases, user names, passwords. But when I had the windows server and installed it from there it used to work why not now? and why can't i do it the same way?

Huh? You're asking an entirely different question now. Are you saying you have an EXISTING database that you want to use?

Are you trying to port a phpbb install from Windows to Ubuntu? Were the MySQL versions the same? How did you dump your database? Did you?

Why can't you do it the same way? I hope that was rhetorical. Ubuntu isn't Windows.

---

### Post by ev5unleash1 on 2007-09-14
No i just want to install phpbb from the download i got. I extracted it to the location then opened it though  a browser (apache) and tried to install it and the resportorys did not help me,.

---

### Post by llamakc on 2007-09-14
I've asked you twice where you downloaded phpbb from: whether from the repositories via apt-get/Synaptic or elsewhere. You still have not answered me fully. 

I don't understand your last post at all.

Do this: open a terminal and type: 

sudo apt-get install phpbb2 phpbb2-conf-mysql

---

### Post by ev5unleash1 on 2007-09-14
I've downloaded it form the phpbb site as a tar.gz file and extracted it to the location. Then I tried doing the install from the browser.

---

### Post by ev5unleash1 on 2007-09-14
And When i tried did that it said that the software is already installed.

---

### Post by llamakc on 2007-09-15
So follow the instructions. They're in /usr/share/doc/phpbb2.

---

### Post by ev5unleash1 on 2007-09-15
Ok

---

### Post by ev5unleash1 on 2007-09-15
YOu don't get it I want to install it from the web not on the computer it self. LIke when you downlaod it form the phpbb site and then put it on a location that is accessable from the apache server/ the web and put in the details of your server and install it that way. And where you told me to go it has all read me files.

---

### Post by ev5unleash1 on 2007-09-15
Problem solved, I had to install a plugin for a php to mysql. So both of them worked.

---

