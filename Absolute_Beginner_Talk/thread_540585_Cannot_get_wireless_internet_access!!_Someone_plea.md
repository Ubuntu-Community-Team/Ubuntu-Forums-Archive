---
title: "Cannot get wireless internet access!! Someone please help"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by XHR_IS_THE_NEW_BLACK on 2007-09-01
Good day ladies and gents.  Obviously I am a new Xubuntu user and have figured most things out except for one of the most important things, connecting to the internet via my wireless lan.  I'm trying to connect my laptop...DELL inspiron..with a broardcom 4318 wireless lan controller.  My wireless card has no native linux drivers but I have had sucess using ndiswrapper and the right windows driver for the card.  When I go to configure my settings to connect to my access point...a windows vista machine...i know it's shameful...my parents machine...I can type my essid, there is no current WEP key, and it is set to dhcp, and save the settings.  But I cant seem to get online.  The output of iwconfig is

 eth1   

IEEE 802.11/g ESSID: "J" Nickname: "Broadcom 4318"
Mode:  Managed   Acess Point: Invalid    
RTS thr: off    Fragment thr: off  
Link Quality=0/100 Signal Level = -256dBm   Noise Level = 256dBm
Rx invalid rwid: 0 Invalid Crypt: 0 Rx invalid frag:0
Tx excessive retried:0   Invalid misc: 0 Missed beacon: 0

I'd assume all the error messages that have zero's after them mean that they're false and there are no errors.  But then again I'm totally clueless.  I am in good range to reach my wireless signal so I know that's not an issue.  Please someone help me!!  Thanks!!

---

### Post by Kolfinna on 2007-09-01
Post the output of iwlist eth1 power and iwlist eth1 txpower.

Also, do you have something like Kwifimanager?

---

### Post by XHR_IS_THE_NEW_BLACK on 2007-09-01
First off, thanks for your reply..much appreciated...the output of 
iwlist eth1 power is simply eth1....I attempted sudo iwlist eth1 scan and scanning but got an error message saying Interface doesn't support scanning:  No such device....Please any help would be awesome...Thanks again..:confused:

---

### Post by Kolfinna on 2007-09-01
Typically, eth1 is a hardwired ethernet connection... post the full ifconfig, please.

---

### Post by anewguy on 2007-09-01
The Broadcom series normally don't run out of the box in Linux.  Please see this link and look at the section on getting wireless working.  It should solve your problem.:)


[http://ubuntuforums.org/showthread.php?t=507505]("http://ubuntuforums.org/showthread.php?t=507505")

---

### Post by Kolfinna on 2007-09-01
I've got a Broadcom card too... actually just got mine up and running.

---

### Post by brn on 2007-09-01
I still carry the scars of a three month battle with the Broadcom interface and am no less ignorant now than when I began.  That said, there are some excellent HOW-TO's in the forums that involve installing either fw-cutter or ndiswrapper.  Among them:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
[*][http://ubuntuforums.org/showthread.php?t=391961&highlight=Presario](http://ubuntuforums.org/showthread.php?t=391961&highlight=Presario)
[*][https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
[*][https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))
[/LIST]
...And many more...

What finally got me running was **wifi-radar**.  I suggest trying this before doing anything that changes your system configuration (Install with Synaptic Package Manager) .  If it still doesn't work, I would first try fw-cutter (didn't work for me) then ndiswrapper (which did but only after applying wifi-radar).  -- Good Luck--

---

