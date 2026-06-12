---
title: "automatix2"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Bigadada_saba on 2007-03-11
Hi every time i click to startup automatix  it just opens and then shuts down.  can any one help me with this

---

### Post by overdrank on 2007-03-11
> **Bigadada_saba said:**
> Hi every time i click to startup automatix  it just opens and then shuts down.  can any one help me with this

Hi are you asked for your password?

---

### Post by ziffnabb on 2007-03-11
Hey, me too!  I just upgraded to 2 using synaptic and now automatix won't run.  It does the same thing as for you?  Help!

Ziffnabb

---

### Post by taurus on 2007-03-11
Try to run it from a terminal to see what the problem is.

Applications -> Accessories -> Terminal
```
gksudo automatix2
```

---

### Post by ziffnabb on 2007-03-11
I did a beboot, then ran the command from terminal, and got a message that automatix is already running.

Any ideas?
Thanks,
ziffnabb

---

### Post by zemitras on 2007-03-11
I there, I have exactly the same problem... 

If I start automatix  by menus -> applications > System tools -> automatix , program appears to start but shuts down really fast 

If I start by terminal -> automatix2, I get a message that automatix is already running.

Don't know what to do now.. please help 

Regards

---

### Post by taurus on 2007-03-11
What's the output of this command from a terminal?

```
ps -A
```

---

### Post by rocknrolf77 on 2007-03-11
It's a bit Norwegian in here, but maybe not the important part. This happened after todays update of automatix2. It was working right before the update. 


> Starting
Traceback (most recent call last):
  File "/usr/bin/automatix.py", line 68, in ?
    main = main_ui()
  File "/usr/lib/automatix2/main_interface.py", line 12, in __init__
    self.build_interface()
  File "/usr/lib/automatix2/main_interface.py", line 50, in build_interface
    self.generate_menus()
  File "/usr/lib/automatix2/main_interface.py", line 104, in generate_menus
    self.generate_catalog_model()
  File "/usr/lib/automatix2/main_interface.py", line 365, in generate_catalog_model
    icon= gtk.gdk.pixbuf_new_from_file(list.icon)
gobject.GError: Klarte ikke å åpne fil «/usr/share/icons/Tango/24x24/devices/multimedia-player-ipod-video-black.png»: No such file or directory



Klarte ikke å åpne fil = Could not open file

---

### Post by zemitras on 2007-03-11
here it is the output from "ps -A" command: 

```
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  100 ?        00:00:00 kseriod
  133 ?        00:00:00 pdflush
  134 ?        00:00:00 pdflush
  135 ?        00:00:00 kswapd0
  136 ?        00:00:00 aio/0
 1722 ?        00:00:00 ata/0
 1728 ?        00:00:00 scsi_eh_0
 1729 ?        00:00:00 scsi_eh_1
 1730 ?        00:00:00 scsi_eh_2
 1834 ?        00:00:00 khubd
 1856 ?        00:00:00 khpsbpkt
 1866 ?        00:00:00 knodemgrd_0
 1932 ?        00:00:00 kjournald
 2011 ?        00:00:00 logd
 2157 ?        00:00:00 udevd
 2877 ?        00:00:00 shpchpd
 3107 ?        00:00:00 kpsmoused
 3461 ?        00:00:00 kjournald
 3773 tty1     00:00:00 getty
 3774 tty2     00:00:00 getty
 3775 tty3     00:00:00 getty
 3776 tty4     00:00:00 getty
 3777 tty5     00:00:00 getty
 3778 tty6     00:00:00 getty
 3987 ?        00:00:00 acpid
 4084 ?        00:00:00 syslogd
 4110 ?        00:00:00 dd
 4112 ?        00:00:00 klogd
 4184 ?        00:00:00 gdm
 4185 ?        00:00:00 gdm
 4204 tty7     00:00:06 Xorg
 4222 ?        00:00:00 cupsd
 4239 ?        00:00:00 hpiod
 4247 ?        00:00:00 python
 4297 ?        00:00:00 dbus-daemon
 4312 ?        00:00:03 hald
 4313 ?        00:00:00 hald-runner
 4319 ?        00:00:00 hald-addon-acpi
 4344 ?        00:00:00 hald-addon-keyb
 4359 ?        00:00:00 hald-addon-stor
 4381 ?        00:00:00 perl
 4624 ?        00:00:00 vmnet-bridge
 4638 ?        00:00:00 vmnet-natd
 4695 ?        00:00:00 hcid
 4699 ?        00:00:00 xinetd
 4700 ?        00:00:00 sdpd
 4717 ?        00:00:00 krfcommd
 4736 ?        00:00:00 x-session-manag
 4753 ?        00:00:00 atd
 4767 ?        00:00:00 cron
 4886 ?        00:00:00 ssh-agent
 4889 ?        00:00:00 dbus-launch
 4890 ?        00:00:00 dbus-daemon
 4892 ?        00:00:00 gconfd-2
 4895 ?        00:00:00 gnome-keyring-d
 4898 ?        00:00:00 gnome-settings-
 4907 ?        00:00:00 sh
 4908 ?        00:00:00 esd
 4915 ?        00:00:01 metacity
 4920 ?        00:00:01 gnome-panel
 4922 ?        00:00:01 nautilus
 4926 ?        00:00:00 bonobo-activati
 4930 ?        00:00:00 gnome-vfs-daemo
 4933 ?        00:00:00 gnome-volume-ma
 4939 ?        00:00:00 update-notifier
 4955 ?        00:00:00 gnome-cups-icon
 4964 ?        00:00:00 gnome-power-man
 4966 ?        00:00:00 trashapplet
 4984 ?        00:00:00 mapping-daemon
 4991 ?        00:00:00 vmnet-netifup
 5001 ?        00:00:00 vmnet-netifup
 5020 ?        00:00:00 mixer_applet2
 5023 ?        00:00:00 vmnet-dhcpd
 5024 ?        00:00:00 vmnet-dhcpd
 5060 ?        00:00:00 gnome-screensav
 5098 ?        00:00:11 firefox-bin
 5136 ?        00:00:00 gnome-terminal
 5138 ?        00:00:00 gnome-pty-helpe
 5139 pts/0    00:00:00 bash
 5158 pts/0    00:00:00 ps

```

---

### Post by rocknrolf77 on 2007-03-11
```
ps -a
```

>   PID TTY          TIME CMD
20038 pts/1                       00:00:00 ps


---

### Post by taurus on 2007-03-11
Try something like

```
sudo kill -9 4939
gksudo automatix2
```

---

### Post by zemitras on 2007-03-11
> **rocknrolf77 said:**
> It's a bit Norwegian in here, but maybe not the important part. This happened after todays update of automatix2. It was working right before the update. 





Klarte ikke å åpne fil = Could not open file

See this post [http://ubuntuforums.org/showthread.php?t=381225&highlight=automatix](http://ubuntuforums.org/showthread.php?t=381225&highlight=automatix)

It doesn't work for me because I get a diferent error, but there's someone there with the same error you have

---

### Post by rocknrolf77 on 2007-03-11
> **taurus said:**
> Try something like

```
sudo kill -9 4939
gksudo automatix2
```


The same.

---

### Post by zemitras on 2007-03-11
> **taurus said:**
> Try something like

```
sudo kill -9 4939
gksudo automatix2
```

Got the same error.. pop up window saying "Automatix is already running, only one automatix session may be run at any time."

---

### Post by taurus on 2007-03-11
> **rocknrolf77 said:**
> The same.

It may not have the same PID so you need to post this output first.

```
ps -**A**
```

---

### Post by rocknrolf77 on 2007-03-11
> **zemitras said:**
> See this post [http://ubuntuforums.org/showthread.php?t=381225&highlight=automatix](http://ubuntuforums.org/showthread.php?t=381225&highlight=automatix)

It doesn't work for me because I get a diferent error, but there's someone there with the same error you have

Thanks, that fixed the problem. :)

---

### Post by taurus on 2007-03-11
> **zemitras said:**
> Got the same error.. pop up window saying "Automatix is already running, only one automatix session may be run at any time."

See if you can remove and reinstall it again.

```
sudo aptitude --purge remove automatix2
sudo aptitude update
sudo aptitude install automatix2
automatix2
```

---

### Post by zemitras on 2007-03-11
I have fixed the problem.. don't know exactly what It solved but I did remove and install automatix2 a few times, sometimes with apt-get others with synaptic and It suddenly Automatix2 was working

Thanks anyway for your help, best regards

---

### Post by jackrobinson on 2007-03-12
This bug affects Kubuntu Edgy 386 users on the latest version of automatix2. The report can be seen here:
[http://www.getautomatix.com/forum/index.php?showtopic=833](http://www.getautomatix.com/forum/index.php?showtopic=833)
The AX devs are working on it.

---

### Post by jackrobinson on 2007-03-12
update: apparently this bug has been fixed in version  1.1-2.22. Users have been advised to upgrade to this version of automatix2 to make it work on Kubuntu Edgy 386.

---

### Post by Bigadada_saba on 2007-03-12
thanks i uninstalled it and re installed it and its working good now

---

### Post by Sunflower1970 on 2007-03-12
> **jackrobinson said:**
> This bug affects Kubuntu Edgy 386 users on the latest version of automatix2. The report can be seen here:
[http://www.getautomatix.com/forum/index.php?showtopic=833](http://www.getautomatix.com/forum/index.php?showtopic=833)
The AX devs are working on it.


It's affecting gnome-flavored Ubuntu users too, not just KDE..I'm in the process now to see if uninstalling and reinstalling it will fix the problem for me....

---

### Post by jackrobinson on 2007-03-12
> **Sunflower1970 said:**
> It's affecting gnome-flavored Ubuntu users too, not just KDE..I'm in the process now to see if uninstalling and reinstalling it will fix the problem for me....

This bug has been fixed. Just upgrade to the latest and the greatest..
```
sudo apt-get update
sudo apt-get upgrade
```

---

