---
title: "Ubuntu hates my wireless"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by 0_o on 2006-08-28
[-o< 

I have installed ubuntu dapper drake on my laptop. An Averatec 3200 series. 

My problem is it does recognize all of my avalible internet connections (2 wireless, 1 ethernet, and 1 modem connection), but I can't connect to my access point. I don't know if I am not configuring it correctaly, or what.

My 2 wirelss connections are displayed as "eth1 and "ra0." The ethernet connection is displayed as "eth0" and the modem "ppp0."

I have set the default gateway device as eth1, and tried to configure it correctaly. I typed the network name, the wep key, and the connection settings, but it still does not work. 

I have tried ndiswapper with my pc, but I am so Linux-retarded I couldn't get that to work either. Would that be a good rout to go?

I have no idea what I am doing wrong, I have seen other people with my same problem, but I still can't fix the problem.

---

### Post by benfindlay on 2006-08-28
Ndiswrapper is a good way to get it sorted, especially if your network cards are running on generic chipsets. WIth some, it is worth letting linux try and auto set them up for you. Others need ndiswrapper to configure them (it actullay uses the windows drivers!)

Also it is worth installing a program called network-manager. It is listed in synaptic package manager, so if your ethernet works, I's suggest plugging in, and installing it as it allows you to see a lot of what is going on with your network devices that you don't normally see.

Hope this helps!

---

### Post by 0_o on 2006-08-28
Hmm.

Can you help me install ndiswrapper, because I have tried, and I don't know the first thing about the commands.

---

### Post by benfindlay on 2006-08-28
I take it you have the tarball file? If so, then I direct you to the following thread:

[http://www.ubuntuforums.org/showthread.php?t=244311]("http://www.ubuntuforums.org/showthread.php?t=244311")

This should show you everything you need to know to get it installed

---

### Post by 0_o on 2006-08-28
Thank you, I'll give that a try.

---

