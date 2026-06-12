---
title: "PPP VPN software + tv out"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by robcolclough on 2007-07-24
Hi there,

I'm pretty new to Ubuntu and Linux in general and would really like to use it as my main OS. I've got most things that I need up and running like the correct codecs for avi/mp3 files, display drivers etc but there are two things that I need that I haven't managed to sort yet....

1. I need a way of connecting to my work vpn (windows based) to pick up my email. Any suggestions?

2. With my old windows setup I could have a dual display in order to watch films on my larger TV, I have an nVidia geforce 4 ti4200 card and have tried the nvTv application but it doesnt seem to work... are there any other ways of doing this?

Thanks in advance for your help, I just need to overcome these couple of obstacles and Ubuntu will be able to totally replace my windows system :D 

Thanks

Rob

---

### Post by MrHippocampus on 2007-07-24
Thankfully these two obstacles can easily be overcome :D

The easiest way to get pptp working is to install networkmanger and its pptp extesion, that way youll be able to right click on an icon in the takbar and easily connect to your VPN. Unfortunately im not in ubuntu at the moment so I cant tell you which packages to install, hopefully somebody else can :)

For dual displays simply ensure you have the nvidia driver installed and then you may be able to use the nvidia-settings program to set up your dual displays (I say may as it sometimes doesnt detect TV's being connected if your using S-Video/Composite, this isnt a problem though as you can enable it by editing xorg.conf directly).

---

### Post by robcolclough on 2007-07-24
Hi i've just tried networkmanager with the pptp extension and I'm getting strange results: I supplied it with the correct address for my company's VPN server and when I select it from the list I get the login box as expected, but once I type in my details nothing happens... I have just looked in the system log for any information and one thing looks out of place: it is listening on eth0 for a DHCP reply BUT I'm using ath0 as my only connection to the internet(wireless)? After a while it gives up listening on eth0 and quits.

Any ideas?

---

### Post by robcolclough on 2007-07-24
also, when I try disabling all of the other network adapters... the VPN option becomes unavailable in network manager. Is there any way of doign this over a wireless connection?

---

### Post by MrHippocampus on 2007-07-25
Strange, I and other people I know have done this over a wireless network with no problem. There is another way to get pptp working, although its a bit more in depth, there are some instructions for it [here]("http://pptpclient.sourceforge.net/howto-ubuntu.phtml").

---

