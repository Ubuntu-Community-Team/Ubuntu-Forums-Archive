---
title: "Cant get my wireless into monitor mode"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by aLsanomo on 2008-04-07
For testing purposes, Ive been trying to use aircrack testing it with my own conection. The problem is that I cant get in going.

My connection works superb. I used ndiswrapper to install my wireless adapter.

When I get to the next command I get the next response:

root@ubuntu:~# iwconfig wlan0 mode Monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

the iwconfig gives me this:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Sitecom"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:F6:3E:87:CE   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key: 0970-1828-1282-1828-.......
          Security mode:restricted
          Power Management:off
          Link Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any ideas how to evade "SET Failed on device wlan0; invalid argument" ?

Any help will be appreciate it.

Thanks in advanced

---

### Post by marufaberlin on 2008-04-07
I got the same problem :-(

---

### Post by plucky on 2008-04-07
Try this [link](http://ubuntuforums.org/showthread.php?t=514723) for an aircrack tutorial.

This tells you how to set up your card for monitor mode.


Good Luck
:)

---

### Post by wieman01 on 2008-04-07
You cannot put a device in monitor mode that was installed using 'ndiswrapper', it's as simple as this. What adapter have you got by the way?

---

### Post by aLsanomo on 2008-04-09
I have a Broadcom 802.11b/g WLAN, 6TO4 Adapter

---

### Post by wieman01 on 2008-04-09
Check this out:

[http://www.aircrack-ng.org/doku.php?id=broadcom]("http://www.aircrack-ng.org/doku.php?id=broadcom")

---

### Post by Clayton_Rodrigues on 2008-04-09
I got a DELL 1395 802.11G,In. and i am running it under ndiswrapper. any idea how can i set up it to the monitor mode ?

---

### Post by wieman01 on 2008-04-10
Again, with 'ndiswrapper' you can't.

---

### Post by BombDiggity on 2008-04-10
Unfortunately broadcom isn't a supported card type for monitor mode.  anything with an intel or atheos chipset however is.  sorry dude

---

### Post by wieman01 on 2008-04-10
Ralink is also a good choice.

---

### Post by aLsanomo on 2008-04-20
> **BombDiggity said:**
> Unfortunately broadcom isn't a supported card type for monitor mode.  anything with an intel or atheos chipset however is.  sorry dude

Thank you and sorry that i haven't been around lately. i was out of town.

I was afraid that Broadcom cards didn't support monitor mode... and in fact, they don't.

Thank you everybody for your help.

---

