---
title: "Need help getting online with Wi-Fi."
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by fishmael on 2007-01-22
Hi everyone. Let me just say that I'm a noob with Ubuntu (and all other Linux). 

I have a DSL router that connects wired as well as wirelessly. I know it works fine because I hook it up to my desktop (WinXP) wired and I use my Nintendo DSlite wirelessly, using Wi-Fi. However, that's all I've done concerning wireless.

Now, it seems that everytime I mess around with network settings on Ubuntu, I keep making stuff screw up. When I first installed it, I was online instantly. However, it had a low connection rate (maybe 30-40%) and I thought it was my neighboor's connection. I'd rather just connect to my own router. So, somehow I deleted that on accident and can't ever seem to get back on. Then I remember messing with ath0, whatever that is, but it didn't do any good. Now, after trying to run some commands like trying to install MadWifi and some other Network Organizer (and forgetting that I needed to online already to install them, D'oh!) ath0 has now disappeared. And I don't know how to add a new connection. Hell, even the wireless internet option disappeared from the network option! 

I have no idea what to do with the Wireless Network Setup Wizard from the host computer, also WinXP. I guess I was just lucky when I got the DS on through Wi-Fi. 

Btw, I know that the Linux computer, a Sony Viao laptop, doesn't need a network card to get online, it has built in wireless LAN access.

Please help me :O

---

### Post by riven0 on 2007-01-22
Have you tried running these commands yet?

> iwconfig

> ifconfig

&

> sudo /etc/init.d/networking restart

Does it help at all?

---

### Post by fishmael on 2007-01-22
The restart prompt seemed to help somewhat, it restored the ath0 and wifi0 connection options. I'm just not sure what to do now. I set my network settings to the wifi0, and made sure the network devices for wifi0 were available and it says it was sending and receiving packets, but i'm not sure what to do now. 

Do I need to enter information like a SSID key from the host computer//router? Just tell me what kind of info I need and I'll get it. Is IP 168.192.1.0 of any relevance? On either WinXp desktops, these help me manage my router settings.

---

### Post by fishmael on 2007-01-22
okay, i'm on. i went to my network options for my router and set it to channel 3, corresponding with the one aht0 was set to. awesome. now i'm installing some packages that will help me get the best connection.

---

### Post by riven0 on 2007-01-22
I see you fixed it yourself. Awesome! :KS 

Now you may want to look into installing network manager (sudo apt-get install network-manager), as that helps a lot of people with unstable wireless connections. If that doesn't work, try [connection manager]("http://www.ubuntuforums.org/showthread.php?t=299462").

---

### Post by ryanhaigh on 2008-02-22
For future reference of others who may look here I believe wifi0 is kindof a dummy device and that wireless settings should be applied to the ath0 interface.

---

