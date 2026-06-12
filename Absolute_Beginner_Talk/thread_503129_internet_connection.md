---
title: "internet connection"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by ankuj2004 on 2007-07-17
i have installed ubuntu 7.04 .I am using intex lan card but it is not being detected by ubuntu what shuould i do.
the lan card configuration is 10-100mbps of intex.the net is working fine in windows xp but ubuntu doen not even detect it.

---

### Post by deadlikeoscar on 2007-07-17
Open a terminal and copy and paste the output you get from typing lspci (It's LSPCI but all lowercase) in the terminal. 

If you don't know how to open the terminal (just trying to save you time, sorry if you already know) Click on Appications-->Accessories-->Terminal

---

### Post by anon23 on 2007-07-18
Hi,

I was also having the same problem with same card intex 8139d lan card.  But i got solution just follow the each and every step as given in following link:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

:)

---

### Post by Gen2ly on 2007-07-18
type ifconfig and see if you see your device listed

---

### Post by speeddemon8803 on 2007-07-18
just a little did you know:

ifconfig is linux's version of the famous ipconfig :)

---

