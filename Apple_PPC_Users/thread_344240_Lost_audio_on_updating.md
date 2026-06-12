---
title: "Lost audio on updating"
date: 2007-01-22
forum: Apple PPC Users
---

### Post by grazie on 2007-01-22
Used System Update Manager to pick up grades a few days ago and lost audio on completion. The upgrades picked up are as follows

2007-01-17 22:34:54 upgrade tzdata 2006m-1ubuntu1 2006p-0ubuntu6.10
2007-01-17 22:34:55 upgrade libkrb53 1.4.3-9ubuntu1 1.4.3-9ubuntu1.1
2007-01-17 22:34:55 upgrade w3m 0.5.1-4ubuntu2 0.5.1-4ubuntu2.6.10
2007-01-17 22:34:56 upgrade libavahi-common-data 0.6.13-2ubuntu2.3 0.6.13-2ubuntu2.4
2007-01-17 22:34:56 upgrade libavahi-common3 0.6.13-2ubuntu2.3 0.6.13-2ubuntu2.4
2007-01-17 22:34:56 upgrade libavahi-core4 0.6.13-2ubuntu2.3 0.6.13-2ubuntu2.4
2007-01-17 22:34:56 upgrade libdbus-1-3 0.93-0ubuntu3 0.93-0ubuntu3.1
2007-01-17 22:34:56 upgrade dbus 0.93-0ubuntu3 0.93-0ubuntu3.1
2007-01-17 22:34:56 upgrade avahi-daemon 0.6.13-2ubuntu2.3 0.6.13-2ubuntu2.4
2007-01-17 22:34:57 upgrade dbus-1-utils 0.93-0ubuntu3 0.93-0ubuntu3.1
2007-01-17 22:34:57 upgrade libnspr4 2:1.firefox2.0+0dfsg-0ubuntu3 2:1.firefox2.0.0.1+0dfsg-0ubuntu0.6.10
2007-01-17 22:34:57 upgrade libnss3 2:1.firefox2.0+0dfsg-0ubuntu3 2:1.firefox2.0.0.1+0dfsg-0ubuntu0.6.10
2007-01-17 22:34:57 upgrade firefox 2.0+0dfsg-0ubuntu3 2.0.0.1+0dfsg-0ubuntu0.6.10
2007-01-17 22:35:00 upgrade libavahi-client3 0.6.13-2ubuntu2.3 0.6.13-2ubuntu2.4
2007-01-17 22:35:00 upgrade libavahi-glib1 0.6.13-2ubuntu2.3 0.6.13-2ubuntu2.4
2007-01-17 22:35:01 upgrade libgtop2-common 2.14.4-0ubuntu1 2.14.4-0ubuntu1.1
2007-01-17 22:35:01 upgrade libgtop2-7 2.14.4-0ubuntu1 2.14.4-0ubuntu1.1
2007-01-17 22:35:01 upgrade linux-restricted-modules-common 2.6.17.6-1 2.6.17.7-10.1
2007-01-17 22:35:01 upgrade linux-restricted-modules-2.6.17-10-powerpc 2.6.17.6-1 2.6.17.7-10.1
2007-01-17 22:35:02 upgrade mozilla-thunderbird 1.5.0.8-0ubuntu0.6.10 1.5.0.9-0ubuntu0.6.10
2007-01-17 22:35:05 upgrade xserver-xorg-core 1:1.1.1-0ubuntu12 1:1.1.1-0ubuntu12.1

Anyone got any ideas or had a similar problem?

The machine is running Edgy on a G4 with an added SB sound card. Worked fine before the update. Also still works fine with Edgy and Feisty Live CDs.

---

### Post by irw on 2007-01-22
Yes, I also lost sound, and despite fiddling with any option I can think off / re-installing codecs, etc, I am still lacking sound.

---

### Post by grazie on 2007-01-23
irw,

Did you lose sound on an update? Do you know exactly what the updates were?
You could use 'sudo cat /var/log/dpkg.log | grep upgrade' to determine your upgrades and then filter by date/time.

---

### Post by grazie on 2007-01-26
I've submitted [Bug #81626]("https://launchpad.net/ubuntu/+bug/81626").

---

### Post by Banjaxala on 2007-02-06
I lost on audio around the time of some updates--in the same session as when I downloaded the external codecs for Xine.

```
2007-02-02 08:08:43 upgrade libgtk2.0-common 2.8.20-0ubuntu1 2.8.20-0ubuntu1.1
2007-02-02 08:08:46 upgrade libgtk2.0-bin 2.8.20-0ubuntu1 2.8.20-0ubuntu1.1
2007-02-02 08:08:47 upgrade libgtk2.0-0 2.8.20-0ubuntu1 2.8.20-0ubuntu1.1
2007-02-02 08:08:48 upgrade gtk2-engines-pixbuf 2.8.20-0ubuntu1 2.8.20-0ubuntu1.1
2007-02-03 08:05:49 upgrade libc6 2.3.6-0ubuntu20.2 2.3.6-0ubuntu20.4
2007-02-03 08:06:03 upgrade app-install-data-commercial 5 5.3
2007-02-03 08:06:04 upgrade synaptic 0.57.8ubuntu11 0.57.8ubuntu13

```

that's all I get from my log file. my machine's a Powerbook G4 titanium, vintage '01.

---

### Post by grazie on 2007-02-06
Your problem appears to be codec related. The cause and solution to my problem is detailed in the bug report.

---

