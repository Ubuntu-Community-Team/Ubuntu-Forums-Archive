---
title: "Not able to open some sites"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by wilzad on 2007-07-26
Hi,
I am not able to open some sites from ubuntu, but thats working fine if i open in windows. 
one site is : [www.ubuntu.com]("http://www.ubuntu.com"), (but i am able to use update manager and i am able to install updates for my ubuntu feisty), but browsing is not working. [www.google]("http://www.google") is working fine. 
 
please advice.
 
regards
Wilzad

---

### Post by davidsrsb on 2007-07-26
This is often a sign of MTU or MRU problems. This the maximum packet size allowed by your ISP connection and defaults to an MTU of 1500 bytes. PPPoE usually wants 1492, but I have seen less. Wireshark is the best tool to see what is really happening. It is available for both Linux and Windows, so you can compare packet sizes for them both.

---

### Post by wilzad on 2007-07-27
is there a option to change this MTU settings ?
will setting up dsn address in resolve.conf fix this

---

