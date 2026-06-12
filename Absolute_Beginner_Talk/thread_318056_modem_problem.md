---
title: "modem problem"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by helix24 on 2006-12-13
hi
i recently installed Ubuntu linux 6.10
im having problem with connecting internet with my modems.
i have a US.Robotics 56k voice internal PCI and a Motorola SM56 PCI Fax Modem 56k. I have never used any Linux before, so im unsure how to configure the modem or even check if it is installed. 

i do get a default modem connection in the Network settings, and i entered my ISP information but nothing happenes when i enable it.

am i doing anything wrong or are those modems not supported?
and where can i get a list of supported 56k modems on Ubuntu?

---

### Post by els on 2006-12-13
I'm new to Linux as well so take my advice with a grain of salt, but I know that there are some modems (known as Winmodems) that aren't supported.  Sorry I can't be much more help, but here are a few links that may get you going in the right direction:

[http://start.at/modem](http://start.at/modem)
[http://www.motorola.com/softmodem/driver.htm](http://www.motorola.com/softmodem/driver.htm)

I'd also recommend hitting Google armed with the following keywords: "Winmodem", "Linux driver (modem model)" ..etc  This issue seems fairly well documented so you shouldn't have too much trouble figuring it out.

Hope this helps.

---

### Post by chinocracy on 2006-12-14
I myself have problems going online at home since I don't have the modem driver for my Ubuntu box. I have my system on dual boot with Win XP Prof. My modem is a Conexant-based E-maxx internal modem, and my older D-link DFM562IS (which I thought was not working before) is on standby. I'll try out the solutions that I found on the Net, but if anyone else has some helpful info, please chip in. Thanks.

Chino

---

### Post by housam on 2006-12-14
Welcom to ubuntu, You can read [this link ]("https://help.ubuntu.com/community/DialupModemHowto")

---

### Post by chinocracy on 2006-12-14
Housam, thanks for reminding me of it.

---

### Post by unisol on 2006-12-14
i believe the us robitics modem is on port ttyS14 load your modem using modem applet. or run sudo wvdialconf/etc/wvdial.conf it should tell you what port your modem is located on.

---

