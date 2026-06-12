---
title: "Remote desktop? XP to Ubuntu?"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by dESAI on 2008-04-09
Hi Good People!

My dad has problems with his Ubuntu pc which I gave him about 6 months ago. Exported PDF's are messes up. I live in a different country so I always try to use a remote desktop client to fix any pc problems he might have. This is the first real problem he's had with Ubuntu software. 

Because I have ongoing problems preventing me from re-installing Ubuntu on my Ubuntu PC (installation CD's always have errors, even after something like 7 attempts to make a bootable cd) since it died, I want to know if i can connect to it via XP?

Please help me to help the old man. He's... sooo old! :popcorn:

Thanks all! Have a good day.

---

### Post by njparton on 2008-04-09
If his ubuntu PC is already set up with a VNC server (and it sounds like it is) you just need to install a vnc client in windows (realvnc, tightvnc etc) and point that at his remote PC.
 
You could also use vino which is built into gnome to export an x-session and connect to is via an xclient in windows such as xming.

---

### Post by Belak on 2008-04-09
I haven't used this, but it looks promising:
[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

I think you might just have to enable a setting in ubuntu and find the Ubuntu PC's ipaddress.

Optionally, you could just get a command line client using Putty

edit:
darn. You beat me to it.

---

### Post by dESAI on 2008-04-09
I'm still a linux n00b :confused: hehe

---

### Post by Belak on 2008-04-09
It might help up being able to help you, if you told us what you were confused about...

---

### Post by njparton on 2008-04-09
Putty is for connecting to a remote ssh server such as openssh yielding command line access not for a desktop connection like vnc.

---

### Post by njparton on 2008-04-09
> **dESAI said:**
> I'm still a linux n00b :confused: hehe
 
Tell us how you used to connect remotely and we'll tell you how to do it from XP.

---

### Post by skroops on 2008-04-09
VNC is a remote desktop program.  A server is run on the machine that you want to connect to, and a client is run on your machine to connect to it.  The windows client is available here [http://www.realvnc.com](http://www.realvnc.com)

Your dad may already have VNC installed but it may still need to be configured.  A guide to configuring VNC server on ubuntu is here [http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php](http://lifehacker.com/software/how-to/set-up-vnc-on-ubuntu-in-four-steps-317125.php)

If you or your dad are behind a router you may have to enable port forwarding.  The VNC server has a configurable port that it runs on and you will have to open that port on your dad's network if it is behind a firewall, and you may have to specifically direct that port to his machine behind the router/firewall.  More information on port forwarding is available here [http://www.portforward.com](http://www.portforward.com)

When you are finished setting everything up you will start the VNC client on your windows machine, put in the IP address of your dad's machine, and connect.  His desktop will appear in a window on your machine and you will be able to use his computer remotely.

---

### Post by njparton on 2008-04-09
If you're connecting over the internet you may also want to tunnel your vnc connection within an ssh connection to ensure that it's encrypted.

---

### Post by dESAI on 2008-04-09
> **njparton said:**
> Tell us how you used to connect remotely and we'll tell you how to do it from XP.

Thanks :) 

In the past I've connected remotely using Dameware. These days I use Win Live Messengers Remote Assistance request.

The problem is I am behind a router and so is my dad. He has minimal computer skills, so asking him to install something is bad enough. Asking him to play with his router is not an option.

---

### Post by Jozza The Wick on 2008-04-09
Try 'CoPilot', an application that was designed for this sort of thing (albeit) on Windows computers. It'll handle the router issues & is meant to be an easy, quick download.Costs a few bucks per use, but I think may be free on weekends...

[https://www.copilot.com/](https://www.copilot.com/)

It's supposed to be runnable under Wine - the question is whether you can get your dad to start Wine & then install it.

Alternatively, you might want to download a copy of your dad's router's manual (which I'm sure you can find online), and walk him through the port forwarding over the phone. If you have the manual it would make it easier for you to follow along as he goes through the steps. (And then use RealVNC)

If there's another Windows computer behind his router (running Windows), you could perhaps CoPilot into that and RealVNC across to the Ubuntu box (and avoid the port forwarding)?

JtW

---

### Post by DFLiddle on 2008-04-16
If you provide remote support to many people on different systems on a regular basis, then I suggest that you look into the Bomgar B100 appliance at [http://www.bomgar.com]("http://www.bomgar.com"). We use a B200 on our campus, and it works beautifully to connect securely to just about *any* operating system. Firewall issues are rare. Support staff can work from Windows or Linux, and within a month Bomgar will be adding a Mac client to the list.

---

