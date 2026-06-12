---
title: "Broadcom Wireless"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by chirulais on 2008-01-22
well, ive switched to ubuntu like 10 times but i keep going back to vista because of the wireless, i did the ndiswrapper thing and actually i could conect (near to my router) but when im in my room i just cant connect (i have lke 10% of signal strenght both in vista and ubuntu) but in vista im able to conect and it is not slow. then i got my gutsy cd in mail i installed and found out my wifi broadcom card was in the restricted manager driver thing an used that but i did not work again when im far from my router.
any help us going to be apreciated, thanks.
and i hope that when i learn more about linux i can help out, just like you do. =D
Sorry for my weak english (im mexican)

im runing gutsy in a dell inspiron 1501 with 512mb ram and a amd mobile sempron =D

---

### Post by Bubba64 on 2008-01-22
On my wireless router which is a personal not a community I can lower or increase the signal strength.

---

### Post by emarkd on 2008-01-22
Depends on your router.  There are several firmware upgrades for routers that will allow you to do this.  Check out:

[http://www.dd-wrt.com/dd-wrtv2/index.php](http://www.dd-wrt.com/dd-wrtv2/index.php)

or

[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)  <-- My favorite

Both of these allow you to adjust the power output of the wireless.

---

### Post by emicsun on 2008-01-22
Have you tried to play with the command iwconfig?

Just type iwconfig and it will give you a report on the status, see example below:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"brb-deck2"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.417 GHz  Access Point: 00:11:50:AE:C9:F8   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=76/100  Signal level=-49 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Then through this you can change various settings for your wireless interface, like sensitivity and power.

Cheers,

Michael

---

### Post by chirulais on 2008-01-22
hey thank you for your help, but my problem isnt the router i think it is ubuntu, because in this laptop i have both vista and gutsy and when im in vista and im far from the router im able to conect, but no in ubuntu.:confused:
Thankyou

---

### Post by rosegarden78 on 2008-01-22
I'm on an Inspiron 1200 with an older card bcm43xx I didn't get the exact model number but you should try the following packages ndiswrapper never got my dell card working

fw-cutter
bcm43xx

If it still doesn't work try typing at the terminal: sudo modprobe bcm43xx

---

### Post by chirulais on 2008-01-22
already tried that, and my chip does work but only near the router u_U

---

