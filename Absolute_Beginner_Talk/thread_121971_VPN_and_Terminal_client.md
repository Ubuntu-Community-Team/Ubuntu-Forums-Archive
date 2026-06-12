---
title: "VPN and Terminal client"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by cje on 2006-01-26
Hi folks, 
I need some help to set up a pptp VPN connection and find a suitable Terminal client.

VPN: I've seen some of the posts in this forum about VPN. But, I need to ask if there are anyone who may tell how to download, configuer and set up a pptp VPN connectin in Ubuntu in the graphical view and not the in the script view.

Terminal Client: further, I need to be guided to find a suitable Terminal Client to talk to a Windows NT environment.

Thanks for any help.

---

### Post by KevinCole on 2006-01-26
For talking at your Windoze boxen, install **rdesktop**...

**rdesktop**: RDP client for Windows NT/2000 Terminal Server rdesktop is an open source client for Windows NT/2000 Terminal Server, capable of natively speaking its Remote Desktop Protocol (RDP) in order to present the user's NT/2000 desktop. Unlike Citrix ICA, no server extensions are required.

---

### Post by Smandola on 2006-01-26
I'm curious to know what you are planning on doing with your NT env when you connect to your linux box.  

I had originally thought that I wanted to have my XP env interact with my Linux box, but really all I wanted was a way of sharing files if I didn't happen to be at home (where my linux box sits). And I also thought the only way to connect would be to use a VPN (since the linux box sits behind a router). 

Instead of setting up a VPN server on my Linux box, I went with Hamachi ([www.hamachi.cc)](www.hamachi.cc)).  Connected the linux box to the service, and then when I need to I can run it from my XP env, from anywhere, and connect, and get my files.  There is a graphical interface for Linux.  However you need to download it separately.  The GUI in XP is simple and effective.

If you are looking at controlling your Linux box from NT, have you looked into VNC ?   

I hope this is helpful information, I know that I didn't answer your questions specifically, but maybe I gave you some ideas to look at.

---

### Post by cje on 2007-03-05
Thanks for your info Kevin, but the sudo apt-get install rdesktop return "not found"... Any idea?

And for your, Samadola; I'm trying to run a windows app at the windows terminal server in my office. Anyway, thanks for you info.

Thanks for quick reply too!

---

### Post by compmodder26 on 2007-03-05
Try network-manager-pptp.  You have to enable the universe respository.  Install that and network-manager-gnome.  That should get you a gui for managing vpn for pptp.

---

### Post by steve.horsley on 2007-03-05
I hope that network-manager-pptp works for you. I've only ever installed and configured pptp from the command line, so I can't comment on it.

As for a terminal client, it should be installed by default. Go to the menu Internet->Terminal Server Client and choose protocol RDP. Enter other required details and connect.

---

### Post by cje on 2007-03-06
Thanks for your info steve.
Anyway, when I do start the TSC connection the screen goes black and the computer logs off. (I'm testing on a Xubuntu system, PII, 500MbRam)
Any idea, what's wrong?

---

### Post by steve.horsley on 2007-03-06
No idea, I'm afraid. I haven't used the RDP client very often, but it has never failed for me. I did notice today that there's a different RDP client (Gnome-RDP I think) in add/remove, but it runs on mono. Still, maybe worth a bash.

---

