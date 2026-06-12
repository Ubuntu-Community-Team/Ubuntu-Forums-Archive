---
title: "TSClient VNC Trouble"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by goodmayonnaise on 2007-09-16
I'm still pretty new to Ubuntu and Linux so I'm not exactly sure what happened. I've been using the Terminal Server Client (tsclient) to connect using RDP with some machines and VNC with others.  I used to be able to connect to both kinds of machines fine until recently. I can't connect to any VNC server with tsclient. I still can connect to RDP machines. VNC connections just give me a generic "An Error has Occured" message and the details to give me any insight.

I noticed it after I installed a VPN connection manager.   I just installed Krdc and could connect to my VNC machines without a problem. But I still want to fix tsclient. 

I've tried completely uninstalling and reinstalling tsclient. That didn't work.  So I'm stuck. Any advice?

---

### Post by colinnwn on 2008-07-12
I can use TSClient 0.150 to RDP into my Windows computers, but I don't know how to get it working to VNC into my Linux computers.  The protocol selector for VNC, XDMPC, and ICA are all greyed out; only RDP and RDPv5 are available.  

Is there a way to use TSClient to remote into a Linux computer?

Thanks.

---

### Post by maiqinha on 2008-07-12
do drop by to [www.shop-foco.com](www.shop-foco.com)  look through the articles there. With information on anything from getting the  cheapest shoes
welcome website: [www.shop-foco.com](www.shop-foco.com) ,there are are have many cheap products

---

### Post by {}dif{} on 2008-07-14
You need to install xtightvncviewer:

```
sudo apt-get install xtightvncviewer
```

After that, restart tsclient and VNC should no longer be grayed out in the dropdown menu.

:)

---

### Post by colinnwn on 2008-07-14
Worked a treat, thanks!  Is there anywhere on the web I should have found this?  I looked at a couple pages of google results and found no decent docs for TSClient.  This is the first time I haven't found lots of good docs and forums for a program in Ubuntu.

---

### Post by waapwoop1 on 2008-07-14
i have the same problem as teh first guy.

Its not greyed out. I insatlled VNC from the package manager and VNC is an option. I have VNC server running on my home computer, (XP)

when i try to connect it says Error, etc.  I have forwared all the ports on the router, I can get RDP working with no trouble, but not VNC.

---

### Post by colinnwn on 2008-07-14
Have you tried Remote Desktop Viewer instead to see if it works?  If it works you can rule out a problem with your router or XP config of VNC.  That would indicate a problem specifically with TSClient.

---

### Post by waapwoop1 on 2008-07-14
I have tried that.

I can connect to the remote desktop, i can login with the password. But no display comes up, just a grey screen. Once i got a black screen. weird hey

---

