---
title: "No modem device on ThinkPad X30"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by windglider on 2006-09-29
I have successfully installed Kubuntu 6.06 on an IBM Thinkpad X30.  I have wireless and wired connection running and access to the Internet.  Everything is great, overall.

But I wanted to use KPPP, and discovered that there is no /dev/modem defined.

This box has the Agere modem card mini-PCI installed.  I would appreciate suggestions on how to proceed to load the proper drivers or using apt-get to download modules and/or packages.

Thanks for any help....  :)

---

### Post by Sef on 2006-09-29
Have you checked [linmodems.org?]("linmodems.org")

---

### Post by windglider on 2006-09-30
Thanks Sef.  Yes, I know about LinModems, but that site and its many links are overwhelming.  Nothing relevant seems to come up under Agere or ThinkPad as keywords.  I even seem to know the specific name of my modem "AC'97", but that does not seem to help.

---

### Post by nige2007 on 2006-09-30
hi im having similar issues with an ol a20m thinkpad cant find modem so cant get past first base:(

---

### Post by _duncan_ on 2006-09-30
The link below explains how to set up various dial-up modems to work with Ubuntu.

[Dial-Up Modem How To]("https://help.ubuntu.com/community/DialupModemHowto")

BTW, the term "Agere" is often used side by side with "Lucent" as in "Lucent/Agere" in most sites dealing with software modems. But before jumping immediately into the Lucent driver section, I suggest you read the part about using the scanModem tool from linmodems.org to properly identify your modem chipset. This is very critical to finding the right driver for your modem.

Good luck!

---

