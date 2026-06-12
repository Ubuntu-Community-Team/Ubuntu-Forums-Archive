---
title: "Cannot remote connect from Windows to Ubunto"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by vvvladut on 2008-02-04
I enabled remote desktop, and on the Windows machine at work I have VNC installed. I have a dynamic ip, so I looked it up with ifconfig and wrote it down. Then, at work, I tried to connect through VNC writing both the ip and ip:0. It said "Connection refused". Any ideas what to do to make this work, please?

Thanks!

---

### Post by kochecc2 on 2008-02-04
Are you on the same network at home as you are at work? Chances are you will need to set up a port forward on your router in order to reach your home computer using VNC.

---

### Post by vvvladut on 2008-02-05
No, I am not on the same network. How do I set up a port forward on my router? Especially since I don't have a router?? 

Thanks!

---

### Post by kochecc2 on 2008-02-05
If you don't have a router, I assume you are plugged directly into your cable or dsl modem. This would mean the ip address of your computer should be accessible from the rest of the internet.  If this is the case you should be running some kind of firewall. I recommend firestarter. This would also mean there should be no port forward required. You will, however need to open the VNC port on your firewall. By default, VNC uses port 5900. What is the ip address of your home computer? That will help me determine if it is a private network or an internet visible network.

---

### Post by jordanmthomas on 2008-02-05
> **kochecc2 said:**
> f this is the case you should be running some kind of firewall. I recommend firestarter. 

Semantics pet peeve here:  firestarter is not a firewall.

---

### Post by kochecc2 on 2008-02-05
> **jordanmthomas said:**
> Semantics pet peeve here:  firestarter is not a firewall.

Ok. I recommend Firestarter for a program for managing and observing your firewall. It is a complete firewall tool for Linux machines. It features an easy to use firewall wizard to quickly create a firewall. Using the program, you can open and close ports with a few clicks, or stealth your machine giving access to only a select few.   - The Firestarter description in the Add/Remove Applications program.

---

### Post by vvvladut on 2008-02-05
Thank you for your reply, kochecc2. I don't have a modem at all - I have a network cable that goes straight into my network card. In Windows I dial up as if using a phone modem, using a username/password given by my ISP. In Ubuntu I set up a connection in PPPoEconf and it connects itelf at startup.

My provider is RDSLink (or just RDS) Romania. I don't know my home IP because it changes each time I reboot; all I know is that they always start with 89.121.xxx.xxx

Many thanks for your help.

---

### Post by kochecc2 on 2008-02-05
Ok, it looks like you have a form of DSL based on the fact that it uses PPPoE. I would install Firestarter, or use your existing firewall manager if you have one installed, and make sure port 5900 is open. Also how do you have your remote desktop configured? When you go to System > Preferences > Remote Desktop, what is checked?

---

### Post by vvvladut on 2008-02-05
OK, I will install firestarter and try to configure it so that port 5900 is open; but then again, why couldn't I log in if I have no firewall at all? Could it be that the firewall at work doesn't let me?

In Remote Desktop I checked the first 2 boxes and the fourth - I think I got that covered, correct?

---

### Post by rkd on 2008-02-05
> **vvvladut said:**
> OK, I will install firestarter and try to configure it so that port 5900 is open; but then again, why couldn't I log in if I have no firewall at all? Could it be that the firewall at work doesn't let me?

Ubuntu has all ports closed by default. That's probably why you couldn't connect. Firestarter will give you the control to open the port. It is possible that the firewall at work also is stopping things. Depends on how tightly your network folks at work have closed up the network there. Quickest way to tell is to try it after opening the port on your PC at home.

---

### Post by kochecc2 on 2008-02-05
Good point with open ports. My recommendation for you to use a firewall was mostly because you are not behind a router. It could be that your work firewall doesn't allow traffic on that port. That would be something to ask your network administrator if you think they would be OK with you trying to do this across their network. Alternatively you could test it at a friend's house or at an internet cafe to see if it works somewhere besides your work. 

I know when remoting into a windows PC using VNC, you need to open the ports on the Windows Firewall on that machine, maybe you need to do the same on your work computer to use it to initiate the connection. This would involve going into Control Panel > Windows Firewall > Exceptions (tab) then click Add Port...   You can name it whatever you want just make sure it is 5900. I usually make two ports, one for TCP and one for UDP. If you do some research you can probably find which protocol VNC uses, but I just open them both up. 

Hope that helps!

---

### Post by vvvladut on 2008-02-05
Thank you both, I will install firestarter and open port 5900 and post here the results of that. 

At work I use VNC all the time to connect to other computers in the network, so I suppose this means that  my comp at work allows outgoing VNC connections (or whatever thay are called, sorry if I'm not using the correct terminology). Perhaps it only allows VNC connections inside the network?

Anyway, I'll try with firestarter next time and then I'll ask the network admin if I'm allowed to make VNC connections over the internet (probable answer: are you crazy? it's against the company policy!!!!!!!!!!!!!!!!!!!) Then I'll get back to you. Thanks for your help so far.

---

