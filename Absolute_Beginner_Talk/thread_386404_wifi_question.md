---
title: "wifi question"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by e^(i*pi) on 2007-03-17
I was at a coffee shop tonight and I had some problems using their wifi.  when I launched firefox I got their homepage and agreed to their terms of use, but after that I got nothing.  I switched to my windows partition and everything was fine, so I know it wasn't the establishments wireless that had the problem.  Does anyone have any idea what the issue may have been.  Also, I'm used to bringing up the screen in windows that shows the available wireless networks, where is that in ubuntu?  I will appreciate any answers, as solving this will bring me one step closer to a windows free existence.

---

### Post by 23meg on 2007-03-17
In Dapper, you can select from the available wireless networks and configure your wireless device in System / Administration / Networking. Choose your wireless device there, and click "Properties". You can also install Network Manager, GTKWifi or Wifi Radar (in order of recommendation) to help with the task of connecting to wireless networks.

---

### Post by shanepardue on 2007-03-17
network-manager works great with changing wireless networks. Feisty uses it by default now.

---

### Post by e^(i*pi) on 2007-03-17
ok, I found what I needed in the system -> admin -> networking, and I installed the network-manager.  I don't see it listed under any of my menus (the network manager), where do I find it at?

---

### Post by 23meg on 2007-03-17
Hit Alt + F2 and type "nm-applet" to run it. It will add an icon to your notification area.

---

