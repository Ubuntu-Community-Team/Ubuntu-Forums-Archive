---
title: "Connection to the internet in kubuntu."
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Rabindranath on 2007-06-24
I have installed kubuntu on my computer and I cannot find out how to connect to the internet in kubuntu. I have a dialup connection to the internet and I have drivers for my modem. When i try to connect using kppp, it says "cannot find /dev/modem1/ "  etc. I have the drivers for linux 7, linux 8, linux 9. Are they suitable for kubuntu?
If not how do connect to the internet.I am attaching the driver files for linux 9.


Thanks in advance for your reply.

---

### Post by Dedoimedo on 2007-06-24
Hello,
Dial-up connection - 56K or a dialer for ethernet / dsl / adsl?
What protocol are you using to connect (PPP, PPTP, L2TP)?
Dedoimedo

---

### Post by kevdog on 2007-06-24
What kind of modem do you have???

---

### Post by Rabindranath on 2007-06-24
I have a dial up connection using a 56k krypton modem and I think I am using PPP but I am not sure.

---

### Post by Rabindranath on 2007-06-24
I used a dialer in windows XP and I just entered the phone number to dial, username and password. Nothing else. KPPP was not able to find /dev/modem/. By the way how do I find the installed devices in kubuntu?

---

### Post by kevdog on 2007-06-24
Installed by LinModem in Ubuntu along time ago.  Please go through this link first:
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Make sure to first install and run the scanModem tool.

---

### Post by Rabindranath on 2007-06-24
Ok thanks. I found only .tar packages. I dont know how to compile those packages. Is there a .deb package of scanmodem tool.

---

### Post by kevdog on 2007-06-24
tar files --

"Unzip" tar files
tar -zxvf *****.tar.gz

If no gz

tar -xvf ****.tar

Go into untarred directory.  
If need to compile make sure you have build-essential package installed:
sudo aptitude installed build-essentials

Then in directory
make
sudo make install

Thats it -- sorry it cant be more complicated

---

### Post by Rabindranath on 2007-06-24
I have done what you said. I have attached the output.

---

### Post by Rabindranath on 2007-06-24
Can someone tell me what to do next. I have  a HSP56 Micro modem driver in windows. Is there a driver for linux?

---

### Post by Rabindranath on 2007-06-24
Sorry, the files are the one I am attaching now. Please help me.

---

