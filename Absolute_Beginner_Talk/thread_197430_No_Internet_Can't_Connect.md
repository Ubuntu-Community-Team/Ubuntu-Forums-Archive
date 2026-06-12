---
title: "No Internet Can't Connect"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-06-15
I cannot ping. ETH0 is active. I tried deactivate than activate no luck. Can someone please help me get online? I am using cable modem. I submitted ifconfig results earlier. I have integrated NVIDIA graphics with NVIDIA networking. Emachine 160GB HD 1024mb ram AMD sempron 3400+processor.

---

### Post by muep on 2006-06-15
Do you know what type of connection do you use? The physical method is the cable but there are different protocol in use.

For starters, try ```
sudo /etc/init.d/networking restart
```

If you know you should be giving it a password, try searching the forum for pppoe

---

### Post by jasrog on 2006-06-15
When I did that I got NO DHCPOFFERS RECEIVED
SIOCSIFADDR: NO SUCH DEVICE
ETH1: ERROR WHILE GETTING INTERFACE FLAGS:NO SUCH DEVICE

---

### Post by muep on 2006-06-15
Are you sure you shouldn't be using pppoe?

---

### Post by jasrog on 2006-06-15
How would I exactly know? And if I should be what do I exactly do?

---

### Post by muep on 2006-06-15
Usually people get some instructions from their Internet Service Providers. If there are some login names and passwords for connection, you probably should use pppoe. 

I've never used it in ubuntu, but there probably are many people here who have.

---

### Post by jasrog on 2006-06-15
I don't use a password to use internet...it is always on connection...

---

### Post by muep on 2006-06-15
Could you give a little more info? Like what kind of network you have at home? (How many computers, do you have a router, etc. ) as well as some basic info about your computer. How many network cards?

Check the cables ;)

---

### Post by jasrog on 2006-06-15
I only have this 1 computer, it is not on router..directly connected via ethernet to cable modem...It has 1 NVIDIA networking card. NVIDIA Geforce 6100 integrated graphics. For windows cable modem  always configures itself automatically..but UBUNTU I cannot get online.....

---

