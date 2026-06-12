---
title: "Odd Error with Cisco Systems 350 Seires Wireless Lan on Kubuntu 7.04"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by beastrace91 on 2007-08-18
Heres the trouble I am having, right now I posting this by running Kubuntu 7.04 off the live CD (Just had to throw this in here: Lets see windows do that post a message on a forum while it is installing!) I have as is in the subject line a Cisco Systems 350 Seires Wireless Lan Adapter. I am currently using a Compaq Presario M2000 the Cisco card is in the exspansion slot. While I am booted off the live CD the system see and uses the wireless card, (due to my built in crappy one seems to have gone out) once I have the kubuntu installed it no longer shows my Cisco card at all. Anyone have any ideas what could be causing this?

On a side note I am going to reinstall Kubuntu right now just to see if I got a bad installation I was just wondering if anyone else ever had similar trouble.

~J3ff

---

### Post by HermanAB on 2007-08-18
These commands will tell you something:
$ sudo lspci
$ sudo lsmod
$ sudo ifconfig
$ sudo dmesg

Hope that helps!

Herman

---

### Post by beastrace91 on 2007-08-18
Thanks for the input but I already finished reinstalling Kubuntu 7.04 and it works fine now, something must have corrupted the first time.

~J3ff

---

