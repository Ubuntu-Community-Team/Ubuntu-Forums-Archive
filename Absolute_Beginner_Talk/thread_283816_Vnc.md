---
title: "Vnc"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by amitroy5 on 2006-10-24
I always connect to another computer using Windows using TightVNC on Windows XP. I was wondering what is a good similar program for Ubuntu?

---

### Post by brentoboy on 2006-10-24
the options are limitless.

what OS is running on the remote PC, and what is running on the local PC?

Are they both ubuntu?  is one Windows?  

Do you want to stick with VNC? or are other things OK?

is it 100% LAN based (all in one local area network) or do you have to connect through the internet or a WAN)

---

### Post by amitroy5 on 2006-10-24
Both systems are Ubuntu. I enabled VNC on the other one using the "Remote Desktop" under System --> Prefernces. So, whatever that one supports. Also, I've been connecting accross the internet. I'm in Los Angeles. I've been connecting to San Francisco when I was using TightVNC on Windows XP.

---

### Post by brentoboy on 2006-10-24
you need to use VNC

the problem is that VNC isn't the same as it is in windows.

the same client works either way, but the server is totally different.  in windows, you can leave your computer at the login prompt, and connect from a distance and login as whomever.

but, in linux, a user needs to be logged into X, and needs to dedicate a hidden session to the VNC server, and you connect up from a distance and use that.

But someone else is going to have to help you with that, I dont have one here to play with, and I forget the details.

Funny thing is, I dont see much in the wiki about it, but it seems there was a lot at one point... ? hmm

---

### Post by amitroy5 on 2006-10-24
I had the system working for quite a while. The remote computer is running Ubuntu. I used to run Windows XP and used TightVNC viewer. I was wondering if there was a good VNC program for Ubuntu. The server part does not matter.  I just need a good client program to connect. Thanks!

---

### Post by brentoboy on 2006-10-24
the quick and dirty solution is to add xvncviewer

in fact, I bet ubuntu installs it by default.
open a terminal and type xvncviewer
or maybe 

this particular vnc viewer is bare bones (at best) but it gets the job done.

if you open synaptic (the add remove programs application, in advanced mode) you can search for vnc clients, it will come up with several options.  some of them might even give you a nice entry in the gnome menu system to make life easy.

I need someone else to pipe in here though becuase I havent thought much about vnc for quite some time.

---

### Post by lazyart on 2006-10-24
Terminal Server Client is already installed in Ubuntu (Applications->Internet).  Just change the protocol from RDPv5 to VNC and enter the connection info.

---

### Post by amitroy5 on 2006-10-24
What exatcly is "client hostname?" I never had to enter that in TightVNC. Thanks!

---

### Post by ewl1217 on 2006-10-24
That would be the IP address or domain name of the computer you're connecting to that's running the server.

---

### Post by lazyart on 2006-10-24
Check the remote desktop settings on the server computer for the settings maybe?  Like *computername:0*?

---

### Post by amitroy5 on 2006-10-24
Thanks for your help. I got it working. :)

---

### Post by Varjagy on 2006-10-25
OK, this thread helped me alot, but there is one thing I wonder about. 

I set the viewer to show the remote desktop in 1024x768, but it still shows it as the resolution on the remote desktop. Any sugestions?

---

### Post by Mission 10 on 2006-10-25
The preinstalled vnc should work. All you do is type in vncviewer and the ip address. The example is what I do on my network. If you don't know the ip you can ifconfig eth0. You may want to make a static IP if you haven't already to avoid confusion.

```
vncviewer 192.168.1.2
```

```
ifconfig eth0
```

---

### Post by Varjagy on 2006-10-26
It's not that I can't get it too hook up or anything, but the fact that the VNC viewer doesn't do what I want it to do.

1. It shows full resolution size 

2. It shows all colors (32-bit true-color).

I want it down to what I set it too on my laptop, but it's not doing that.

Suggestions?

---

