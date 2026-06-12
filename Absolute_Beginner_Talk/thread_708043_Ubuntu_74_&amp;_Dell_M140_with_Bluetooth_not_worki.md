---
title: "Ubuntu 74 &amp; Dell M140 with Bluetooth not working..."
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by dernwine on 2008-02-25
Hi all.
Have done a fair amount of thread searching and cant resolve this problem. 
I have a Dell XPS M140 running 7.04.

dmesg shows:

root@harpo:/home/xxxxxxx# dmesg | grep -i blue
[   32.668000] Bluetooth: Core ver  2.11
[   32.668000] Bluetooth: HCI device and connection manager initialized
[   32.668000] Bluetooth: HCI socket layer initialized
[   32.756000] Bluetooth: L2CAP ver 2.8
[   32.756000] Bluetooth: L2CAP socket layer initialized
[   32.820000] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   33.872000] Bluetooth: RFCOMM socket layer initialized
[   33.872000] Bluetooth: RFCOMM TTY layer initialized
[   33.872000] Bluetooth: RFCOMM ver 1.8


 ps -ef | grep hidd
root      5872     1  0 22:34 ?        00:00:00 /usr/bin/hidd --master --server
root      6173  5805  0 22:44 pts/0    00:00:00 grep hidd

ps -ef | grep hci
root      5870     1  0 22:34 ?        00:00:00 /usr/sbin/hcid -x -s
root      6179  5805  0 22:45 pts/0    00:00:00 grep hci

 lsmod | grep -i blue
bluetooth              55908  5 rfcomm,hidp,l2cap

When I do a hcitool --scan:

 hcitool scan
Device is not available: No such device

hidd --search shows:

 hidd --search
Searching ...

wifi LED light lights up sometimes, and the bluetooth LED never lights up, but that doesn't seem to mean much as wifi works just fine without the LED being illuminated.
I HAVE tried running: /etc/init.d/bluetooth restart several times as well to no avail.

I have a Audiovox 5600 phone with bluetooth in pairing mode, but it doesn't look like Ubuntu realizes it has a bluetooth device available. 

Any help appreciated, this is driving me nuts.

Thanks in advance!

---

### Post by gohanssjn on 2008-02-26
Do you only have Ubuntu?

My XPS M1210 needs Bluetooth uninstalled in Vista to see it in Ubuntu.  Weird little glitch...

---

### Post by dernwine on 2008-02-26
gohanssjn,

Yes, I only have Ubuntu installed, not dual booting. Although I've been thinking of installing VMWare and installing XP to see if I get same results. Not sure if bluetooth plays nice with VMWare or not though...

---

