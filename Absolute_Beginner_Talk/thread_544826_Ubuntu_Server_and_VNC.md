---
title: "Ubuntu Server and VNC"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by tuseef on 2007-09-06
Hi Im trying my luck here so here goes nothing

Apologies in advance as im totally new to Linux from a setup perspective

After struggling (and going through the shock of not having a GUI when installing Ubuntu Server 7.04) I have managed to successfully install Ubuntu Server with the GNOME desktop.

I used some online guides which were very useful and set up a LAMP server

In terms of networking, I have 8 public ip's (5 usable as 1 is network, other is broadcast other is router)

I have setup my netgear router in routed ip mode, with each machine on my LAN taking a public ip.

I have forwarded all the relevant ports in my router to go to the relevant machine on my network which runs the ubuntu server (referenced by public ip)

The ports I have forwarded are as follows:

5800
5500
5900
5801
5901
22

This is all fine. I have 2 internet connections at home so I am able to test from an internal and external perspective.

I've done nothing to my ubuntu server apart from install LAMP and the GUI and run a system update

I can remotely access the server via another windows machine on my LAN using tightVNC

I can remotely access the server via the same windows machine even when its connected to my secondary ISP

Therefore I know that particular functionality is working and I could go someplace else physically (i.e. my work machine) and use TightVNC to connect/browse/do whatever

Here lies the problem, our machines at work at heavily locked down and I cannot install anything, so I would like to access via a browser with java.

When i try using public ip of machine behind my router on port 5900 i just get the following

RFB 003.007 

I have no idea what im doing wrong, as far as im aware there is no firewall on the ubuntu server so I should not need to open any ports.  I tried the same command using the other ports and i got nowhere

As a side note, I used to run windows 98se as a server using pretty much the same network setup, however i had tightvnc installed on it and could remotely connect via tightvnc client as well as java.  

On my ubuntu server I just use the standard software (system -> preferences -> remote desktop

These seem quite different to me, though i appreciate they are probably not.   Remote desktop on ubuntu does not seem to have any many changable options as tightVNC had on my win98 machine..I was able to configure the ports etc....all this thing seems to show me is 

vncviewer server.zdsl.isp.com:0 <<<<<i cant seem to change this info

I have searched around for help but had no luck

Just to clarify, I can connect to my ubuntu server via VNC, but not via browser/java

I can also connect to my server from an internal and external machine using SSH which i have set to tunnel to my server via public ip on port 5900, but when i use the command line given to me by remote desktop 

e.g. vncviewer server.zdsl.isp.com:0 I just get

VNC viewer version 3.3.7 - built Mar  8 2007 21:56:52
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Error: Can't open display:

Same happens when I try any of the other ports i listed earlier.

Any help is greatly appreciated

---

### Post by tuseef on 2007-09-06
Still struggling with this.

I see that Tight VNC is also available for linux, yet i would not have a clue how to install it

---

### Post by tuseef on 2007-09-07
bump

---

