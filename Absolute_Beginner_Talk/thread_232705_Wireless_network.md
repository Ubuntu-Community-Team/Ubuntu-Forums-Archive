---
title: "Wireless network"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by flemmingesm on 2006-08-09
I am all new to Linux and Ubuntu. I have tested the live CD and am convinced that this is what I want to use.
Only trouble is my "TOPCOM skyr@cer wireless USB stick 54 Mpbs - V2" that doesn't seem to be recognized i Ubuntu. The company ewbsite doesn't offer a native linux driver.
As I am an absoulute beginner i need a "dummy guide" on what to do...
Can anybody help???

Flemming Mørup
Denmark

---

### Post by wieman01 on 2006-08-09
You may be able to use the native Windows driver for your adapter. I am doing it in connection with Linksys WUSB45g v4. Give it a shot and search for "ndiswrapper" and its usage. The module allows you to install wireless cards while making use of the driver that ship with the Windows CD.

---

### Post by flemmingesm on 2006-08-10
Thanks.
I have installed ndiswrapper, the GUI and loaded the driver from Windows XP: "sis163u.inf". I get the message that hardware is not present. What dod I do now???

Flemming Mørup
Denmark

---

### Post by wieman01 on 2006-08-10
When deploying the Windows driver please ensure all driver related file are in the same folder as the *.inf file. The system needs all of them (usually it should be around 3 files).

Could you also post the content of your /etc/network/interfaces file?

---

### Post by aeiah on 2006-08-10
dniswrapper can be rather fiddly. i found that for my wifi card, a driver for linux had already been built independant of the company. there are databases that will tell you what chipset your card uses. a lot use the same chipset, even across brands. maybe the chipset has some independant driver support in linux. it may be more efficient and less of a headache than ndiswrapper.

---

### Post by davebgimp on 2006-08-10
There's info on your card working with ubuntu at this link:

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Just scroll down to Topcom.

---

### Post by flemmingesm on 2006-08-16
Hi there

Thanks for the replies!
I've been out of town...
My mistake was only to include the .inf file. I copied the other files as well and now it works wonderfully!

Thanks again!

Flemming Mørup 
Denmark

---

