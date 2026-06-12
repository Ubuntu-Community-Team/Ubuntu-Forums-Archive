---
title: "New Sessions via Windows VNC Viewer"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by BobHope2112 on 2008-01-29
Hi all,

Apologies if this posting is malcategorized, but I thought it fair to make warning of my neophyte status.  I've searched the web, and specifically this forum, for some assistance in what I'm attempting.  Please give me a nudge in right direction.

From a Windows VNC client, I would like to connect to an Ubuntu (Gutsy) PC, and login to create a new session.  

I've been able to set TightVNC up on Ubuntu, using a [[COLOR="Sienna"]community tutorial[/COLOR]]("https://help.ubuntu.com/community/VNC"), and successfully connect from my Windows client.  This is only works, though, *after* I have logged into Ubuntu, and have manually started vncserver.  I cannot discern if it is even possible to extend this setup to meet my goals.

There are a number of postings in this forum asking for approximately the same function.  Addressing some of the questions or recommendations brought up in those postings:

[LIST]
[*]Ultimately, this machine is intended to be headless, so I want full control of it across the network.
[*]Internet access to this machine is not necessary, or even particularily desired. (I have an academic interest, but it's not something to be implemented.)
[*]I don't want to rely on an automatic login.  The machine should be secured from someone simply attaching a head.
[*]NX is oft recommended in this circumstance. I'm not complete adverse to using that, but I would prefer some form of VNC as I'm currently using that on serveral other (Windows) machines on my network.
[/LIST]
Thanks for your consideration of my difficulties.

---

### Post by jeffus_il on 2008-01-29
Do you know that you can run any program on your headless machine using the ssh protocol with full security.
Open a terminal and execute command: ```
ssh -X headlessmachine
```
and 
```
 firefox
```
for example to run firefox

---

### Post by BobHope2112 on 2008-01-29
No, I can't say that I knew that.  In fact, I don't know much about SSH at all, so I will look into that.  Do you know if I can even do what I'm wanting to do with VNC?

---

### Post by jeffus_il on 2008-01-29
> **BobHope2112 said:**
> No, I can't say that I knew that.  In fact, I don't know much about SSH at all, so I will look into that.  Do you know if I can even do what I'm wanting to do with VNC?
You won't run a complete desktop on a remote machine, Only single applications, but more efficiently, especially if you don't need the desktop on a remote machine, and of course very securely. What do you need to run on the headless machine?

---

### Post by scorp123 on 2008-01-29
> **BobHope2112 said:**
>  From a Windows VNC client, I would like to connect to an Ubuntu (Gutsy) PC, and login to create a new session.   VNC doesn't work like that. If you really want that you'd have to SSH into your machine and then manually create a new vncserver session, and then connect to that one. That's why people tend to recommend NX, because it has this functionality to create a new session on demand.

VNC was designed because its creators wanted to leave a program running and then access it again from another computer, e.g. reconnect again and again to the same previous session. For that scenario it works tip top.

But if you want a new VNC session you'd first have to create one.

> **BobHope2112 said:**
>  This is only works, though, *after* I have logged into Ubuntu, and have manually started vncserver.  Works as designed.

> **BobHope2112 said:**
>  [*]Internet access to this machine is not necessary, or even particularily desired. (I have an academic interest, but it's not something to be implemented.)  You can tunnel VNC through SSH. I do that all the time and it's relatively safe. A few tutorials I just found via Google:
[http://members.shaw.ca/nicholas.fong/vnc/](http://members.shaw.ca/nicholas.fong/vnc/)
[http://users.rcn.com/tushar.manglik/](http://users.rcn.com/tushar.manglik/)
[http://www.linuxforums.org/forum/linux-security/105011-tunnel-vnc-over-ssh.html](http://www.linuxforums.org/forum/linux-security/105011-tunnel-vnc-over-ssh.html)

There are many more like this one. It's not hard once you understand the principle.

> **BobHope2112 said:**
>  [*]NX is oft recommended in this circumstance.  NX and VNC are not entirely the same and don't necessarily replace each other. I personally prefer VNC despite NX's vastly superior network performance (working in a NX session feels like being logged in locally!) whereas with VNC you have to do some fine tuning with various compression settings to even get remotely close to NX's performance. But VNC has one cool feature: A sudden disconnect won't kill your running programs; e.g. when you reconnect again all your programs will still be there, happily doing whatever they needed to be doing regardless if you're connected or not. NX claims to have this feature too but according to my experience it doesn't work so reliably well as in VNC. I very often have troubles reconnecting to a NX session, whereas in VNC it works without efforts. Also VNC is way easier to setup. Not that NX is hard to setup ... but VNC is easier by a wide stretch.

---

### Post by scorp123 on 2008-01-29
> **jeffus_il said:**
> Do you know that you can run any program on your headless machine using the ssh protocol with full security.
Open a terminal and execute command: ```
ssh -X headlessmachine
```
and 
```
 firefox
```
for example to run firefox .... But a sudden disconnect (e.g. sudden change of IP address every once a few hours ... as it may very well happen with ADSL connections!) will kill your session and take all your data to Nirvana. Too bad if you were doing something important in that moment ....  Besides: Working with X11 applications that way is slow like hell.

In that regard VNC --or rather: VNC over SSH if you are connecting over the Internet-- is clearly superior ... a sudden disconnect just disconnects you but it won't kill your applications, and whatever you were doing will still be there, waiting for you in your VNC session. So you just reconnect again and continue ... Also: VNC offers several options for data compression so the performance should be higher than running a program via "ssh -X".

Just my 0.05€ :)

---

### Post by jeffus_il on 2008-01-29
If [BobHope2112]("http://ubuntuforums.org/member.php?u=490563") needs to run one application at a time and does not need a remote desktop, there is no setup, maybe only to install the "openssh" server, I think mine was installed by default, and since he does not require internet access, I guess tunneling is not necessary, I think he should try to open an  application on his headless machine through ssh and see if that suits him, If not he can always try the more complex alternatives. I guess the real question is what does he need?

---

### Post by scorp123 on 2008-01-29
> **jeffus_il said:**
>  If he needs to run one application at a time and does not need a remote desktop ...  True .... But I'd only recommend that on a LAN.

> **jeffus_il said:**
>  I guess the real question is what does he need?  I think he already has plenty of pointers and things he can try out ... VNC-over-SSH, VNC, ssh -X ..... Whatever he needs I guess one of the methods suggested will suit him :)

---

### Post by jeffus_il on 2008-01-29
> **scorp123 said:**
> True .... But I'd only recommend that on a LAN.

 I think he already has plenty of pointers and things he can try out ... VNC-over-SSH, VNC, ssh -X ..... Whatever he needs I guess one of the methods suggested will suit him :)
  He states that he is on a LAN, in his post:
> Internet access to this machine is not necessary, or even particularily desired. (I have an academic interest, but it's not something to be implemented.)

---

### Post by BobHope2112 on 2008-01-29
[QUOTE=jeffus_il]You won't run a complete desktop on a remote machine, Only single applications, but more efficiently, especially if you don't need the desktop on a remote machine, and of course very securely. What do you need to run on the headless machine?[/QUOTE]
Really anything that can be run locally. The machine is basically to tinker with, but I don't have the room to set it up with it's own "head," or on a KVM.

[QUOTE=scorp123]I think he already has plenty of pointers and things he can try out ... VNC-over-SSH, VNC, ssh -X ..... Whatever he needs I guess one of the methods suggested will suit him:[/QUOTE]
Indeed.  I had been hoping that I could (mostly) set it up like the other Windows machines here, but it appears that I will have to retrench. Thanks guys, you've given me perspective.

---

### Post by jeffus_il on 2008-01-29
Bob, 
I hope we are not confusing you with our posts, Start with ssh, it will open a terminal on your headless, type a command, try xclock, you can do anything you could do locally. See if you like it and if it satisfies your needs, if not, post again, the forum will help you with the next step, Good Luck!
Jeff

---

