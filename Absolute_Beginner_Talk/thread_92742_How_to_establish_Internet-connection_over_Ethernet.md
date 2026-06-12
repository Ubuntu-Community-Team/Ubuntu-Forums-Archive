---
title: "How to establish Internet-connection over Ethernet?"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by Wolf1994 on 2005-11-20
In WindowsXP I have for Internet this:

ISDN - VIA Rhine II Fast Ethernet Adapter
PPP over Ethernet protocol
Internet protocol TCP/IP
packet planner QoS

Attributes:
Get IP-adress automatically
Get DNS-server automatically

Besides I know:
Physical net-adress
IP-adress
subnet mask
(sorry for inaccuracy - I tried to pick the right translation from Russian)

and at last:
my login
my password

How I can establish connection using above information? I found panel with the Ethernet-connection but don't found where to enter my login/password... Please point me full sequence of actions to perform the Internet-connection. I talked about liveCD-version - if it does matter.

---

### Post by adwait on 2005-11-20
If you use pppoe, try using
```
sudo pppoeconf
```

It will ask you some questions including your username/password and should get you connected to the internet.

---

### Post by sarah_b on 2005-11-20
All I had to do is go to: System > Administration > Network > I clicked on my Ethernet connection which was detected, and then chose "activate", then entered my user name and password and that was it. 

I think I was lucky, I see very many post that ubuntu users are having problems connecting.

---

### Post by Wolf1994 on 2005-11-20
Thanks. I try it one more time.

> All I had to do is go to: System > Administration > Network > I clicked on my Ethernet connection which was detected, and then chose "activate", then entered my user name and password and that was it.
I tried to do this in that way but "Activate" was unaccessable.

---

### Post by sarah_b on 2005-11-20
Try looking at this post: 
[http://www.ubuntuforums.org/showthread.php?t=92633]("http://www.ubuntuforums.org/showthread.php?t=92633")

You may have to install and use "ndiswrapper"

---

### Post by Wolf1994 on 2005-11-20
Thanks all very much. I made it! Now I type this under Ubuntu (LiveCD)! pppoeconf - helped! There's only one problem was - to locate the "Terminal". But it not taked to much time to resolve.

Last question regarding Internet:
How I can monitor traffic? In Windows its was an icon in system tray...

---

### Post by danne on 2005-11-20
[QUOTE=sarah_b]Try looking at this post: 
[http://www.ubuntuforums.org/showthread.php?t=92633]("http://www.ubuntuforums.org/showthread.php?t=92633")

You may have to install and use "ndiswrapper"[/QUOTE]

nvm

---

### Post by sarah_b on 2005-11-20
[QUOTE=Wolf1994]Thanks all very much. I made it! [/QUOTE]

I'm glad you were able to make a connection and I hope you enjoy ubuntu as much as I do

sarah

---

### Post by adwait on 2005-11-20
[QUOTE=Wolf1994]Thanks all very much. I made it! Now I type this under Ubuntu (LiveCD)! pppoeconf - helped! There's only one problem was - to locate the "Terminal". But it not taked to much time to resolve.

Last question regarding Internet:
How I can monitor traffic? In Windows its was an icon in system tray...[/QUOTE]
Right click on the panel and select Add to Panel>Applet and then select network mintor (or something like that).

---

### Post by Wolf1994 on 2005-11-20
Thank you. That's all I wished to know.

---

### Post by sarah_b on 2005-11-20
[QUOTE=danne]nvm[/QUOTE]

tdms

---

