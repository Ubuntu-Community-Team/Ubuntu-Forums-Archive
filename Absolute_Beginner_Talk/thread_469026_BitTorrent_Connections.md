---
title: "BitTorrent Connections"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by R00tBreaker on 2007-06-09
I'm using Firestarter as my firewall in ubuntu 7.04. When I logged in today and started up Firestarter, it instantly gave me about a 6 or 7 blocked connections on port 6881 (used by BitTorrent). It has never done this before. They are still going. It has blocked 100+ attempted connections in the past 5 minutes. Why has this never happened before and how can I stop it?

---

### Post by R00tBreaker on 2007-06-09
bump :-\"

---

### Post by shof2k on 2007-06-09
I don't know a lot about firewalls, but can you try the following.

i)  Are the blocked connections incoming or outgoing?

ii)  Port 6881 is used by bittorrent.  Are you sure it's not running in the background?

iii)  You can see if anything else is running, by opening a terminal and typing ```
 netstat -anp 
```.  Can you post the output here.

---

### Post by R00tBreaker on 2007-06-09
> **shof2k said:**
> I don't know a lot about firewalls, but can you try the following.

i)  Are the blocked connections incoming or outgoing?

ii)  Port 6881 is used by bittorrent.  Are you sure it's not running in the background?

iii)  You can see if anything else is running, by opening a terminal and typing ```
 netstat -anp 
```.  Can you post the output here.

The netstat command you gave me generated an output so large that it extends beyond what the terminal window can contain. I'm almost 100% positive BitTorrent isn't running in the background. ps -u [myusername] :

  PID TTY          TIME CMD
 5697 ?        00:00:00 bonobo-activati
 5743 ?        00:00:00 evolution-data-
11425 ?        00:00:00 x-session-manag
11467 ?        00:00:00 ssh-agent
11470 ?        00:00:00 dbus-launch
11471 ?        00:00:00 dbus-daemon
11473 ?        00:00:00 gconfd-2
11476 ?        00:00:00 gnome-keyring-d
11478 ?        00:00:00 gnome-settings-
11485 ?        00:00:00 sh
11486 ?        00:00:00 esd
11490 ?        00:00:03 metacity
11493 ?        00:00:01 gnome-panel
11499 ?        00:00:00 nautilus
11502 ?        00:00:00 gnome-vfs-daemo
11508 ?        00:00:00 update-notifier
11510 ?        00:00:00 evolution-alarm
11511 ?        00:00:00 gnome-volume-ma
11514 ?        00:00:00 nm-applet
11525 ?        00:00:00 trashapplet
11527 ?        00:00:00 gnome-cups-icon
11529 ?        00:00:00 mixer_applet2
11532 ?        00:00:00 evolution-excha
11533 ?        00:00:00 gnome-power-man
11554 ?        00:00:00 mapping-daemon
11565 ?        00:00:00 gksu
11701 ?        00:00:00 gnome-screensav
11758 ?        00:00:16 firefox-bin
11922 ?        00:00:01 gnome-terminal
11925 ?        00:00:00 gnome-pty-helpe
11926 pts/0    00:00:00 bash
11975 pts/0    00:00:00 ps

The connections are incoming, btw. All via BitTorrent on port 6881. All different people/IP Addresses.

---

### Post by shof2k on 2007-06-11
If it's not under your userid then it must be running as another userid or root.  Can you type: ```
 sudo netstat -anp >> netstat.txt 
``` and attach the resulting netstat.txt file from your home folder?

Peace

---

### Post by Songwind on 2007-06-11
Sounds like a tracker didn't take you off the list of peers when you disconnected from something last time and now people are erroneously trying to connect to your system to share files.

---

