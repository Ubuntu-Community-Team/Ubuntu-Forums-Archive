---
title: "Enabling Wireless networking in Ubuntu Linux (Broadcom)"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by jbucaran on 2007-04-28
Hello,

I have followed through several how-to's about solving this problem and I have seen few post saying "I solved the problem, thanks!". Honestly by doing some of them I have ended up messing all up and having to reinstall Ubuntu several times over. I need to (1) enable wireless networking for my **Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)** in my HP dv8000 laptop and (2) setup to accept it my wireless network working through a LANPRO LP-5420G wireless router. I have seen some tutorials for just that wireless card device but nothing works or the guides are just too clumsy or too advanced to do for me.

Please, if anyone (actually) knows how to solve this, explain it in easy terms and a how-to fashion for everyone out there having the same headache. 

Regards, Jorge Bucaran

---

### Post by Najand on 2007-04-28
The broadcom guys never support linux drivers. There are some ways but you cannot be sure it always works.

---

### Post by felipe.ryan on 2007-04-28
Damn mate this was a pain for me as well, have you tried the method with fw-cutter ??? That was the only method that worked for me, if you haven't tried, try searching for bcm43xx-fwcutter in the forums. It worked so well for me.

---

### Post by jbucaran on 2007-04-28
I have read that due Broadcom have offered no support configuring wireless networks with this card in Linux is a pain. However I have read it is possible. But I is there a way?

---

### Post by jbucaran on 2007-04-28
felipe.ryan, can you tell me what your Broacom card model is? BCM4318 or BCM4309.

---

### Post by jbucaran on 2007-04-28
I just found a solution that works fine for me: I type in the terminal

"sudo apt-get install bcm43xx-fwcutter"

And all worked out. I must also point that the roaming mode is enabled for the wireless connection. I just click the network icon and select "connect to other wireless connections" and setup my network. It is WPA with AES encryption, the password is in hexadecimal and I didn't have to enter any separators or prefixes just something like this: 
"CEEF8545E2D2801A00A4031972387425641C8C813CAAADAA248FD53AA1EE2C"

Now it is working fine. Thanks for the help.

---

