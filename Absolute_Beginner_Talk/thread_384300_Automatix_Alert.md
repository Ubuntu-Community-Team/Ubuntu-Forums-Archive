---
title: "Automatix Alert"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by jamere on 2007-03-14
When I start Automatix the following popup is displayed...

Automatix: Alert!

Synaptic is running
Please close

Synaptic is NOT running and Automatix closes. Anyone know what the deal is?

Thanks,
Jim M

---

### Post by taurus on 2007-03-14
Do you have adept running in the background then?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ps -A
```

---

### Post by lamalex on 2007-03-14
also check if you have updates waiting for you, you need to install them first.

---

### Post by finferflu on 2007-03-14
I've had exactly the same problem in some previous Ubuntu installs (yes, I mess it up often :P). Even runnning ps -A I wouldn't find any synaptic/apt process running. That was puzzling... I never managed to solve it before reinstalling again...

---

### Post by jamere on 2007-03-14
No synaptic, apt running or updates awaiting. There have been Automatix updates the past couple of days however. The updates weren't documented so don't know what they were trying to accomplish. Here's the process list:

jim@jim-desktop:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:02 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
   75 ?        00:00:00 kseriod
  110 ?        00:00:29 kswapd0
  111 ?        00:00:00 aio/0
 1672 ?        00:00:00 khubd
 1754 ?        00:00:02 kjournald
 1827 ?        00:00:00 logd
 1974 ?        00:00:00 udevd
 2740 ?        00:00:00 kpsmoused
 2785 ?        00:00:00 shpchpd
 3570 tty1     00:00:00 getty
 3571 tty2     00:00:00 getty
 3572 tty3     00:00:00 getty
 3573 tty4     00:00:00 getty
 3574 tty5     00:00:00 getty
 3575 tty6     00:00:00 getty
 3786 ?        00:00:00 acpid
 3909 ?        00:00:02 dd
 3911 ?        00:00:00 klogd
 3945 ?        00:00:00 gdm
 4128 ?        00:00:00 hpiod
 4153 ?        00:00:01 python
 4243 ?        00:00:00 dbus-daemon
 4258 ?        00:00:06 hald
 4259 ?        00:00:00 hald-runner
 4331 ?        00:00:00 hald-addon-acpi
 4509 ?        00:00:00 hald-addon-keyb
 4523 ?        00:00:01 hald-addon-stor
 4545 ?        00:00:00 perl
 4588 ?        00:00:00 exim4
 5027 ?        00:00:00 hcid
 5034 ?        00:00:00 sdpd
 5045 ?        00:00:00 krfcommd
 5064 ?        00:00:01 ntpd
 5096 ?        00:00:00 atd
 5109 ?        00:00:00 cron
 5197 ?        00:00:00 ntpd
 5201 ?        00:00:00 dhclient3
 6267 ?        00:00:00 oafd
24528 ?        00:00:02 artsd
20758 ?        00:00:08 gksu
20761 ?        00:00:00 sudo
 5490 ?        00:00:00 pppd
27582 ?        00:00:00 pdflush
28934 ?        00:00:01 gconfd-2
28949 ?        00:00:00 gdm
28954 tty7     00:12:38 Xorg
28983 ?        00:00:00 x-session-manag
29019 ?        00:00:00 ssh-agent
29022 ?        00:00:00 dbus-launch
29023 ?        00:00:00 dbus-daemon
29026 ?        00:00:00 gnome-keyring-d
29029 ?        00:00:05 gnome-settings-
29038 ?        00:00:00 sh
29039 ?        00:00:00 esd
29046 ?        00:00:27 metacity
29051 ?        00:00:32 gnome-panel
29053 ?        00:00:18 nautilus
29057 ?        00:00:00 bonobo-activati
29062 ?        00:00:00 update-notifier
29063 ?        00:00:00 gnome-volume-ma
29066 ?        00:00:00 gnome-vfs-daemo
29076 ?        00:00:02 gksu
29078 ?        00:00:00 evolution-alarm
29082 ?        00:00:05 gnome-cups-icon
29084 ?        00:00:40 firestarter
29090 ?        00:00:00 gnome-power-man
29104 ?        00:00:00 sh
29105 ?        00:00:00 esd
29109 ?        00:00:00 trashapplet
29113 ?        00:00:00 evolution-data-
29115 ?        00:00:00 mapping-daemon
29149 ?        00:00:00 evolution-excha
29157 ?        00:00:00 multiload-apple
29177 ?        00:00:00 gnome-dictionar
29515 ?        00:00:01 tomboy
29517 ?        00:00:12 stickynotes_app
29530 ?        00:00:02 gweather-applet
29544 ?        00:00:00 mixer_applet2
29552 ?        00:00:07 gnome-screensav
32352 ?        00:00:00 kdeinit
32355 ?        00:00:00 dcopserver
32358 ?        00:00:00 klauncher
32360 ?        00:00:01 kded
32381 ?        00:00:00 kio_file
32499 ?        00:00:00 knotify
 1680 ?        00:00:00 mozilla-thunder
 1684 ?        00:00:00 run-mozilla.sh
 1688 ?        00:02:00 mozilla-thunder
 4878 ?        00:02:47 firefox-bin
 4909 ?        00:00:00 netstat <defunct>
 5176 ?        00:10:32 acroread <defunct>
 7273 ?        00:00:00 cupsd
23296 ?        00:00:00 syslogd
23315 ?        00:00:00 notification-da
23399 ?        00:00:00 gksu
23402 ?        00:00:00 sudo
23762 ?        00:00:00 pdflush
26832 ?        00:00:00 gnome-terminal
26837 ?        00:00:00 gnome-pty-helpe
26838 pts/0    00:00:00 bash
26857 pts/0    00:00:00 ps
jim@jim-desktop:~$

---

### Post by taurus on 2007-03-14
What happens if you run these two commands from a terminal?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by jamere on 2007-03-14
taurus, here's what I get...

jim@jim-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Get:4 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                   
Get:7 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]         
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release           
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages                       
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Fetched 10B in 3s (3B/s) 
Reading package lists... Done
jim@jim-desktop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jim@jim-desktop:~$ 
jim@jim-desktop:~$

---

### Post by jamere on 2007-03-14
Still getting the Automatix alert popup when I start Automatix...

---

### Post by familyjules74123 on 2007-03-14
try reinstalling automatix maybe?

---

### Post by jackrobinson on 2007-03-14
why not ask on the automatix forums?
[http://www.getautomatix.com/forum](http://www.getautomatix.com/forum) 
The quality of support is really good there.

---

### Post by mahiyar on 2007-03-14
In the automatix forum somebody has posted this problem, the link is here [http://www.getautomatix.com/forum/index.php?showtopic=709](http://www.getautomatix.com/forum/index.php?showtopic=709) , unfortunately the problem seems unresolved.

---

### Post by jamere on 2007-03-14
Thanks everyone for comments and suggestion. As mahiyar noted...looks to be unresolved. 

Jim

---

