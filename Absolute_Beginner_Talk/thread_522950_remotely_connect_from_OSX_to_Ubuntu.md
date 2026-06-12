---
title: "remotely connect from OSX to Ubuntu"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by TarsierSpectral on 2007-08-11
I am trying to use VNC to remotely connect from OSX to Ubuntu which is at my friend's house. He uses DHCP, and IP is assigned by his cable provider. I used ifconfig to get his IP address then on my OSX machine I used Chicken of the VNC and typed that IP address but I can't connect. I get the following message:
Could not connect to server IP:5900 
(it showes actual IP I typed)

Anyone has any clue what I am doing wrong?

---

### Post by tgalati4 on 2007-08-11
You probably need to make a pinhole in your router's firewall for port 5900.  At your friend's house, try logging directly into the modem (192.168.1.1 or similar) and go to Port Forwarding and set a Service called "VNC" at port 5900 for IP 192.168.1.100 (or what ever the actual IP is for that machine).

This does represent a security risk so don't leave it open all the time, only when you need it.  There are more secure methods for remote access.  Search for "VNC tunnel" in the forums for several ways to do it.

---

### Post by TarsierSpectral on 2007-08-11
thanks, but he does not have a router.  He is connected to the cable modem directly

---

### Post by annda on 2007-08-11
look at the iptables in ubuntu. firestarter is the gui - the appropriate port (5900) needs to be open.

---

### Post by TarsierSpectral on 2007-08-11
how do I look at the iptables?  what's firestarter

---

### Post by annda on 2007-08-11
firestarter is the gui to linux native firewall iptables. this is something your friend with ubuntu needs to configure to allow other people connect to his/her computer.

[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by TarsierSpectral on 2007-08-11
I am on my friend's computer how do I do that?

---

### Post by TarsierSpectral on 2007-08-11
so I am in firestarter, what do I need to do in there?

---

### Post by steve.horsley on 2007-08-11
If you don't know what firestarter is (a GUI for configuring iptables) and you haven't configured iptables yourself (if you had, you would also know how to look at it) then you don't need to worry about iptables. Its default setting is not to block anything.

Did you actually start a VNC server on the Ubuntu box? Go System->Preferences->Remote Desktop and check to box to allow remote users.

---

### Post by TarsierSpectral on 2007-08-11
but now I did go to firestarter and it is telling me that the firewall.  I didn't have it before and still could not connect.  Yes, the VNC is started

---

### Post by TarsierSpectral on 2007-08-12
sorry, I was rushing last night and my last response doesn't make sense.  
So, I installed firestarter as someone recommnded here.  What do I need to do next to get this remote desktop working?

---

### Post by steve.horsley on 2007-08-12
First, make sure the firewall isn't blocking it. You could de-install firestarter, but you probably want it eventually, to stop the whole world from connecting to this VNC server. Actually, I would be inclined to do the VNC tunneling over SSH, for security. But let's concentrate on the basics first.

1) Make sure that the VNC server is listening. Use this command:
**netstat -ltn**
and see if you can see an entry for a socket listening on port 5900. When I enable VNC on my PC, I see a line like this:
tcp6       0      0 :::5900                 :::*                    LISTEN

2) Look in the firestarter GUI to make sure port 5900 is allowed incoming. I can't help you there - I've never used firestarter. 
If you don't have firestarter installed, you can use this command to list the firewall rules that are in force:
**sudo iptables -L**
Paste the output into an editor, search and replace your IP address with "1.2.3.4" so you don't tell the whole world where to go hacking, and post the result here. 

3) Maybe your ISP blocks port 5900? I don't know how to prove this other than try to connect to port 5900 from outside, but that doesn't prove it's not a config problem on the box.

---

### Post by fuoco on 2007-09-09
How would I do the opposite? connect from ubuntu to another os x system on my lan?

---

