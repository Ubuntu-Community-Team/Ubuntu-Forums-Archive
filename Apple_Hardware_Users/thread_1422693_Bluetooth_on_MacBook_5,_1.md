---
title: "Bluetooth on MacBook 5, 1"
date: 2010-03-05
forum: Apple Hardware Users
---

### Post by alaroldai on 2010-03-05
Hey guys

I just finished installing Ubuntu 9.10 on my macbook 5 1, and have found that bluetooth apparently does not work. It was working while booted from the live cd. I have found several posts on the forums recommending that I reset bluetooth using [FONT=Microsoft Sans Serif]hciconfig hci0 reset [FONT=Verdana]but this command returns "Can't get device info: No such device". Also, the bluetooth preferences window shows that no bluetooth adapters are present. I've just started with linux, so i'm rapidly running out of ideas. Any hints?

-Alaroldai
[/FONT][/FONT]

---

### Post by Kulgan on 2010-03-06
You are not alone. 
Now that I finally got round to upgrading my phone's firmware, I can use bluetooth - just not from Linux... 

This doesn't just apply to Macs; Dell Studio 1537 here, BT working before upgrade to Karmic.

---

### Post by linuxopjemac on 2010-03-06
Blueman is an application that can make a lot of bluetooth stuff working...

---

### Post by Kulgan on 2010-03-06
Blueman or bluemon? Blueman doesn't appear to exist. 

Solved the problem via Windows. I fresh-installed 7 a while back, so I had to install the Vista bluetooth driver and enable bluetooth from there. Upon reboot the bluetooth managers work, although light indicates that it is never turned off. Confirmed working with phone.

---

