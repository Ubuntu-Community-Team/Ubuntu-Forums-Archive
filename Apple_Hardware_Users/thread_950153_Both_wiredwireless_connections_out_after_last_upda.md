---
title: "Both wired/wireless connections out after last update"
date: 2008-10-16
forum: Apple Hardware Users
---

### Post by gioanpj on 2008-10-16
Hello,

I'll preface this by saying that I'm a neophyte linux user. I have Ubuntu installed on a 2007 Macbook. I installed the latest updates (I'm assuming) a few days ago. It required a system restart. After the restart the wireless connection stopped working, nor does it connect when the Ethernet cable is plugged in. The icon for the internet connection appears at the top of the screen, but it won't pick up any networks. Here is some information which might be helpful:

Into the terminal I typed in "ifconfig lo" and got the following:

Link Encap: local loopback
inet addr: ::127.0.0.1 Mask:255.0.0.0
inet6 addr: :: 1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2168 errors:0 dropped:0 overruns:0 Frame:0
TX packets:2168 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:108400 (105.8 KB) TX bytes:108400 (105.8 KB)


I'm really not sure what to do at all. If anyone could offer any constructive advice, I'd be really thankful.

---

### Post by cyberdork33 on 2008-10-16
what does just 'ifconfig' return?

---

### Post by gioanpj on 2008-10-18
> **cyberdork33 said:**
> what does just 'ifconfig' return?

Eth0   
       
       Link encap:Ethernet  HW 00:19:e3:40:dc:cb
       UP BROADCAST MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
       Interupt:16

Lo     
       
       Link Encap:local loopback
       inet addr: ::127.0.0.1 Mask:255.0.0.0
       inet6 addr: :: 1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436 Metric:1
       RX packets:2168 errors:0 dropped:0 overruns:0 Frame:0
       TX packets:2168 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:110700 (108.1 KB) TX bytes:110700 (108.1 KB)

---

### Post by mfox on 2008-10-18
I had a similar thing happen on my MSI Wind with the Realtek wireless card.  In this case, I had to compile the drivers when they were first installed, and the compilation apparently didn't carry over to the updated kernel that came with the update.  I don't know if the same would apply to the MacBook, where the Broadcom firmware is extracted, but it might.  I suggest redoing the firmware extraction that you did when you first installed Ubuntu.

---

### Post by gioanpj on 2008-10-18
Do you think it would be better to just send what I want to an external harddrive, then install the new version of linux in a few days?

---

### Post by cyberdork33 on 2008-10-18
eth0 is your wired card. It seems to be recognized by the system.

---

### Post by gioanpj on 2008-10-20
Mmm. Yeah, this is really odd. The network manager shows up, etc. But none of the networks do. I'm really in the dust in this one. I'll mess around with it some more.

---

### Post by klyick on 2008-10-21
I had this same problem. Here's what fixed it for me.

If you are running a macbook and ubuntu, you may have stumbled across a thread on these forums regarding a update to the ath driver. A kind individual in that thread offered a script that would compile and create the new driver based on whatever kernel you currently had. 

Well, it seems that the recent update effectively borked this compiled driver. However, you'll be happy to hear that the fix is as simple as recreating the driver using that script again and installing it, and all is well. 

Hope this helps someone.

---

