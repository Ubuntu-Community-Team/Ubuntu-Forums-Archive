---
title: "[SOLVED] Remote DesktopHelp!!"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by jamesrfla on 2007-09-08
I have a desktop running Ubuntu 7.04 and I want to do remotely access it from another computer in our home network. I enabled remote desktop in the system/preferences/remote desktop and now I don't know what to do next? Also would it be better to access the desktop that I am trying to remotely login from a Ubuntu computer or windows XP computer?

---

### Post by skymera on 2007-09-08
first, are you wireles?
if you do let ports 5500,5800,and 5900 TCP !AND! UDP
through your router

then in ffirestarter let the computerr connecting through IPTABLES

---

### Post by mlentink on 2007-09-08
Either is fine. In windows. you're going to need a VNC viewer, almost any will do. Google for vncviewer and you'l l find one. Try UltraVNC, which is what I use.
In Ubuntu (or Linux) go to Applications>Internet>Terminal Server Client. Choose VNC as the protocol and enter the IP of the machine you want to look at.
You should be all set.

---

### Post by jamesrfla on 2007-09-08
I am doing it through a wired internet but I do have a wireless router.

---

### Post by mlentink on 2007-09-08
> **skymera said:**
> 
if you do let ports 5500,5800,and 5900 TCP !AND! UDP
through your router

He wants to do it in his home network, so bothering with port forwarding can wait

---

### Post by jamesrfla on 2007-09-08
I got the Ultra VNC on my Windows XP computer. Now what?

---

### Post by jamesrfla on 2007-09-08
I figured it out and it works. Will I be able to access it outside my network? Thank you so much!

---

### Post by mlentink on 2007-09-08
Sure you will, I do it every day. Look at Skymera&#347; remarks: in your router, you will have to forward port 5900 (VNC) to the machine you want to control. 
PLease be aware that the VNC protocol is not very secure. so use it with some reservation

---

### Post by wormser on 2007-09-08
This [site]("http://portforward.com/english/routers/port_forwarding/routerindex.htm") has guides on port forwarding for almost every router.

If you want to access it by domain name instead of ip go [here]("http://www.dyndns.com/").  They have a free option.

I also recommend using ssh to tunnel your connection for security.

```
ssh -L 5900:localhost:5900 username@mydomain.com
```

Then in you vnc viewer use localhost:5900 for the address.

---

### Post by jamesrfla on 2007-09-08
I think I am going to stay with accessing it through my home network. If I just enabled remote desktop on the Ubuntu desktop and and installed the VNC viewer on my XP computer than anyone outside my network can't access the Ubuntu computer right?

---

### Post by mlentink on 2007-09-08
That depends on how secure your router is, but that's almost always ok. So don't worry.
If you ever should decide you want to do remote ( in: from outside your home network) , come back and we'll guide you through it.

---

### Post by jamesrfla on 2007-09-08
Thank you once again!!

---

