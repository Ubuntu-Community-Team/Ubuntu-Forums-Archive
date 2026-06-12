---
title: "Change in Wifi settings cause ath0 to stop working?"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by mskadu on 2006-12-14
Hi everyone,

a BIG thank you to those who answered my previous question so quickly. Here's a new one.

I recently had to reset my wireless router which meant i had to re-configure most of my settings. And while i was at it i changed things like my SSID, IP range, etc. I used a ethernet cable to connect to my router and do all the required stuff. 

However, now my wireless refuses to work despite being able to see my new SSID in the list of wireless lans and entering the right password (it didnt have a password earlier). 

The curious thing is that i dont seem to get a DHCP lease. I tried a "sudo ifdown ath0" and then a "sudo ifup ath0", which showed me that it was still trying to connect to my old router ip address for it DHCP lease. ](*,) 

I've tried reconfiguring my wireless connection using that little GUI tool that comes with Ubuntu (i forget its name). I tried both - DHCP as well as manually specifying a ip address for the wireless communication.

What am i doing wrong?:???: 

Thanks in advance..

- Mskadu

PS: Sorry if this is the wrong place to be posting this

---

### Post by mskadu on 2006-12-14
This problem is now solved. Here's what i did:

a) Removed the password on my router
b) Was able to connect to my wireless router
c) Set password and restarted router
d) Was able to connect after supplying new password

I dont see why this order worked -- but work, it did :rolleyes:

---

