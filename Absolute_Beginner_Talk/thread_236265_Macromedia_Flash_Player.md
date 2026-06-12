---
title: "Macromedia Flash Player"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-08-14
The sound in Macromedia Flash Player didn't work for me, then I posted looking for help and someone told me to enter the following into the command line:

```
sudo apt-get install flashplugin-nonfree
sudo update-flashplugin
```

This didn't fix the sound, and I already had the plugin...

So someone told me to try this:

```
sudo ln -s /tmp/.esd-1000 /tmp/.esd
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
sudo mkdir -p /tmp/.esd/
sudo touch /tmp/.esd/socket

```

And this worked. I could hear sound again in Macromedia Flash Player.

But then, today, I logged in and tried viewing the same thing online with the plugin, but the sound is gone again. I tried redoing all the commands in the terminal, but none have worked.

Can someone help me with this?

---

### Post by deadgobby on 2006-08-14
Do you have a sound card or on board sound? If you have a sound card, have you tried to disable the onboard sound in the BIOS? 
Gobby

---

### Post by Ambimom on 2006-08-14
There's a bug in some configurations....> [Bug 45786] Re: default sound card is randomly set on boot, settting default sound card through gnome-sound-properties did not work correctly, changing volume through hotkeys (on logitech multimedia keyboard) is bind with card0, not with default card  [https://launchpad.net/bugs/45786](https://launchpad.net/bugs/45786)

I have this bug and when it boots to "usb" I get no sound in Flashplayer either.  Then I reboot and get "ich5" and everything works perfectly again.  It's maddening, ](*,) but harmless.

Maybe that's your problem?  Check your system preferences Sound and see if there's more than one sound card default.

---

### Post by emprog on 2006-08-14
This worked for me..
go to the following directory..
cd /etc/firefox

next edit the file firefoxrc changing this line-> FIREFOX_DSP="none" to FIREFOX_DSP="aoss"

---

### Post by kbsuperstar on 2006-08-14
I only have one sound card set as the default, and only one sound card on my motherboard. I tried changing that setting in firefoxrc to "aoss," but still no sound. I can hear music fine from my speakers when I play it in amaroK.

Any other suggestions?

---

### Post by emprog on 2006-08-14
One more thing, open terminal and try this..

sudo apt-get install alsa-oss

Then make sure you restart your browser. Hope this helps.

---

### Post by kbsuperstar on 2006-08-14
Nopa, alsa-oss is already installed and upgraded. So, it didn't work. Damn.. 


Any other suggestions?

---

### Post by M+J on 2006-08-25
I think that this is a bug in macromedia. I have the same problem, One day it works next day no sound and I dont have a sound card.](*,)

---

### Post by klytu on 2006-08-25
> **M+J said:**
> I think that this is a bug in macromedia. I have the same problem, One day it works next day no sound and I dont have a sound card.](*,)

This might be due to a conflict with another sound daemon running at the same time. Please post the output of 

```
ps -ef
```

---

### Post by M+J on 2006-08-25
This might be due to a conflict with another sound daemon running at the same time. Please post the output of

Code:

ps -ef

oops I was out looking thru the forums and tryed this:

sudo apt-get install flashplugin-nonfree
sudo update-flashplug
and restarted firefox

it worked for now thanks anyway:-D

---

### Post by Uchiha Sasuke^^ on 2006-08-25
> **klytu said:**
> This might be due to a conflict with another sound daemon running at the same time. Please post the output of 

```
ps -ef
```

i have da same problem! ](*,) 

root@sasuke-pc:/home/sasuke# ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 09:49 ?        00:00:01 init [2]
root         2     1  0 09:49 ?        00:00:00 [ksoftirqd/0]
root         3     1  0 09:49 ?        00:00:00 [watchdog/0]
root         4     1  0 09:49 ?        00:00:00 [events/0]
root         5     1  0 09:49 ?        00:00:00 [khelper]
root         6     1  0 09:49 ?        00:00:00 [kthread]
root         8     6  0 09:49 ?        00:00:00 [kblockd/0]
root         9     6  0 09:49 ?        00:00:00 [kacpid]
root       158     6  0 09:49 ?        00:00:00 [pdflush]
root       159     6  0 09:49 ?        00:00:00 [pdflush]
root       161     6  0 09:49 ?        00:00:00 [aio/0]
root       160     1  0 09:49 ?        00:00:00 [kswapd0]
root       748     6  0 09:49 ?        00:00:00 [kseriod]
root      1764     6  0 09:49 ?        00:00:00 [ata/0]
root      1765     6  0 09:49 ?        00:00:00 [ata_hotplug/0]
root      1768     6  0 09:49 ?        00:00:00 [scsi_eh_0]
root      1769     6  0 09:49 ?        00:00:00 [scsi_eh_1]
root      1838     6  0 09:49 ?        00:00:00 [khubd]
root      1850     1  0 09:49 ?        00:00:00 [khpsbpkt]
root      1868     1  0 09:49 ?        00:00:00 [knodemgrd_0]
root      1947     1  0 09:49 ?        00:00:00 [kjournald]
root      2179     1  0 09:49 ?        00:00:00 /sbin/udevd --daemon
root      2966     1  0 09:49 ?        00:00:00 [shpchpd_event]
root      3040     6  0 09:49 ?        00:00:00 [kgameportd]
dhcp      3630     1  0 09:50 ?        00:00:00 dhclient3 -pf /var/run/dhclient.
root      3909     1  0 09:50 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
root      4027     1  0 09:50 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      4033     1  0 09:50 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
root      4348     1  0 09:50 ?        00:00:00 /usr/sbin/gdm
root      4369  4348  0 09:50 ?        00:00:00 /usr/sbin/gdm
root      4382  4369  0 09:50 tty7     00:00:06 /usr/bin/X :0 -br -audit 0 -auth
hplip     4391     1  0 09:50 ?        00:00:00 /usr/sbin/hpiod
hplip     4398     1  0 09:50 ?        00:00:00 python /usr/sbin/hpssd
104       4470     1  0 09:50 ?        00:00:00 /usr/bin/dbus-daemon --system
108       4485     1  0 09:50 ?        00:00:00 /usr/sbin/hald
root      4486  4485  0 09:50 ?        00:00:00 hald-runner
108       4491  4486  0 09:50 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
108       4545  4486  0 09:50 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
sasuke    4558  4369  0 09:50 ?        00:00:00 /bin/bash /usr/bin/startxgl.sh
root      4683     1  0 09:50 ?        00:00:00 /usr/sbin/xinetd -pidfile /var/r
root      4687     1  0 09:50 ?        00:00:00 hcid: processing events
root      4691     1  0 09:50 ?        00:00:00 /usr/sbin/sdpd
sasuke    4704  4558  0 09:50 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
sasuke    4708     1  0 09:50 ?        00:00:00 /usr/bin/dbus-launch --exit-with
root      4709     1  0 09:50 ?        00:00:00 [krfcommd]
root      4723     1  0 09:50 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadm
sasuke    4753     1  0 09:50 ?        00:00:00 dbus-daemon --fork --print-pid 8
sasuke    4758  4558  6 09:50 ?        00:02:25 Xgl -fullscreen :1 -ac -br -acce
daemon    4760     1  0 09:50 ?        00:00:00 /usr/sbin/atd
root      4773     1  0 09:50 ?        00:00:00 /usr/sbin/cron
root      4816     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-bridge -d /var/ru
root      4830     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-natd -d /var/run/
root      4836     1  0 09:50 ?        00:00:00 /usr/sbin/vmware-serverd -s -d
sasuke    4890  4558  0 09:50 ?        00:00:00 gnome-session
root      4902     1  0 09:50 tty1     00:00:00 /sbin/getty 38400 tty1
root      4903     1  0 09:50 tty2     00:00:00 /sbin/getty 38400 tty2
root      4904     1  0 09:50 tty3     00:00:00 /sbin/getty 38400 tty3
root      4905     1  0 09:50 tty4     00:00:00 /sbin/getty 38400 tty4
root      4906     1  0 09:50 tty5     00:00:00 /sbin/getty 38400 tty5
root      4907     1  0 09:50 tty6     00:00:00 /sbin/getty 38400 tty6
sasuke    4919     1  0 09:50 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 5
sasuke    4922     1  0 09:50 ?        00:00:00 /usr/bin/gnome-keyring-daemon
sasuke    4924     1  0 09:50 ?        00:00:00 /usr/lib/bonobo-activation/bonob
sasuke    4926     1  0 09:50 ?        00:00:01 /usr/lib/control-center/gnome-se
sasuke    4928     1  0 09:50 ?        00:00:00 /usr/bin/esd -terminate -nobeeps
sasuke    4937     1  0 09:50 ?        00:00:00 /usr/lib/vino/vino-server --oaf-
sasuke    4947     1  0 09:50 ?        00:00:05 gnome-panel --sm-client-id defau
sasuke    4949     1  0 09:50 ?        00:00:01 nautilus --no-default-window --s
sasuke    4954     1  0 09:50 ?        00:00:00 gnome-volume-manager --sm-client
sasuke    4960     1  0 09:50 ?        00:00:00 update-notifier
sasuke    4970     1  0 09:50 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs
sasuke    4973     1  0 09:50 ?        00:00:02 gnome-cups-icon --sm-client-id d
sasuke    4974     1  0 09:50 ?        00:00:04 cgwd
sasuke    4981     1  0 09:50 ?        00:00:07 compiz.real --replace gconf
sasuke    4987     1  0 09:50 ?        00:00:00 gnome-power-manager
root      4994     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-netifup -d /var/r
root      4992     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-netifup -d /var/r
sasuke    5021     1  0 09:50 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapp
root      5023     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-dhcpd -cf /etc/vm
root      5024     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-dhcpd -cf /etc/vm
sasuke    5030     1  0 09:50 ?        00:00:00 /usr/lib/gnome-applets/gweather-
sasuke    5032     1  0 09:50 ?        00:00:00 /usr/lib/gnome-panel/clock-apple
sasuke    5034     1  0 09:50 ?        00:00:00 /usr/lib/gnome-applets/mixer_app
sasuke    5043     1  3 09:50 ?        00:01:20 /usr/lib/amarok/amarokapp
sasuke    5045     1  0 09:50 ?        00:00:00 kdeinit Running...
sasuke    5049     1  0 09:50 ?        00:00:00 dcopserver [kdeinit] --nosid --s
sasuke    5051  5045  0 09:50 ?        00:00:00 klauncher [kdeinit]
sasuke    5053     1  0 09:50 ?        00:00:00 kded [kdeinit]
sasuke    5056     1  0 09:50 ?        00:00:09 /usr/lib/gamin/gam_server
sasuke    5066  5045  0 09:50 ?        00:00:00 kio_file [kdeinit] file /tmp/kso
sasuke    5073     1  0 09:50 ?        00:00:01 gnome-screensaver
dhcp      5108     1  0 09:51 ?        00:00:00 dhclient3 -pf /var/run/dhclient.
sasuke    5173     1  2 09:53 ?        00:00:59 /usr/lib/firefox/firefox-bin -a
cupsys    5367     1  0 09:55 ?        00:00:00 /usr/sbin/cupsd
syslog    5630     1  0 09:56 ?        00:00:00 /sbin/syslogd -u syslog
sasuke    5674     1  0 09:57 ?        00:00:00 /usr/lib/notification-daemon/not
sasuke    6604     1  0 10:16 ?        00:00:06 gaim
sasuke    6675     1  0 10:18 ?        00:00:00 gksu /usr/bin/x-terminal-emulato
root      6676  6675  0 10:18 ?        00:00:01 gnome-terminal
root      6680     1  0 10:18 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 11
root      6682     1  0 10:18 ?        00:00:00 /usr/lib/bonobo-activation/bonob
root      6685  6676  0 10:18 ?        00:00:00 gnome-pty-helper
root      6686  6676  0 10:18 pts/0    00:00:00 bash
sasuke    7054     1  0 10:24 ?        00:00:00 /usr/lib/amarok/amarokapp
root      7186  6676  0 10:29 pts/1    00:00:00 bash
sasuke    7212  6604  0 10:29 ?        00:00:00 gaim
root      7215  7186  0 10:29 pts/1    00:00:00 ps -ef

---

### Post by klytu on 2006-08-25
> **Uchiha Sasuke^^ said:**
> i have da same problem! ](*,) 

root@sasuke-pc:/home/sasuke# ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 09:49 ?        00:00:01 init [2]
root         2     1  0 09:49 ?        00:00:00 [ksoftirqd/0]
root         3     1  0 09:49 ?        00:00:00 [watchdog/0]
root         4     1  0 09:49 ?        00:00:00 [events/0]
root         5     1  0 09:49 ?        00:00:00 [khelper]
root         6     1  0 09:49 ?        00:00:00 [kthread]
root         8     6  0 09:49 ?        00:00:00 [kblockd/0]
root         9     6  0 09:49 ?        00:00:00 [kacpid]
root       158     6  0 09:49 ?        00:00:00 [pdflush]
root       159     6  0 09:49 ?        00:00:00 [pdflush]
root       161     6  0 09:49 ?        00:00:00 [aio/0]
root       160     1  0 09:49 ?        00:00:00 [kswapd0]
root       748     6  0 09:49 ?        00:00:00 [kseriod]
root      1764     6  0 09:49 ?        00:00:00 [ata/0]
root      1765     6  0 09:49 ?        00:00:00 [ata_hotplug/0]
root      1768     6  0 09:49 ?        00:00:00 [scsi_eh_0]
root      1769     6  0 09:49 ?        00:00:00 [scsi_eh_1]
root      1838     6  0 09:49 ?        00:00:00 [khubd]
root      1850     1  0 09:49 ?        00:00:00 [khpsbpkt]
root      1868     1  0 09:49 ?        00:00:00 [knodemgrd_0]
root      1947     1  0 09:49 ?        00:00:00 [kjournald]
root      2179     1  0 09:49 ?        00:00:00 /sbin/udevd --daemon
root      2966     1  0 09:49 ?        00:00:00 [shpchpd_event]
root      3040     6  0 09:49 ?        00:00:00 [kgameportd]
dhcp      3630     1  0 09:50 ?        00:00:00 dhclient3 -pf /var/run/dhclient.
root      3909     1  0 09:50 ?        00:00:00 /usr/sbin/acpid -c /etc/acpi/eve
root      4027     1  0 09:50 ?        00:00:00 /bin/dd bs 1 if /proc/kmsg of /v
klog      4033     1  0 09:50 ?        00:00:00 /sbin/klogd -P /var/run/klogd/km
root      4348     1  0 09:50 ?        00:00:00 /usr/sbin/gdm
root      4369  4348  0 09:50 ?        00:00:00 /usr/sbin/gdm
root      4382  4369  0 09:50 tty7     00:00:06 /usr/bin/X :0 -br -audit 0 -auth
hplip     4391     1  0 09:50 ?        00:00:00 /usr/sbin/hpiod
hplip     4398     1  0 09:50 ?        00:00:00 python /usr/sbin/hpssd
104       4470     1  0 09:50 ?        00:00:00 /usr/bin/dbus-daemon --system
108       4485     1  0 09:50 ?        00:00:00 /usr/sbin/hald
root      4486  4485  0 09:50 ?        00:00:00 hald-runner
108       4491  4486  0 09:50 ?        00:00:00 /usr/lib/hal/hald-addon-acpi
108       4545  4486  0 09:50 ?        00:00:00 /usr/lib/hal/hald-addon-keyboard
sasuke    4558  4369  0 09:50 ?        00:00:00 /bin/bash /usr/bin/startxgl.sh
root      4683     1  0 09:50 ?        00:00:00 /usr/sbin/xinetd -pidfile /var/r
root      4687     1  0 09:50 ?        00:00:00 hcid: processing events
root      4691     1  0 09:50 ?        00:00:00 /usr/sbin/sdpd
sasuke    4704  4558  0 09:50 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus
sasuke    4708     1  0 09:50 ?        00:00:00 /usr/bin/dbus-launch --exit-with
root      4709     1  0 09:50 ?        00:00:00 [krfcommd]
root      4723     1  0 09:50 ?        00:00:00 /sbin/mdadm -F -i /var/run/mdadm
sasuke    4753     1  0 09:50 ?        00:00:00 dbus-daemon --fork --print-pid 8
sasuke    4758  4558  6 09:50 ?        00:02:25 Xgl -fullscreen :1 -ac -br -acce
daemon    4760     1  0 09:50 ?        00:00:00 /usr/sbin/atd
root      4773     1  0 09:50 ?        00:00:00 /usr/sbin/cron
root      4816     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-bridge -d /var/ru
root      4830     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-natd -d /var/run/
root      4836     1  0 09:50 ?        00:00:00 /usr/sbin/vmware-serverd -s -d
sasuke    4890  4558  0 09:50 ?        00:00:00 gnome-session
root      4902     1  0 09:50 tty1     00:00:00 /sbin/getty 38400 tty1
root      4903     1  0 09:50 tty2     00:00:00 /sbin/getty 38400 tty2
root      4904     1  0 09:50 tty3     00:00:00 /sbin/getty 38400 tty3
root      4905     1  0 09:50 tty4     00:00:00 /sbin/getty 38400 tty4
root      4906     1  0 09:50 tty5     00:00:00 /sbin/getty 38400 tty5
root      4907     1  0 09:50 tty6     00:00:00 /sbin/getty 38400 tty6
sasuke    4919     1  0 09:50 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 5
sasuke    4922     1  0 09:50 ?        00:00:00 /usr/bin/gnome-keyring-daemon
sasuke    4924     1  0 09:50 ?        00:00:00 /usr/lib/bonobo-activation/bonob
sasuke    4926     1  0 09:50 ?        00:00:01 /usr/lib/control-center/gnome-se
sasuke    4928     1  0 09:50 ?        00:00:00 /usr/bin/esd -terminate -nobeeps
sasuke    4937     1  0 09:50 ?        00:00:00 /usr/lib/vino/vino-server --oaf-
sasuke    4947     1  0 09:50 ?        00:00:05 gnome-panel --sm-client-id defau
sasuke    4949     1  0 09:50 ?        00:00:01 nautilus --no-default-window --s
sasuke    4954     1  0 09:50 ?        00:00:00 gnome-volume-manager --sm-client
sasuke    4960     1  0 09:50 ?        00:00:00 update-notifier
sasuke    4970     1  0 09:50 ?        00:00:00 /usr/lib/gnome-vfs-2.0/gnome-vfs
sasuke    4973     1  0 09:50 ?        00:00:02 gnome-cups-icon --sm-client-id d
sasuke    4974     1  0 09:50 ?        00:00:04 cgwd
sasuke    4981     1  0 09:50 ?        00:00:07 compiz.real --replace gconf
sasuke    4987     1  0 09:50 ?        00:00:00 gnome-power-manager
root      4994     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-netifup -d /var/r
root      4992     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-netifup -d /var/r
sasuke    5021     1  0 09:50 ?        00:00:00 /usr/lib/nautilus-cd-burner/mapp
root      5023     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-dhcpd -cf /etc/vm
root      5024     1  0 09:50 ?        00:00:00 /usr/bin/vmnet-dhcpd -cf /etc/vm
sasuke    5030     1  0 09:50 ?        00:00:00 /usr/lib/gnome-applets/gweather-
sasuke    5032     1  0 09:50 ?        00:00:00 /usr/lib/gnome-panel/clock-apple
sasuke    5034     1  0 09:50 ?        00:00:00 /usr/lib/gnome-applets/mixer_app
sasuke    5043     1  3 09:50 ?        00:01:20 /usr/lib/amarok/amarokapp
sasuke    5045     1  0 09:50 ?        00:00:00 kdeinit Running...
sasuke    5049     1  0 09:50 ?        00:00:00 dcopserver [kdeinit] --nosid --s
sasuke    5051  5045  0 09:50 ?        00:00:00 klauncher [kdeinit]
sasuke    5053     1  0 09:50 ?        00:00:00 kded [kdeinit]
sasuke    5056     1  0 09:50 ?        00:00:09 /usr/lib/gamin/gam_server
sasuke    5066  5045  0 09:50 ?        00:00:00 kio_file [kdeinit] file /tmp/kso
sasuke    5073     1  0 09:50 ?        00:00:01 gnome-screensaver
dhcp      5108     1  0 09:51 ?        00:00:00 dhclient3 -pf /var/run/dhclient.
sasuke    5173     1  2 09:53 ?        00:00:59 /usr/lib/firefox/firefox-bin -a
cupsys    5367     1  0 09:55 ?        00:00:00 /usr/sbin/cupsd
syslog    5630     1  0 09:56 ?        00:00:00 /sbin/syslogd -u syslog
sasuke    5674     1  0 09:57 ?        00:00:00 /usr/lib/notification-daemon/not
sasuke    6604     1  0 10:16 ?        00:00:06 gaim
sasuke    6675     1  0 10:18 ?        00:00:00 gksu /usr/bin/x-terminal-emulato
root      6676  6675  0 10:18 ?        00:00:01 gnome-terminal
root      6680     1  0 10:18 ?        00:00:00 /usr/lib/libgconf2-4/gconfd-2 11
root      6682     1  0 10:18 ?        00:00:00 /usr/lib/bonobo-activation/bonob
root      6685  6676  0 10:18 ?        00:00:00 gnome-pty-helper
root      6686  6676  0 10:18 pts/0    00:00:00 bash
sasuke    7054     1  0 10:24 ?        00:00:00 /usr/lib/amarok/amarokapp
root      7186  6676  0 10:29 pts/1    00:00:00 bash
sasuke    7212  6604  0 10:29 ?        00:00:00 gaim
root      7215  7186  0 10:29 pts/1    00:00:00 ps -ef

You might want to try killing esd; that's the only process I could find that might be in conflict. Usually esd doesn't cause a problem for me, but occasionally it kills flash sound. Try:

```
sudo killall esd
```

Then close and restart firefox and try your flash sound.

---

### Post by Uchiha Sasuke^^ on 2006-08-27
thanks, that solves my problem, but i have to do it every time! mayby a solution to this?

---

### Post by klytu on 2006-08-27
> **Uchiha Sasuke^^ said:**
> thanks, that solves my problem, but i have to do it every time! mayby a solution to this?

Yeah, me too basically! :-( I also installed Kubuntu to see if the same kind of sound conflict happens (KDE uses artsd by default instead of esd which is used in Ubuntu by default) and it happens in KDE as well, but not as often. The sound in flash goes away less frequently when I configure Ubuntu and Kubuntu not to play any system, start up, or log out sounds. But it still happens from time to time when some app starts up esd or artsd to play sounds.

I think a possible solution might be to write a script that would run in the background and kill any running sound daemons when they are no longer playing anything, but I don't know how to do that yet.

---

### Post by Uchiha Sasuke^^ on 2006-08-28
> **klytu said:**
> Yeah, me too basically! :-( I also installed Kubuntu to see if the same kind of sound conflict happens (KDE uses artsd by default instead of esd which is used in Ubuntu by default) and it happens in KDE as well, but not as often. The sound in flash goes away less frequently when I configure Ubuntu and Kubuntu not to play any system, start up, or log out sounds. But it still happens from time to time when some app starts up esd or artsd to play sounds.

I think a possible solution might be to write a script that would run in the background and kill any running sound daemons when they are no longer playing anything, but I don't know how to do that yet.

me neither, but thankz for the help anyway, now i have the posibility of playing flash with sound xD

---

