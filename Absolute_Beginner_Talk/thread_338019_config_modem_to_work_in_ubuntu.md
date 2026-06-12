---
title: "config modem to work in ubuntu"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by micro_xii on 2007-01-13
Greetings

I have ubuntu 6

I have dual boot, xp and ubuntu. I have dial up connection. My Modem works perfectly if I run xp. NOw when I boot to my ubuntu and try to connect to internet, the ubuntu did not detect my modem. I believe my Modem is conexant.

How to configure my modem in ubuntu...thanks:mrgreen:

---

### Post by mikewhatever on 2007-01-14
And greetings to you too.
Hope this will get you started: [https://help.ubuntu.com/community/DialupModemHowto/Conexant?highlight=%28conexant%29](https://help.ubuntu.com/community/DialupModemHowto/Conexant?highlight=%28conexant%29)

By the way, do you have Ubuntu 6.06 or Ubuntu 6.10. They are not the same.

---

### Post by housam on 2007-01-14
Download the [scanModem]("http://132.68.73.235/linmodems/index.html#scanmodem") tool to scan your modem.
You can download to xp and then transfer the file to ubuntu. then you install the scan Modem and run it ( under ubuntu only - read the installation instructions )
The output will show if you need a driver for your modem or not.
Good luck

---

### Post by ieee488 on 2007-01-14
The quick and dirty way to find out if your modem is compatible with Ubuntu without you having to install driver is to 
1.) open up a Terminal window
2.) type **sudo wvdialconf** and hit Enter key

you should see Ubuntu testing the ports looking for a modem
if it finds it then you are in luck

if not, then download and use scanModem as suggested

---

