---
title: "libnullplugin.so"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by gorg on 2007-01-17
been trying to get flash and java plugins.  followed some instructions on here. no joy
did about:plugins and got this
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	                  all types            *                     No

that say it is not enabled. do i need it enabled for the plugins i installed to work?
and , if so, how do i go about enabling it.
thanks

---

### Post by Bachstelze on 2007-01-17
You don't need to worry about it. If your Flash and Java plugins do not appear in the list, you most certainly haven't installed them properly. Instructions about how to do it are [here](https://help.ubuntu.com/community/RestrictedFormats).

---

### Post by gorg on 2007-01-17
ok, thanks

---

### Post by gorg on 2007-01-18
i am still getting the install addtitional plugins at different sites
but

sudo update-alternatives --config firefox-javaplugin.so
Password:

There is only 1 program which provides firefox-javaplugin.so
(/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so). Nothing to configure.
 and this

java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)
and this
 sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

and this
 sudo update-alternatives --list java
/usr/bin/gij-wrapper-4.1
/usr/lib/jvm/java-gcj/jre/bin/java
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java

and this
 ps -A
  PID TTY          TIME CMD
    1 ?        00:00:02 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 watchdog/0
    4 ?        00:00:00 events/0
    5 ?        00:00:00 khelper
    6 ?        00:00:00 kthread
    8 ?        00:00:00 kblockd/0
    9 ?        00:00:00 kacpid
  100 ?        00:00:00 pdflush
  101 ?        00:00:00 pdflush
  103 ?        00:00:00 aio/0
  102 ?        00:00:00 kswapd0
  690 ?        00:00:00 kseriod
 1880 ?        00:00:00 khubd
 1978 ?        00:00:00 kjournald
 2204 ?        00:00:01 udevd
 3005 ?        00:00:00 shpchpd_event
 3132 ?        00:00:00 kgameportd
 3303 ?        00:00:00 dhclient3
 3928 ?        00:00:00 acpid
 4044 ?        00:00:00 dd
 4046 ?        00:00:00 klogd
 4065 ?        00:00:00 dbus-daemon
 4080 ?        00:00:04 hald
 4081 ?        00:00:00 hald-runner
 4086 ?        00:00:00 hald-addon-acpi
 4141 ?        00:00:00 hald-addon-keyb
 4148 ?        00:00:00 hald-addon-stor
 4149 ?        00:00:00 hald-addon-stor
 4151 ?        00:00:03 hald-addon-stor
 4152 ?        00:00:03 hald-addon-stor
 4476 ?        00:00:00 gdm
 4491 ?        00:00:00 gdm
 4497 tty7     00:59:58 Xorg
 4515 ?        00:00:00 hpiod
 4519 ?        00:00:00 python
 4813 ?        00:00:00 hcid
 4818 ?        00:00:00 sdpd
 4828 ?        00:00:00 krfcommd
 4841 ?        00:00:00 mdadm
 4875 ?        00:00:00 atd
 4888 ?        00:00:00 cron
 4960 tty1     00:00:00 getty
 4961 tty2     00:00:00 getty
 4962 tty3     00:00:00 getty
 4963 tty4     00:00:00 getty
 4964 tty5     00:00:00 getty
 4965 tty6     00:00:00 getty
 4976 ?        00:00:02 x-session-manag
 5018 ?        00:00:00 ssh-agent
 5021 ?        00:00:00 dbus-launch
 5022 ?        00:00:00 dbus-daemon
 5024 ?        00:00:01 gconfd-2
 5027 ?        00:00:00 gnome-keyring-d
 5029 ?        00:00:00 bonobo-activati
 5031 ?        00:00:08 gnome-settings-
 5035 ?        00:00:00 esd
 5037 ?        00:00:00 esd
 5042 ?        00:01:03 metacity
 5048 ?        00:00:26 gnome-panel
 5050 ?        00:00:08 nautilus
 5054 ?        00:00:01 trashapplet
 5057 ?        00:00:01 gnome-volume-ma
 5063 ?        00:00:00 gnome-vfs-daemo
 5061 ?        00:00:04 update-notifier
 5074 ?        00:00:01 gksu
 5078 ?        00:00:12 firestarter
 5084 ?        00:00:50 gnome-cups-icon
 5087 ?        00:00:00 mapping-daemon
 5091 ?        00:00:02 mixer_applet2
 5093 ?        00:00:02 clock-applet
 5098 ?        00:00:03 gnome-power-man
 5107 ?        00:00:00 gconfd-2
 5109 ?        00:00:00 esd
 5243 ?        00:00:08 gnome-screensav
 5772 ?        00:00:27 cupsd
 5922 ?        00:00:00 syslogd
 3711 ?        00:00:00 firefox
 3722 ?        00:00:00 run-mozilla.sh
 3727 ?        00:04:09 firefox-bin
 7354 ?        00:00:01 gnome-terminal
 7357 ?        00:00:00 gnome-pty-helpe
 7358 pts/0    00:00:00 bash
 7383 pts/0    00:00:00 ps

this is everything i could find in the forums concerning java. unless i missed something .
thanks

ps: on one thread , it was suggested to remove earier versions of java, not sure how to do that




  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

---

