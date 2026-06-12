---
title: "am I infected by virus?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by johnnyw on 2007-06-27
when I plug my ubuntu pc to the ethernet it starts blinking ( the NIC led). I have nothing transfering data and when I open the system monitor I see 20 kb/s data rate being received. my inet connection can`t be used either ( i cant open any web site)


any ideas?

---

### Post by Tomosaur on 2007-06-27
Difficult to say from so little info. It's unlikely, and depending on what deamons and such you have running, it could just be ordinary idle traffic (your computer will check the network periodically for a variety of reasons which it's not worth going into here).

In any case, it always pays to be sure. First of all, close all of the applications which obviously use a network connection (browsers, bittorrent, messengers etc etc). Next, open up a terminal and give us the output of the following commands:

```

ps -e

```
The above command gives us all of your running processes.

```

netstat

```
This command gives us network information.

Use the CODE tags when pasting the output here.

---

### Post by johnnyw on 2007-06-27
```
johnnyw@johnnyw-desktop:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  157 ?        00:00:00 pdflush
  158 ?        00:00:00 pdflush
  160 ?        00:00:00 aio/0
  159 ?        00:00:00 kswapd0
  747 ?        00:00:00 kseriod
 1761 ?        00:00:00 ata/0
 1762 ?        00:00:00 ata_hotplug/0
 1765 ?        00:00:00 scsi_eh_0
 1766 ?        00:00:00 scsi_eh_1
 1767 ?        00:00:00 scsi_eh_2
 1768 ?        00:00:00 scsi_eh_3
 1896 ?        00:00:00 khubd
 1980 ?        00:00:00 kjournald
 2213 ?        00:00:00 udevd
 3041 ?        00:00:00 shpchpd_event
 3097 ?        00:00:00 kgameportd
 3641 ?        00:00:00 dhclient3
 3675 ?        00:00:00 portmap
 3938 ?        00:00:00 acpid
 4028 ?        00:00:00 syslogd
 4054 ?        00:00:00 dd
 4056 ?        00:00:00 klogd
 4075 ?        00:00:00 dbus-daemon
 4091 ?        00:00:01 hald
 4092 ?        00:00:00 hald-runner
 4097 ?        00:00:00 hald-addon-acpi
 4147 ?        00:00:00 hald-addon-keyb
 4158 ?        00:00:00 hald-addon-stor
 4159 ?        00:00:00 hald-addon-stor
 4161 ?        00:00:00 hald-addon-stor
 4162 ?        00:00:00 hald-addon-stor
 4490 ?        00:00:00 gdm
 4519 ?        00:00:00 gdm
 4524 tty7     00:05:40 Xorg
 4542 ?        00:00:00 hpiod
 4548 ?        00:00:00 python
 4606 ?        00:00:00 boinc_client
 4629 ?        00:00:00 inetd
 4677 ?        00:00:00 nmbd
 4681 ?        00:00:00 smbd
 4731 ?        00:00:00 rpc.statd
 4732 ?        00:00:00 smbd
 4748 ?        00:00:00 hcid
 4752 ?        00:00:00 sdpd
 4767 ?        00:00:00 krfcommd
 4780 ?        00:00:00 mdadm
 4814 ?        00:00:00 atd
 4827 ?        00:00:00 cron
 4905 tty1     00:00:00 getty
 4906 tty2     00:00:00 getty
 4907 tty3     00:00:00 getty
 4908 tty4     00:00:00 getty
 4909 tty5     00:00:00 getty
 4910 tty6     00:00:00 getty
 4931 ?        00:00:00 x-session-manag
 4973 ?        00:00:00 ssh-agent
 4976 ?        00:00:00 dbus-launch
 4977 ?        00:00:00 dbus-daemon
 4979 ?        00:00:00 gconfd-2
 4982 ?        00:00:00 gnome-keyring-d
 4984 ?        00:00:00 bonobo-activati
 4986 ?        00:00:00 gnome-settings-
 4988 ?        00:00:00 esd
 4995 ?        00:00:03 metacity
 5001 ?        00:00:02 gnome-panel
 5003 ?        00:00:03 nautilus
 5006 ?        00:00:00 gnome-volume-ma
 5014 ?        00:00:00 update-notifier
 5023 ?        00:00:00 gnome-vfs-daemo
 5028 ?        00:00:00 trashapplet
 5036 ?        00:00:00 gnome-power-man
 5040 ?        00:00:00 mapping-daemon
 5051 ?        00:00:00 mixer_applet2
 5053 ?        00:00:00 clock-applet
 5081 ?        00:00:00 gnome-screensav
 5095 ?        00:00:00 gksu
 5096 ?        00:00:01 network-admin <defunct>
 5100 ?        00:00:00 esd
 5270 ?        00:00:01 gnome-terminal
 5271 ?        00:00:00 gnome-pty-helpe
 5307 pts/2    00:00:00 bash
 5438 ?        00:05:27 wcg_hpf2_rosett
 5439 ?        00:00:00 wcg_hpf2_rosett
 5440 ?        00:00:00 wcg_hpf2_rosett
 5442 ?        00:00:03 firefox-bin
 5461 ?        00:00:47 gnome-system-mo
 5535 ?        00:00:00 scsi_eh_5
 5536 ?        00:00:00 usb-storage
 5570 ?        00:00:00 hald-addon-stor
 5571 ?        00:00:00 hald-addon-stor
 5609 pts/0    00:00:00 bash
 5626 pts/0    00:00:00 ps
johnnyw@johnnyw-desktop:~$ ps -e
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  157 ?        00:00:00 pdflush
  158 ?        00:00:00 pdflush
  160 ?        00:00:00 aio/0
  159 ?        00:00:00 kswapd0
  747 ?        00:00:00 kseriod
 1761 ?        00:00:00 ata/0
 1762 ?        00:00:00 ata_hotplug/0
 1765 ?        00:00:00 scsi_eh_0
 1766 ?        00:00:00 scsi_eh_1
 1767 ?        00:00:00 scsi_eh_2
 1768 ?        00:00:00 scsi_eh_3
 1896 ?        00:00:00 khubd
 1980 ?        00:00:00 kjournald
 2213 ?        00:00:00 udevd
 3041 ?        00:00:00 shpchpd_event
 3097 ?        00:00:00 kgameportd
 3641 ?        00:00:00 dhclient3
 3675 ?        00:00:00 portmap
 3938 ?        00:00:00 acpid
 4028 ?        00:00:00 syslogd
 4054 ?        00:00:00 dd
 4056 ?        00:00:00 klogd
 4075 ?        00:00:00 dbus-daemon
 4091 ?        00:00:01 hald
 4092 ?        00:00:00 hald-runner
 4097 ?        00:00:00 hald-addon-acpi
 4147 ?        00:00:00 hald-addon-keyb
 4158 ?        00:00:00 hald-addon-stor
 4159 ?        00:00:00 hald-addon-stor
 4161 ?        00:00:00 hald-addon-stor
 4162 ?        00:00:00 hald-addon-stor
 4490 ?        00:00:00 gdm
 4519 ?        00:00:00 gdm
 4524 tty7     00:05:42 Xorg
 4542 ?        00:00:00 hpiod
 4548 ?        00:00:00 python
 4606 ?        00:00:00 boinc_client
 4629 ?        00:00:00 inetd
 4677 ?        00:00:00 nmbd
 4681 ?        00:00:00 smbd
 4731 ?        00:00:00 rpc.statd
 4732 ?        00:00:00 smbd
 4748 ?        00:00:00 hcid
 4752 ?        00:00:00 sdpd
 4767 ?        00:00:00 krfcommd
 4780 ?        00:00:00 mdadm
 4814 ?        00:00:00 atd
 4827 ?        00:00:00 cron
 4905 tty1     00:00:00 getty
 4906 tty2     00:00:00 getty
 4907 tty3     00:00:00 getty
 4908 tty4     00:00:00 getty
 4909 tty5     00:00:00 getty
 4910 tty6     00:00:00 getty
 4931 ?        00:00:00 x-session-manag
 4973 ?        00:00:00 ssh-agent
 4976 ?        00:00:00 dbus-launch
 4977 ?        00:00:00 dbus-daemon
 4979 ?        00:00:00 gconfd-2
 4982 ?        00:00:00 gnome-keyring-d
 4984 ?        00:00:00 bonobo-activati
 4986 ?        00:00:00 gnome-settings-
 4988 ?        00:00:00 esd
 4995 ?        00:00:03 metacity
 5001 ?        00:00:02 gnome-panel
 5003 ?        00:00:03 nautilus
 5006 ?        00:00:00 gnome-volume-ma
 5014 ?        00:00:00 update-notifier
 5023 ?        00:00:00 gnome-vfs-daemo
 5028 ?        00:00:00 trashapplet
 5036 ?        00:00:00 gnome-power-man
 5040 ?        00:00:00 mapping-daemon
 5051 ?        00:00:00 mixer_applet2
 5053 ?        00:00:00 clock-applet
 5081 ?        00:00:00 gnome-screensav
 5095 ?        00:00:00 gksu
 5096 ?        00:00:01 network-admin <defunct>
 5100 ?        00:00:00 esd
 5270 ?        00:00:02 gnome-terminal
 5271 ?        00:00:00 gnome-pty-helpe
 5307 pts/2    00:00:00 bash
 5438 ?        00:05:27 wcg_hpf2_rosett
 5439 ?        00:00:00 wcg_hpf2_rosett
 5440 ?        00:00:00 wcg_hpf2_rosett
 5461 ?        00:00:47 gnome-system-mo
 5535 ?        00:00:00 scsi_eh_5
 5536 ?        00:00:00 usb-storage
 5570 ?        00:00:00 hald-addon-stor
 5571 ?        00:00:00 hald-addon-stor
 5609 pts/0    00:00:00 bash
 5627 pts/0    00:00:00 ps

```


I owe you the ps e code

---

### Post by p_quarles on 2007-06-27
As far as I know, there are not yet any viruses that can infect Linux systems. It's just a matter of time, sure, but it will definitely be big news when it happens.

If you want to see where your automated network traffic is going, you can install the "Etherape" app from the repositories. It gives you a graphical overview of all the connections your system is making. Most of it is just checking e-mail, software updates, and RSS feeds.

---

### Post by johnnyw on 2007-06-27
```
johnnyw@johnnyw-desktop:~$ netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost:42054         localhost:39888         ESTABLISHED
tcp        0      0 localhost:39888         localhost:42054         ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  9      [ ]         DGRAM                    10009    /dev/log
unix  2      [ ]         DGRAM                    5223     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    10110    @/org/freedesktop/hal/udev_event
unix  3      [ ]         STREAM     CONNECTED     51253    /tmp/orbit-johnnyw/linc-15ff-0-7f125ba076795
unix  3      [ ]         STREAM     CONNECTED     51252
unix  3      [ ]         STREAM     CONNECTED     51251    /tmp/orbit-johnnyw/linc-139f-0-48295d9366a80
unix  3      [ ]         STREAM     CONNECTED     51250
unix  3      [ ]         STREAM     CONNECTED     51249    /tmp/orbit-johnnyw/linc-15ff-0-7f125ba076795
unix  3      [ ]         STREAM     CONNECTED     51248
unix  3      [ ]         STREAM     CONNECTED     51247    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     51246
unix  3      [ ]         STREAM     CONNECTED     51217    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     51216
unix  3      [ ]         STREAM     CONNECTED     51206    /tmp/orbit-johnnyw/linc-15ff-0-7f125ba076795
unix  3      [ ]         STREAM     CONNECTED     51205
unix  3      [ ]         STREAM     CONNECTED     51202    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     51201
unix  3      [ ]         STREAM     CONNECTED     51198    /tmp/.ICE-unix/4931
unix  3      [ ]         STREAM     CONNECTED     51197
unix  3      [ ]         STREAM     CONNECTED     51193    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     51192
unix  3      [ ]         STREAM     CONNECTED     50517    @/tmp/hald-local/dbus-rXqbCYxlGY
unix  3      [ ]         STREAM     CONNECTED     50516
unix  3      [ ]         STREAM     CONNECTED     50508    @/tmp/hald-local/dbus-rXqbCYxlGY
unix  3      [ ]         STREAM     CONNECTED     50502
unix  3      [ ]         STREAM     CONNECTED     16248    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     16247
unix  3      [ ]         STREAM     CONNECTED     16245    /tmp/orbit-johnnyw/linc-1555-0-1fe44b0f4030f
unix  3      [ ]         STREAM     CONNECTED     16244
unix  3      [ ]         STREAM     CONNECTED     16243    /tmp/orbit-johnnyw/linc-139f-0-48295d9366a80
unix  3      [ ]         STREAM     CONNECTED     16242
unix  3      [ ]         STREAM     CONNECTED     16241    /tmp/orbit-johnnyw/linc-1555-0-1fe44b0f4030f
unix  3      [ ]         STREAM     CONNECTED     16240
unix  3      [ ]         STREAM     CONNECTED     16239    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     16238
unix  2      [ ]         STREAM                   16212
unix  3      [ ]         STREAM     CONNECTED     16211    /tmp/orbit-johnnyw/linc-1555-0-1fe44b0f4030f
unix  3      [ ]         STREAM     CONNECTED     16210
unix  3      [ ]         STREAM     CONNECTED     16207    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     16206
unix  3      [ ]         STREAM     CONNECTED     16203    /tmp/.ICE-unix/4931
unix  3      [ ]         STREAM     CONNECTED     16202
unix  3      [ ]         STREAM     CONNECTED     16198    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16197
unix  3      [ ]         STREAM     CONNECTED     13997
unix  3      [ ]         STREAM     CONNECTED     13996
unix  3      [ ]         STREAM     CONNECTED     13994    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     13993
unix  3      [ ]         STREAM     CONNECTED     13991    /tmp/orbit-johnnyw/linc-1496-0-60aaab0a62ea9
unix  3      [ ]         STREAM     CONNECTED     13990
unix  3      [ ]         STREAM     CONNECTED     13989    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     13988
unix  3      [ ]         STREAM     CONNECTED     13987    /tmp/orbit-johnnyw/linc-1496-0-60aaab0a62ea9
unix  3      [ ]         STREAM     CONNECTED     13986
unix  3      [ ]         STREAM     CONNECTED     13983    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     13982
unix  3      [ ]         STREAM     CONNECTED     13979    /tmp/.ICE-unix/4931
unix  3      [ ]         STREAM     CONNECTED     13978
unix  3      [ ]         STREAM     CONNECTED     13974    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13973
unix  2      [ ]         STREAM                   13178
unix  3      [ ]         STREAM     CONNECTED     13104    /tmp/orbit-johnnyw/linc-13e7-0-1a7531a8debee
unix  3      [ ]         STREAM     CONNECTED     13103
unix  3      [ ]         STREAM     CONNECTED     13100    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     13099
unix  375    [ ]         STREAM     CONNECTED     13095    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13094
unix  3      [ ]         STREAM     CONNECTED     12798    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12797
unix  3      [ ]         STREAM     CONNECTED     12796    @/tmp/dbus-cVVsktxEtkunix  3      [ ]         STREAM     CONNECTED     12795
unix  3      [ ]         STREAM     CONNECTED     12794    /tmp/orbit-johnnyw/linc-13d6-0-feb374f5bca8
unix  3      [ ]         STREAM     CONNECTED     12793
unix  3      [ ]         STREAM     CONNECTED     12790    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12789
unix  3      [ ]         STREAM     CONNECTED     12785    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12784
unix  3      [ ]         STREAM     CONNECTED     12729    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12728
unix  3      [ ]         STREAM     CONNECTED     12727    /tmp/orbit-johnnyw/linc-1389-0-25b904cf2724b
unix  3      [ ]         STREAM     CONNECTED     12726
unix  3      [ ]         STREAM     CONNECTED     12725    /tmp/orbit-johnnyw/linc-13bb-0-2bed24e82723e
unix  3      [ ]         STREAM     CONNECTED     12724
unix  3      [ ]         STREAM     CONNECTED     12718    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12717
unix  3      [ ]         STREAM     CONNECTED     12716    /tmp/orbit-johnnyw/linc-1389-0-25b904cf2724b
unix  3      [ ]         STREAM     CONNECTED     12715
unix  3      [ ]         STREAM     CONNECTED     12714    /tmp/orbit-johnnyw/linc-13bd-0-2bed24e862395
unix  3      [ ]         STREAM     CONNECTED     12712
unix  3      [ ]         STREAM     CONNECTED     12704    /tmp/orbit-johnnyw/linc-13bd-0-2bed24e862395
unix  3      [ ]         STREAM     CONNECTED     12703
unix  3      [ ]         STREAM     CONNECTED     12702    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     12701
unix  3      [ ]         STREAM     CONNECTED     12700    /tmp/orbit-johnnyw/linc-13bd-0-2bed24e862395
unix  3      [ ]         STREAM     CONNECTED     12699
unix  3      [ ]         STREAM     CONNECTED     12696    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12695
unix  3      [ ]         STREAM     CONNECTED     12691    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12690
unix  3      [ ]         STREAM     CONNECTED     12687    /tmp/orbit-johnnyw/linc-13bb-0-2bed24e82723e
unix  3      [ ]         STREAM     CONNECTED     12686
unix  3      [ ]         STREAM     CONNECTED     12685    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     12684
unix  3      [ ]         STREAM     CONNECTED     12683    /tmp/orbit-johnnyw/linc-13bb-0-2bed24e82723e
unix  3      [ ]         STREAM     CONNECTED     12682
unix  3      [ ]         STREAM     CONNECTED     12679    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12678
unix  3      [ ]         STREAM     CONNECTED     12674    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12673
unix  3      [ ]         STREAM     CONNECTED     12659    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12658
unix  3      [ ]         STREAM     CONNECTED     12650    /tmp/mapping-johnnyw
unix  3      [ ]         STREAM     CONNECTED     12642
unix  3      [ ]         STREAM     CONNECTED     12638    /tmp/orbit-johnnyw/linc-1389-0-25b904cf2724b
unix  3      [ ]         STREAM     CONNECTED     12637
unix  3      [ ]         STREAM     CONNECTED     12636    /tmp/orbit-johnnyw/linc-139f-0-48295d9366a80
unix  3      [ ]         STREAM     CONNECTED     12635
unix  3      [ ]         STREAM     CONNECTED     12628    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12627
unix  3      [ ]         STREAM     CONNECTED     12626    /tmp/orbit-johnnyw/linc-1389-0-25b904cf2724b
unix  3      [ ]         STREAM     CONNECTED     12625
unix  3      [ ]         STREAM     CONNECTED     12624    /tmp/orbit-johnnyw/linc-13a4-0-5638c0bc98cdb
unix  3      [ ]         STREAM     CONNECTED     12623
unix  3      [ ]         STREAM     CONNECTED     12617    /tmp/orbit-johnnyw/linc-138b-0-25b904cfb843b
unix  3      [ ]         STREAM     CONNECTED     12616
unix  3      [ ]         STREAM     CONNECTED     12615    /tmp/orbit-johnnyw/linc-139f-0-48295d9366a80
unix  3      [ ]         STREAM     CONNECTED     12614
unix  3      [ ]         STREAM     CONNECTED     12612    /tmp/orbit-johnnyw/linc-13a4-0-5638c0bc98cdb
unix  3      [ ]         STREAM     CONNECTED     12611
unix  3      [ ]         STREAM     CONNECTED     12610    /tmp/orbit-johnnyw/linc-139f-0-48295d9366a80
unix  3      [ ]         STREAM     CONNECTED     12609
unix  3      [ ]         STREAM     CONNECTED     12604    /tmp/orbit-johnnyw/linc-13a4-0-5638c0bc98cdb
unix  3      [ ]         STREAM     CONNECTED     12603
unix  3      [ ]         STREAM     CONNECTED     12602    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     12601
unix  3      [ ]         STREAM     CONNECTED     12600    /tmp/orbit-johnnyw/linc-13a4-0-5638c0bc98cdb
unix  3      [ ]         STREAM     CONNECTED     12599
unix  3      [ ]         STREAM     CONNECTED     12596    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12595
unix  3      [ ]         STREAM     CONNECTED     12591    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12590
unix  3      [ ]         STREAM     CONNECTED     12587    /tmp/orbit-johnnyw/linc-139f-0-48295d9366a80
unix  3      [ ]         STREAM     CONNECTED     12586
unix  3      [ ]         STREAM     CONNECTED     12585    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     12584
unix  3      [ ]         STREAM     CONNECTED     12562    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12561
unix  3      [ ]         STREAM     CONNECTED     12560    /tmp/orbit-johnnyw/linc-139f-0-48295d9366a80
unix  3      [ ]         STREAM     CONNECTED     12559
unix  3      [ ]         STREAM     CONNECTED     12556    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12555
unix  3      [ ]         STREAM     CONNECTED     12533    @/tmp/dbus-cVVsktxEtkunix  3      [ ]         STREAM     CONNECTED     12532
unix  3      [ ]         STREAM     CONNECTED     12531    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12530
unix  2      [ ]         DGRAM                    12529
unix  3      [ ]         STREAM     CONNECTED     12528    /tmp/orbit-johnnyw/linc-1398-0-5638c0bc314b8
unix  3      [ ]         STREAM     CONNECTED     12527
unix  3      [ ]         STREAM     CONNECTED     12524    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12523
unix  3      [ ]         STREAM     CONNECTED     12520    /tmp/.ICE-unix/4931
unix  3      [ ]         STREAM     CONNECTED     12519
unix  3      [ ]         STREAM     CONNECTED     12515    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12514
unix  3      [ ]         STREAM     CONNECTED     12508    /tmp/orbit-johnnyw/linc-138b-0-25b904cfb843b
unix  3      [ ]         STREAM     CONNECTED     12507
unix  3      [ ]         STREAM     CONNECTED     12506    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     12505
unix  3      [ ]         STREAM     CONNECTED     12500    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12499
unix  3      [ ]         STREAM     CONNECTED     12496    @/tmp/dbus-cVVsktxEtkunix  3      [ ]         STREAM     CONNECTED     12495
unix  3      [ ]         STREAM     CONNECTED     12494    /tmp/orbit-johnnyw/linc-1396-0-5638c0bc8e08
unix  3      [ ]         STREAM     CONNECTED     12493
unix  3      [ ]         STREAM     CONNECTED     12490    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12489
unix  3      [ ]         STREAM     CONNECTED     12484    /tmp/.ICE-unix/4931
unix  3      [ ]         STREAM     CONNECTED     12483
unix  3      [ ]         STREAM     CONNECTED     12479    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12478
unix  3      [ ]         STREAM     CONNECTED     12469    /tmp/orbit-johnnyw/linc-138b-0-25b904cfb843b
unix  3      [ ]         STREAM     CONNECTED     12468
unix  3      [ ]         STREAM     CONNECTED     12465    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12464
unix  3      [ ]         STREAM     CONNECTED     12459    /tmp/.ICE-unix/4931
unix  3      [ ]         STREAM     CONNECTED     12458
unix  3      [ ]         STREAM     CONNECTED     12462    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12457
unix  3      [ ]         STREAM     CONNECTED     12452    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12451
unix  3      [ ]         STREAM     CONNECTED     12442    /tmp/orbit-johnnyw/linc-137a-0-414a3e558e436
unix  3      [ ]         STREAM     CONNECTED     12441
unix  3      [ ]         STREAM     CONNECTED     12440    /tmp/orbit-johnnyw/linc-137a-0-414a3e558e436
unix  3      [ ]         STREAM     CONNECTED     12439
unix  3      [ ]         STREAM     CONNECTED     12438    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     12437
unix  3      [ ]         STREAM     CONNECTED     12430    @/tmp/dbus-cVVsktxEtkunix  3      [ ]         STREAM     CONNECTED     12429
unix  3      [ ]         STREAM     CONNECTED     12427    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12426
unix  3      [ ]         STREAM     CONNECTED     12425    /tmp/orbit-johnnyw/linc-138d-0-25b904cf35588
unix  3      [ ]         STREAM     CONNECTED     12424
unix  3      [ ]         STREAM     CONNECTED     12421    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12420
unix  3      [ ]         STREAM     CONNECTED     12417    /tmp/.ICE-unix/4931
unix  3      [ ]         STREAM     CONNECTED     12416
unix  3      [ ]         STREAM     CONNECTED     12412    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12411
unix  3      [ ]         STREAM     CONNECTED     12410    /tmp/orbit-johnnyw/linc-1389-0-25b904cf2724b
unix  3      [ ]         STREAM     CONNECTED     12409
unix  3      [ ]         STREAM     CONNECTED     12408    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     12407
unix  3      [ ]         STREAM     CONNECTED     12404    /tmp/orbit-johnnyw/linc-1389-0-25b904cf2724b
unix  3      [ ]         STREAM     CONNECTED     12403
unix  3      [ ]         STREAM     CONNECTED     12400    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12399
unix  3      [ ]         STREAM     CONNECTED     12396    /tmp/.ICE-unix/4931
unix  3      [ ]         STREAM     CONNECTED     12395
unix  3      [ ]         STREAM     CONNECTED     12391    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12390
unix  3      [ ]         STREAM     CONNECTED     12377    /tmp/.ICE-unix/4931
unix  3      [ ]         STREAM     CONNECTED     12376
unix  3      [ ]         STREAM     CONNECTED     12380    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12375
unix  3      [ ]         STREAM     CONNECTED     12374    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12373
unix  3      [ ]         STREAM     CONNECTED     12372    /tmp/orbit-johnnyw/linc-1383-0-1c86b1642f77
unix  3      [ ]         STREAM     CONNECTED     12371
unix  3      [ ]         STREAM     CONNECTED     12368    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12367
unix  3      [ ]         STREAM     CONNECTED     12347    /tmp/orbit-johnnyw/linc-137a-0-414a3e558e436
unix  3      [ ]         STREAM     CONNECTED     12346
unix  3      [ ]         STREAM     CONNECTED     12343    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12342
unix  3      [ ]         STREAM     CONNECTED     12338    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12337
unix  3      [ ]         STREAM     CONNECTED     12333    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12332
unix  2      [ ]         STREAM                   12323
unix  3      [ ]         STREAM     CONNECTED     12313    /tmp/orbit-johnnyw/linc-1343-0-49a82ef125b36
unix  3      [ ]         STREAM     CONNECTED     12312
unix  3      [ ]         STREAM     CONNECTED     12311    /tmp/orbit-johnnyw/linc-1378-0-7fcd465b35583
unix  3      [ ]         STREAM     CONNECTED     12310
unix  3      [ ]         STREAM     CONNECTED     12272    /tmp/orbit-johnnyw/linc-1343-0-49a82ef125b36
unix  3      [ ]         STREAM     CONNECTED     12271
unix  3      [ ]         STREAM     CONNECTED     12270    /tmp/orbit-johnnyw/linc-1373-0-1c32585d11471
unix  3      [ ]         STREAM     CONNECTED     12158
unix  2      [ ]         DGRAM                    12144
unix  3      [ ]         STREAM     CONNECTED     12138    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12137
unix  3      [ ]         STREAM     CONNECTED     12134    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12133
unix  3      [ ]         STREAM     CONNECTED     12132
unix  3      [ ]         STREAM     CONNECTED     12131
unix  3      [ ]         STREAM     CONNECTED     11775    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11774
unix  2      [ ]         DGRAM                    11763
unix  2      [ ]         DGRAM                    11754
unix  2      [ ]         DGRAM                    11721
unix  2      [ ]         DGRAM                    11401
unix  4      [ ]         STREAM     CONNECTED     12041    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11371
unix  3      [ ]         STREAM     CONNECTED     10435    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10434
unix  3      [ ]         STREAM     CONNECTED     10417    @/tmp/hald-local/dbus-rXqbCYxlGY
unix  3      [ ]         STREAM     CONNECTED     10415
unix  3      [ ]         STREAM     CONNECTED     10416    @/tmp/hald-local/dbus-rXqbCYxlGY
unix  3      [ ]         STREAM     CONNECTED     10409
unix  3      [ ]         STREAM     CONNECTED     10403    @/tmp/hald-local/dbus-rXqbCYxlGY
unix  3      [ ]         STREAM     CONNECTED     10402
unix  3      [ ]         STREAM     CONNECTED     10393    @/tmp/hald-local/dbus-rXqbCYxlGY
unix  3      [ ]         STREAM     CONNECTED     10392
unix  3      [ ]         STREAM     CONNECTED     10347    @/tmp/hald-local/dbus-rXqbCYxlGY
unix  3      [ ]         STREAM     CONNECTED     10342
unix  3      [ ]         STREAM     CONNECTED     10237    /var/run/acpid.socketunix  3      [ ]         STREAM     CONNECTED     10236
unix  3      [ ]         STREAM     CONNECTED     10240    @/tmp/hald-local/dbus-rXqbCYxlGY
unix  3      [ ]         STREAM     CONNECTED     10231
unix  3      [ ]         STREAM     CONNECTED     10105    @/tmp/hald-runner/dbus-G2OOisOn1F
unix  3      [ ]         STREAM     CONNECTED     10104
unix  3      [ ]         STREAM     CONNECTED     10081
unix  3      [ ]         STREAM     CONNECTED     10080
unix  2      [ ]         DGRAM                    10071
johnnyw@johnnyw-desktop:~$

```

---

### Post by joe.turion64x2 on 2007-06-27
> **p_quarles said:**
> As far as I know, there are not yet any viruses that can infect Linux systems. It's just a matter of time, sure, but it will definitely **be big news** when it happens.

If you want to see where your automated network traffic is going, you can install the "Etherape" app from the repositories. It gives you a graphical overview of all the connections your system is making. Most of it is just checking e-mail, software updates, and RSS feeds.
Surely it will make headlines thanks to MS cash. 

Isn't it the update daemon?

---

### Post by johnnyw on 2007-06-27
> **p_quarles said:**
> As far as I know, there are not yet any viruses that can infect Linux systems. It's just a matter of time, sure, but it will definitely be big news when it happens.

If you want to see where your automated network traffic is going, you can install the "Etherape" app from the repositories. It gives you a graphical overview of all the connections your system is making.** Most of it is just checking e-mail, software updates, and RSS feeds**.

I use webmail only.. I do not know what rss is

---

### Post by eternalsword on 2007-06-28
Have you installed any third party apps?  If not, then there is no way you could possibly have a virus.  Linux is not like Windows where a virus can invade your system without having installed it yourself.

---

### Post by speaker219 on 2007-06-28
--

---

### Post by deadgobby on 2007-06-28
I do not think you are in any way infected. To infect your Linux system you need to invoke it. That is you are logged in as root and invoke it. There is 45 known linux virus's out there and your chances are way low. To compare to windows worms and virus's rolling around.  For now a linux virus cannot attack the whole linux kernel. It only can attack a certain program. All you need to do is reload the program and virus is gone. Linux is like a hall way with many doors. Like in the Matrix movie when Neo walks into a hall way full of green doors. A linux virus can only effect one this time one door. As linux gets bigger there will be a threat on worms and virus's to attack the system. 
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
Gobby

---

### Post by Tomosaur on 2007-06-28
From your info, I can't see anything that would cause alarm. The network activity appears to be ordinary idle traffic, so nothing to worry about there.

For those people saying there are no Linux viruses - there are. The problem with viruses is that nobody knows about them until they're found. The current estimate of viruses in the wild is so small as to be effectively zero, when compared to say, Windows, but there is no way of really knowing. Added to this, the chances of a virus successfully infecting a Linux machine are incredibly slim, but it's not unheard of.

---

