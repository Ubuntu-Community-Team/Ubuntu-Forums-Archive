---
title: "56k Modem volume off"
date: 2005-10-01
forum: Absolute Beginner Talk
---

### Post by dalani on 2005-10-01
In the modem monitor applet properties, there is a setting to turn off the volume on a dial up modem. However whenever I connect, my  modem dials-up with the annoying volume on. The 'volume off' setting in the applet doesn't seem to take effect. 
Is there a way of getting my modem to connect silently???

---

### Post by blastus on 2005-10-01
I've had a modem even do that on Windows and that modem was VERY loud. The modem simply ignored the volume setting and it could not be turned off. The "fix" I found was to find an old ear phone, cut the wire and plug it into the jack on the modem (if your modem has one.) Worked like a charm. :cool:

---

### Post by nitricacid on 2005-10-01
Could always open the computer pull out the modem and rip off the mini speaker that is on the modem board then place it back into the mother board and dial up.



Just ignore this post, i was board and wanted to be ignorant.

---

### Post by dalani on 2005-10-08
Put away your pliers I solved it this way:

I found Ubuntu's dial-up config file
/etc/chatscripts/ppp0

used vim text editor 
#sudo vim /etc/chatscripts/ppp0

then add M0L0 in the line containing > ATDT phone# 
so that it reads: > ATM0L0DT phone# 
these are zeros in M0L0.
thanks to Nerderello at Linuxforums.org for the modem silence code.

(VIM basics: press insert,edit text, press esc,then type :write to save file
then press esc and :q to quit VIM)

-----------------------------------
For the record, I am somewhat disappointed one would have to go through such antics to solve something  trivial  like that. ModemMonitor gui interface has a setting to silence the modem but to no effect. Luckily I've had worse distros which is why I know Vim and the linux filesystem.

---

### Post by arvana on 2008-01-10
Thanks, dalani -- works like a charm!

I personally set it to ATM1L0DT to get some feedback of it connecting, without it blaring through my speakers as well.

---

