---
title: "[SOLVED] Trouble - Gutsy not syncing to time servers"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-11-19
i know there are several post of it here, but none helped me.

can someone please tell me what I have to type in to get a report of my system, so to see what could be wrong with time sync.

thanks

---

### Post by PointyWombat on 2007-11-20
Do you have NTP installed? What does "ntpq -p" produce?

---

### Post by MozartlovesUbun2 on 2007-11-20
> **PointyWombat said:**
> Do you have NTP installed? What does "ntpq -p" produce?

$ ntpq -p
No association ID's returned
======================

"ntpq -p" or "ntpq" in synaptics brings no results

how do i install it?

---

### Post by asmiller-ke6seh on 2007-11-20
> **MozartlovesUbun2 said:**
> $ ntpq -p
No association ID's returned
======================

"ntpq -p" or "ntpq" in synaptics brings no results

how do i install it?

You might want to try searching SYNAPTICS for "NTP" without the "Q".

---

### Post by PointyWombat on 2007-11-20
You can right-click on the date-time button on the desktop and select 'adjust date & time'. From there select 'keep synchronized with internet server' under configuration. If NTP is not installed, it will automatically prompt you to install it. After that, just select an NTP server close to you location wise. Once that's done, 'ntpq -p' should show you information about how your synchronized.

---

### Post by MozartlovesUbun2 on 2007-11-20
> **PointyWombat said:**
> You can right-click on the date-time button on the desktop and select 'adjust date & time'. From there select 'keep synchronized with internet server' under configuration. If NTP is not installed, it will automatically prompt you to install it. After that, just select an NTP server close to you location wise. Once that's done, 'ntpq -p' should show you information about how your synchronized.

yes i did all that before posting here, it did ask  me to install it and i typed my password and all that

but the sync still does not work

what should i do?

==============

ntpq -p
No association ID's returned

---

### Post by MozartlovesUbun2 on 2007-11-20
> **asmiller-ke6seh said:**
> You might want to try searching SYNAPTICS for "NTP" without the "Q".

ok "NTP" brings like a hundred results in synaptics, um which one do i choose?

hmm, seems i have the NTP installed, do i need anything else?

---

### Post by PointyWombat on 2007-11-20
please show the output of the following:

grep server /etc/ntp.conf
and
ps -ef | grep ntp

---

### Post by MozartlovesUbun2 on 2007-11-20
> **PointyWombat said:**
> please show the output of the following:

grep server /etc/ntp.conf
and
ps -ef | grep ntp

mozart@network:~$ grep server /etc/ntp.conf
# You do need to talk to an NTP server or two (or three).
# Local users may interrogate the ntp server more closely.
mozart@network:~$ ps -ef | grep ntp
ntp      14482     1  0 19:15 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 109:120 -g
mozart   15407 15382  0 19:30 pts/0    00:00:00 grep ntp
mozart@network:~$ 

thanks for you help :)

i am in montreal, so it should be the canadian atlantic time, but it always shows me wrong, even the date was wrong, so i went in and changed manually, now i ve set it to toronto but that still didnt help

---

### Post by PointyWombat on 2007-11-20
Ok, so NTP is installed and running, but not configured.

When you go into 'Time and Date Settings" (System->Admin->Time and Date):

Is your timezone set to America/Montreal?
What does it say for Configuration?
Under Time servers, if you hit Select Servers, is anything checked?

---

### Post by MozartlovesUbun2 on 2007-11-20
> **PointyWombat said:**
> Ok, so NTP is installed and running, but not configured.

When you go into 'Time and Date Settings" (System->Admin->Time and Date):

Is your timezone set to America/Montreal?
What does it say for Configuration?
Under Time servers, if you hit Select Servers, is anything checked?

hi ya
ok, well i went in through (System->Admin->Time and Date) this time and it was different from when i 
right click on the clock and choose the same place in that your method showed up with no server selected, but going to same place as i was usually selecting shows up with the top server checked marked???? (is this a bug?)

anyway i did it now your way and checked boxed it

hmm, but it didnt sync, my montreal ubuntu laptop clock is running an hour faster!  (but usually the clock gets even worse when i shut down and boot up, today it showed me that it was still yesterday)

booting in windows, time is ok

---

### Post by PointyWombat on 2007-11-20
Does "ntpq -p" now show anything?

---

### Post by MozartlovesUbun2 on 2007-11-20
> **PointyWombat said:**
> Does "ntpq -p" now show anything?

same

ntpq -p
No association ID's returned
mozart@network:~$ 

i also tried it with sudo su

---

### Post by PointyWombat on 2007-11-20
Hmm.. Let's restart NTP:
sudo /etc/init.d/ntp restart

Any errors?

Also, lets see if there's anything listed for server in the ntp.conf file:
grep server /etc/ntp.conf

---

### Post by MozartlovesUbun2 on 2007-11-20
> **PointyWombat said:**
> Hmm.. Let's restart NTP:
sudo /etc/init.d/ntp restart

Any errors?

Also, lets see if there's anything listed for server in the ntp.conf file:
grep server /etc/ntp.conf

mozart@network:~$ sudo /etc/init.d/ntp restart
[sudo] password for mozart:
 * Stopping NTP server ntpd                                              [ OK ] 
 * Starting NTP server ntpd                                              [ OK ] 
mozart@network:~$ grep server /etc/ntp.conf
# You do need to talk to an NTP server or two (or three).
# Local users may interrogate the ntp server more closely.
server time.nrc.ca
mozart@network:~$

---

### Post by PointyWombat on 2007-11-20
Does "ntpq -p" show anything now?

---

### Post by MozartlovesUbun2 on 2007-11-20
> **PointyWombat said:**
> Does "ntpq -p" show anything now?

yes thank you :)

mozart@network:~$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 time.nrc.ca     .INIT.          16 u    -   64    0    0.000    0.000   0.000
mozart@network:~$ 

---------------------
hmm but it still is running an hour ahead
i'll go manually reset it

---

### Post by MozartlovesUbun2 on 2007-11-20
**cool ok it worked**

yup that did it it actually synced for the first time, hmm strange so i had to stop and restart, was that it?

thank you

---

### Post by PointyWombat on 2007-11-20
ok. good news. I don't know why it didn't restart NTP when using the GUI. I thought that it would have..either way.. glad to see its working.

---

### Post by MozartlovesUbun2 on 2007-11-20
> **PointyWombat said:**
> ok. good news. I don't know why it didn't restart NTP when using the GUI. I thought that it would have..either way.. glad to see its working.

[http://perkypants.org/blog/2007/11/21/quelle-surprise/](http://perkypants.org/blog/2007/11/21/quelle-surprise/)

[http://www.gnome.org/~federico/news-2007-11.html#20](http://www.gnome.org/~federico/news-2007-11.html#20)

 Distros waste a lot of time reimplementing each other's features, and later trying to merge everything together in a public project like GNOME.

Novell implemented intlclock.

Later, Fedora imported it, made their own packaging changes, and added some cool features.

Later, Ubuntu imported it and made their own packaging changes.

**Meanwhile, gnome-panel's clock diverged on its own. Now we have four clocks which must be merged by hand.**

---

### Post by MozartlovesUbun2 on 2007-12-08
**Had some problems again on a fresh install**

mozart@network:~$ ps -ef | grep ntp
ntp       5353     1  0 Dec07 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -u 109:120 -g
mozart    7215  7196  0 02:28 pts/0    00:00:00 grep ntp
mozart@network:~$ sudo /etc/init.d/ntp restart
[sudo] password for mozart:
 * Stopping NTP server ntpd                                              [ OK ] 
 * Starting NTP server ntpd                                              [ OK ] 
mozart@network:~$ grep server /etc/ntp.conf
# You do need to talk to an NTP server or two (or three).
server ntp.ubuntu.com 
# Local users may interrogate the ntp server more closely.
server time.nrc.ca
server ntp.univ-lyon1.fr
server swisstime.ethz.ch
mozart@network:~$ ntpq -p
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 europium.canoni 193.79.237.14    2 u    8   64    3  101.615  26124.3   4.600
 time.nrc.ca     132.246.168.2    2 u   12   64    3   34.178  26125.4   3.210
 dns.univ-lyon1. 195.220.94.163   2 u   11   64    3  126.676  26125.4   5.472
 swisstime.ee.et 129.132.2.22     2 u   15   64    3  123.101  26123.5   3.774
mozart@network:~$

---

