---
title: "[SOLVED] Help needed with Dial-Up connections"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-08-04
Hi all,
I just changed from Libranet to Ubuntu 6.06 and I have big time trouble to set up my Dial-Up Internet connection. I have a Gnet 56k Modem (MD0321), Internal PCI, with the Topic chipset. This Modem works with Fedora Core 5, with Libranet 3.0 and with Windows XP just fine. How come that I'm not able to set-up this for Ubuntu. I found it listed in the SYSTEM MANAGER where it tells me that the vendor is Topic. And it is also shown in >SYSTEM>ADMINISTRATION>NETWORKING together with eth0 and eth1. I can activate it. I configured it with 'sudo pppconfig' and I still can not connect. I'm in trouble:!: ....I need help:?: ...
Juergen

---

### Post by deadgobby on 2006-08-04
[https://help.ubuntu.com/community/DialupModemHowto?highlight=%28modem%29](https://help.ubuntu.com/community/DialupModemHowto?highlight=%28modem%29)

---

### Post by Cariboo1938 on 2006-08-04
> **deadgobby said:**
> [https://help.ubuntu.com/community/DialupModemHowto?highlight=%28modem%29](https://help.ubuntu.com/community/DialupModemHowto?highlight=%28modem%29)
Thank you for this information. My modem is a hardware modem which does NOT
connect to a serial port but is in a PCI slot. So all the guidelines are not applicable to my situation. How would I find the right device name?

---

### Post by avtolle on 2006-08-04
Get to a terminal , e.g., Applications->Terminal, type in "lspci" (without the ""), and see what it reports.

---

### Post by Cariboo1938 on 2006-08-04
> **avtolle said:**
> Get to a terminal , e.g., Applications->Terminal, type in "lspci" (without the ""), and see what it reports.
Thank you avtolle! here is the line, when I listed with "lspci":
 
[COLOR="Red"]000:02:07.0 Communication controller: TOPIC SEMICONDUCTOR Corp TP560 Data/Fax/Voice 56k modem[/COLOR]


This is the modem I installed. What would be the port address? what is the device name in this case?
Regards
Juergen

---

### Post by Cariboo1938 on 2006-08-05
Hello avtolle, I did as you recommneded and I got the information that Ubunu detected my hardware modem correctly. Here is what "lspci" listed:
000:02:07.0 Communication controller: TOPIC SEMICONDUCTOR Corp TP560 Data/Fax/Voice 56k modem
I did sudo 'pppconfig' and I tried to activate the modem at >NETWORKING.
I'm still not able to connect. What on earth is wrong with Ubuntu?:-k 
Any thoughts?
Juergen

---

### Post by Cariboo1938 on 2006-08-05
Problem solved! I followed the instructions for hardware modems in the DialupModemHowto ([https://help.ubuntu.com/community/DialupModemHowto)](https://help.ubuntu.com/community/DialupModemHowto)). The main issue was to find the right name for the modem port. The command "sudo wvdialconf /etc/wvdial.conf" scans all ports for the modem. In my case was the result : 'Found a modem on /dev/ttyS4'. ttyS4 is information needed when the connection is set up with "sudo pppconfig".
It took me nearly 2 days to get this...but now it works great..Thank you all for your inputs, and special thanks for the very detailed instruction sin the DialupModemHowto.
Juergen:-({|=

---

