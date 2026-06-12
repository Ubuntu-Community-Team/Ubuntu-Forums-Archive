---
title: "Problems Connecting"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by SueD on 2006-07-30
Hi All. I installed Ubuntu yesterday and thought everything went well...that is until I tried to connect. I hope the following information will shed some light...

1) System Specifications:
Monitor: CRT
Ram Amount:448MB (DDR SDRAM)
HD: IDE/SATA/Scsi HD#1-IDE WinXP...HD#2-IDE Ubuntu
Onboard or Discreet Graphics Card: SiS
CPU: Intel Celeron 2.2MHz
MainBoard: Intel???
Modem / Eth / Wifi brand:SiS 900-Based PCI Fast Ethernet Adapter  
Adapter cards you have installed:Network Adapter WAN (PPP/SLIP) Interface  
2) Version of Ubuntu your using: Ubuntu 6.06
3) Any error or output codes you receive durring the install or after
localhost pppd [5054]:PAP authentication failed
localhost pppd [5054]:Connection terminated
localhost pppd [5332]:Plugin rp-pppoe.so loaded
localhost pppd [5334]: pppd 2.4.4b1 started by root, uid 0
localhost pppd [5334]:PPP session is 41261
localhost pppd [5334]:Using interface ppp0
localhost pppd [5334]:Connect: ppp0 <-->eth0
localhost pppd [5334]:Remote message: Authentactaion failed
localhost pppd [5334]:PAP authentication failed
localhost pppd [5334]:Connection terminated

I'm so frustrated and don't know where to go from here. I tried everything posted [**here**]("https://help.ubuntu.com/community/ADSLPPPoE") and still nothing. Please point me in the right direction. Oh, and although my understanding is not too bad, I lack technical knowledge so the more basic the instructions, the better. Thanks.

---

### Post by Apple 101 on 2006-07-31
Are you attempting to connect via xDSL, WLAN, or dial-up?

---

### Post by SueD on 2006-07-31
I got rid of dial up and have been using a D-Link DSL-300G ADSL modem for over a year without any problems. Is that what you're asking?

---

### Post by confused57 on 2006-07-31
The last reply in this thread mentioned a website for DSL support:

[http://www.ubuntuforums.org/showthread.php?t=226142](http://www.ubuntuforums.org/showthread.php?t=226142)

There is a SiS900 Linux driver, but Dapper automatically recognized my SiS integrated network controller...don't think that's your problem though.

---

### Post by SueD on 2006-07-31
Thanks. I already saw that this morning and I'm not sure but I don't think that's my problem. If it is, I don't understand how to fix it.

---

### Post by MaximB on 2006-07-31
type in the terminal
sudo pppoe

---

### Post by SueD on 2006-07-31
"sudo: pppoe: command not found."

Next?

---

### Post by NewbieNik on 2006-07-31
take the : out of the command,so it reads

sudo pppoe

---

### Post by SueD on 2006-07-31
I had no colon...when I typed in sudo pppoe, the response I got was sudo: pppoe: command not found

---

### Post by SueD on 2006-08-01
So there's no solution?

---

### Post by confused57 on 2006-08-01
I'm not familiar with DSL, but PAP authentication failure possibly has something to do with your ISP username & password not being recognized...I'm sure you already knew that, but just in case.  Wish I could help you more.

---

### Post by SueD on 2006-08-01
Thanks anyways.

---

### Post by SueD on 2006-08-01
I got it working! It was the stupidest thing...when I was in sudo pppoeconf and it asked for my name, I didn't delete that part BEFORE inputting my name. What a duh!LOL

---

### Post by civetta on 2006-08-01
> **NewbieNik said:**
> take the : out of the command,so it reads

sudo pppoe

Do you mean sudo pppoeconf? Bash doesn't recognize sudo pppoe for me either.

---

