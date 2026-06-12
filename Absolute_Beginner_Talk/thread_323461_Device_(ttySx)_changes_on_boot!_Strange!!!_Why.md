---
title: "Device (ttySx) changes on boot! Strange!!! Why?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by Carlos Santiago on 2006-12-22
Hi. I have a PCMCIA modem (Novatel Merlin UMTS Modem U630) and I am running Ubuntu 6.06 on my laptop, an Acer Travelmate 4150.

When I switch on my laptop, the serial device that identifies the modem can be either /dev/ttyS0 or /dev/ttyS4.

If the device matches the indicated on the configuration files, everything works just fine.

If not, I have to change the config files manually and start the connection also manually.

Can anyone plz tell me how can I force my modem to have always the same ttyS?

Thx

---

### Post by Carlos Santiago on 2006-12-22
I have search a lot for solutions this problem. 

Can anyone plz help me?

---

### Post by Carlos Santiago on 2007-03-01
The solution is to use a UDEV rule.

For example writing the file /etc/udev/rules.d/99-modem3g.rules with the text

ACTION=="add", KERNEL=="ttyS[0-4]", NAME+="modem3g"

Then the modem will be /dev/modem3g

---

