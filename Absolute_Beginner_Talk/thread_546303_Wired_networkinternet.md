---
title: "Wired network/internet"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by jay3712 on 2007-09-08
I just did a fresh install of feisty on a computer I built a couple years ago just for fun. Asus P4S8X motherboard, P4 2.33Ghz, ATI 9000 pro, 512 ram. I cannot get to the internet. I am using a wired connection to my Belkin F5d7230-4 router. It shows my wired network connection on dhcp, but no worky. I know this question is very common but I have been looking for a while and would love some help. Also, go easy, I'm a newb when it comes to Linux. 
Thanks fellas

---

### Post by oilchangeguy on 2007-09-08
try powering off the modem, router, and computer. restart everything and see if that works.

---

### Post by jay3712 on 2007-09-08
nope, no dice

---

### Post by oilchangeguy on 2007-09-08
try modem to computer. leave out the router. (probably should restart everything again) and do you have a two screened icon on the top panel?

---

### Post by jay3712 on 2007-09-08
I took the router out of the equation and restarted everything, still no go. I got the same 'connected to wired network' message and the lil two-screened network icon as I did before.

---

### Post by jay3712 on 2007-09-08
Anyone have any other suggestions?

---

### Post by jay3712 on 2007-09-09
Bump for some more help

---

### Post by jbonll05 on 2007-09-09
I have been using a Belkin F5D7231-4 for about a year. This laptop(Compaqnx6110) is the only wifi machine I have. It has bcm43xx onboard that is not out of the box functional. Edgy 6:10 required the ndis wrapper to work. I am using it wired now - I had to turn off the wifi to get the wired to work the first time. Everything you have done has worked for me in the past. The only difference is this laptop will not wire-up if the non-functional wifi is on and displayed on the top bar. That is grabbing straws! JB

---

### Post by jay3712 on 2007-09-09
My desktop doesn't have any wireless, just the wired connection. Someone please give me some help, this is really frustrating.
Thanks

---

### Post by jay3712 on 2007-09-10
Bump one last time, surely someone can help me.

---

### Post by ieee488 on 2007-09-10
Wish I could help.

I'm typing to you on Ubuntu 6.06 connected to Verizon DSL.

Ubuntu found the network card which I bought secondhand on eBay.
I activated the network card. Set it for DHCP.
And that was it.

Are you trying to get online?

---

### Post by str8line on 2007-09-16
Belkin's default gateway is 192.168.2.1, if you open up terminal and type ->ping 192.168.2.1 what are your ping results?

---

