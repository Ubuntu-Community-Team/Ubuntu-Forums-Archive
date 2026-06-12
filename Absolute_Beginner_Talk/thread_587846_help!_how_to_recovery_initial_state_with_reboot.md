---
title: "help! how to recovery initial state with reboot"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by say2sky on 2007-10-23
I have notice after long time use of Firefox and mplayer, CPU usage will become very high.  I try to close both and reopen them but CPU usage immediately reach high as before. Now I can only reboot system, then CPU usage will keep low for a period of time(one hour about, depend on situation).

My question is
1. any one have met similar problem?
2. is there any way except reboot system can let system recovery initial status ie. just as reboot. 
3. is this phenomemon related with X-windows System. Because I never have this on a server without X?

Thanks in advance.

---

### Post by hyper_ch on 2007-10-23
I don't use mplayer but I haven't noticed the cpu usage with FF. I noticed that FF slowly uses more and more ram (memory leak?) but once shutdown and restarted everything's back to normal.

---

### Post by say2sky on 2007-10-23
> **hyper_ch said:**
> I don't use mplayer but I haven't noticed the cpu usage with FF. I noticed that FF slowly uses more and more ram (memory leak?) but once shutdown and restarted everything's back to normal.

In the past, I have same memory leak problem with FF. But now the situation seems improved a lot and I now also have more RAM so memory is not a serious problem to me. 

When mplayer and FF work altogether, CPU can reach 100% usage and other application no respond any more. And this cannot be solved by simply close and open FF and mplayer so I ask for help here. :mad:

---

### Post by realvz on 2007-10-23
try Opera and mplayer...

I use firefox myself and have the same issues as yours...

you might also wanna try swiftfox

---

### Post by say2sky on 2007-10-23
> **realvz said:**
> try Opera and mplayer...

I use firefox myself and have the same issues as yours...

you might also wanna try swiftfox

You are right. Opera and mplayer perhaps are good choice. If I cannot find a simple operation to recovery initial state, I will use opera and mplayer as my daily 
combinatory.

---

### Post by say2sky on 2007-10-24
Here is ps result :confused:

```

:~$ ps -eo "pid pcpu comm args" --sort "pcpu"
  PID %CPU COMMAND         COMMAND
    2  0.0 kthreadd        [kthreadd]
    3  0.0 migration/0     [migration/0]
    4  0.0 ksoftirqd/0     [ksoftirqd/0]
    5  0.0 watchdog/0      [watchdog/0]
   27  0.0 kacpid          [kacpid]
   28  0.0 kacpi_notify    [kacpi_notify]
  206  0.0 aio/0           [aio/0]
 2010  0.0 ksuspend_usbd   [ksuspend_usbd]
 2011  0.0 khubd           [khubd]
 2051  0.0 ata_aux         [ata_aux]
 2208  0.0 scsi_eh_0       [scsi_eh_0]
 3570  0.0 pccardd         [pccardd]
 3589  0.0 pccardd         [pccardd]
 3609  0.0 kpsmoused       [kpsmoused]
 4091  0.0 xfssyncd        [xfssyncd]
 4093  0.0 xfssyncd        [xfssyncd]
 6253  0.0 getty           /sbin/getty 38400 tty4
 6254  0.0 getty           /sbin/getty 38400 tty5
 6257  0.0 getty           /sbin/getty 38400 tty2
 6258  0.0 getty           /sbin/getty 38400 tty3
 6259  0.0 getty           /sbin/getty 38400 tty1
 6260  0.0 getty           /sbin/getty 38400 tty6
 6681  0.0 NetworkManagerD /usr/sbin/NetworkManagerDispatcher --pid-file /var/ru
 6694  0.0 system-tools-ba /usr/bin/system-tools-backends
 6695  0.0 dbus-daemon     dbus-daemon --session --print-address --nofork
 6716  0.0 hald-runner     hald-runner
 6773  0.0 hald-addon-cpuf /usr/lib/hal/hald-addon-cpufreq
 6774  0.0 hald-addon-acpi hald-addon-acpi: listening on acpid socket /var/run/a
 6775  0.0 hald-addon-keyb hald-addon-keyboard: listening on /dev/input/event6
 6776  0.0 hald-addon-keyb hald-addon-keyboard: listening on /dev/input/event7
 6777  0.0 hald-addon-keyb hald-addon-keyboard: listening on /dev/input/event8
 6878  0.0 logger          logger -p daemon.err -t mysqld_safe -i -t mysqld
 7085  0.0 avahi-autoipd   avahi-autoipd: [eth0] bound 169.254.6.54
 7086  0.0 avahi-autoipd   avahi-autoipd: [eth0] callout dispatcher
 7107  0.0 saslauthd       /usr/sbin/saslauthd -a pam -c -n 5
 7108  0.0 saslauthd       /usr/sbin/saslauthd -a pam -c -n 5
 7109  0.0 saslauthd       /usr/sbin/saslauthd -a pam -c -n 5
 7110  0.0 saslauthd       /usr/sbin/saslauthd -a pam -c -n 5
 7111  0.0 saslauthd       /usr/sbin/saslauthd -a pam -c -n 5
 7256  0.0 avahi-daemon    avahi-daemon: chroot helper
 7290  0.0 hcid            /usr/sbin/hcid -x -s
 7300  0.0 bluetoothd-serv /usr/lib/bluetooth/bluetoothd-service-audio
 7301  0.0 bluetoothd-serv /usr/lib/bluetooth/bluetoothd-service-input
 7306  0.0 krfcommd        [krfcommd]
 7365  0.0 atd             /usr/sbin/atd
 7598  0.0 apache2         /usr/sbin/apache2 -k start
 7599  0.0 apache2         /usr/sbin/apache2 -k start
 7600  0.0 apache2         /usr/sbin/apache2 -k start
 7601  0.0 apache2         /usr/sbin/apache2 -k start
 7602  0.0 apache2         /usr/sbin/apache2 -k start
 7607  0.0 timidity        /usr/bin/timidity -Os -iAD
 7644  0.0 avahi-autoipd   avahi-autoipd: [eth1] bound 169.254.6.238
 7645  0.0 avahi-autoipd   avahi-autoipd: [eth1] callout dispatcher
 7853  0.0 mapping-daemon  /usr/lib/nautilus-cd-burner/mapping-daemon
 8323  0.0 apache2         /usr/sbin/apache2 -k start
 9934  0.0 apache2         /usr/sbin/apache2 -k start
11630  0.0 ps              ps -eo pid pcpu comm args --sort pcpu
    7  0.0 khelper         [khelper]
 2423  0.0 xfsbufd         [xfsbufd]
 2424  0.0 xfssyncd        [xfssyncd]
 4086  0.0 kjournald       [kjournald]
 4089  0.0 mount.ntfs      /sbin/mount.ntfs /dev/sda3 /media/sda3 -o rw,umask=00
 4090  0.0 xfsbufd         [xfsbufd]
 6462  0.0 acpid           /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid
 6497  0.0 kondemand/0     [kondemand/0]
 6837  0.0 mysqld_safe     /bin/sh /usr/bin/mysqld_safe
 7170  0.0 console-kit-dae /usr/sbin/console-kit-daemon
 7329  0.0 gdm             /usr/sbin/gdm
 7495  0.0 dhclient3       dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0
 7732  0.0 dhclient3       dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth1
  136  0.0 kseriod         [kseriod]
 4092  0.0 xfsbufd         [xfsbufd]
 7382  0.0 cron            /usr/sbin/cron
 7790  0.0 qmgr            qmgr -l -t fifo -u
 2415  0.0 xfsdatad/0      [xfsdatad/0]
 4308  0.0 pppd            /usr/sbin/pppd call dsl-provider
 7552  0.0 cron            /usr/sbin/cron
 7648  0.0 gnome-keyring-d /usr/bin/gnome-keyring-daemon -d
 7804  0.0 bluetooth-apple bluetooth-applet
 7920  0.0 evolution-data- /usr/lib/evolution/evolution-data-server-1.12 --oaf-a
   26  0.0 kblockd/0       [kblockd/0]
 7569  0.0 cron            /usr/sbin/cron
 7700  0.0 ssh-agent       /usr/bin/ssh-agent x-session-manager
10686  0.0 proftpd         proftpd: (accepting connections)
 7270  0.0 dhcdbd          /usr/sbin/dhcdbd --system
 7710  0.0 dbus-daemon     dbus-daemon --fork --print-address 17 --print-pid 19
11275  0.0 gnome-pty-helpe gnome-pty-helper
  154  0.0 pdflush         [pdflush]
 7255  0.0 avahi-daemon    avahi-daemon: registering [oso.local]
 7779  0.0 gnome-vfs-daemo /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 7060  0.0 master          /usr/lib/postfix/master
 7697  0.0 fcitx <defunct> [fcitx] <defunct>
 7802  0.0 vino-session    vino-session --sm-client-id default5
 7914  0.0 evolution-excha /usr/lib/evolution/2.12/evolution-exchange-storage --
    6  0.0 events/0        [events/0]
 6667  0.0 NetworkManager  /usr/sbin/NetworkManager --pid-file /var/run/NetworkM
 2414  0.0 xfslogd/0       [xfslogd/0]
 6756  0.0 hald-addon-keyb hald-addon-keyboard: listening on /dev/input/event1
11315  0.0 pickup          pickup -l -t fifo -u -c
11480  0.0 run-mozilla.sh  /bin/sh /opt/firefox/run-mozilla.sh /opt/firefox/fire
 2639  0.0 udevd           /sbin/udevd --daemon
 7726  0.0 bonobo-activati /usr/lib/bonobo-activation/bonobo-activation-server -
 7844  0.0 python          python /usr/share/system-config-printer/applet.py
  155  0.0 kswapd0         [kswapd0]
 6959  0.0 ddclient        ddclient - sleeping for 49 seconds
 7883  0.0 mixer_applet2   /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-i
  153  0.0 pdflush         [pdflush]
 7846  0.0 gnome-power-man gnome-power-manager
 7432  0.0 apache2         /usr/sbin/apache2 -k start
11469  0.0 firefox         /bin/sh /usr/bin/firefox
 2050  0.0 ata/0           [ata/0]
 7885  0.0 trashapplet     /usr/lib/gnome-applets/trashapplet --oaf-activate-iid
 7651  0.0 x-session-manag x-session-manager
 3590  0.0 ipw2100/0       [ipw2100/0]
 2209  0.0 scsi_eh_1       [scsi_eh_1]
 6630  0.0 klogd           /sbin/klogd -P /var/run/klogd/kmsg
 6651  0.0 dbus-daemon     /usr/bin/dbus-daemon --system
 7756  0.0 gnome-volume-ma gnome-volume-manager --sm-client-id default4
 7702  0.0 gconfd-2        /usr/lib/libgconf2-4/gconfd-2 6
 7889  0.0 deskbar-applet  /usr/bin/python /usr/lib/deskbar-applet/deskbar-apple
    1  0.0 init            /sbin/init
 6572  0.0 syslogd         /sbin/syslogd -u syslog
 6822  0.0 hald-addon-stor hald-addon-storage: polling /dev/scd0 (every 2 sec)
 7703  0.0 fcitx           /usr/bin/fcitx
 6715  0.0 hald            /usr/sbin/hald
 7345  0.0 gdm             /usr/sbin/gdm
 7712  0.0 gnome-settings- /usr/lib/gnome-control-center/gnome-settings-daemon
 6628  0.0 dd              /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 7078  0.0 privoxy         /usr/sbin/privoxy --pidfile /var/run/privoxy.pid --us
 7887  0.1 gnome-netstatus /usr/lib/gnome-netstatus/gnome-netstatus-applet --oaf
11276  0.1 bash            bash
 7718  0.1 metacity        /usr/bin/metacity --sm-client-id=default0
 6877  0.1 mysqld          /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/my
 7842  0.1 stardict        stardict -h
 7723  0.1 nautilus        nautilus --no-default-window --sm-client-id default2
 3952  0.1 kcryptd/0       [kcryptd/0]
 7721  0.2 gnome-panel     gnome-panel --sm-client-id default1
 7881  0.2 multiload-apple /usr/lib/gnome-applets/multiload-applet-2 --oaf-activ
 7808  0.2 gnome-screensav gnome-screensaver
 7121  0.5 tor             /usr/sbin/tor
11592  0.6 bash            bash
11273  1.2 gnome-terminal  gnome-terminal
 7828  1.5 trackerd        trackerd
 7381  8.8 Xorg            /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xaut
11626 34.7 gmplayer        gmplayer /home/say2sky/Desktop/.Movie2/12 Angry Men&#21313;
11485 42.5 firefox-bin     /opt/firefox/firefox-bin

```

---

### Post by hyper_ch on 2007-10-24
install htop and run it from the command line... I use that to see how much ram/cpu/... my processes use... maybe you'll find something there.

---

