---
title: "Remote access ..."
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-05-08
My home PC dual boots both Ubuntu Feisty and Windows XP.  I have some questions about remote access:

1)  I've tried to VNC to my Ubuntu Linux desktop and it seems quite a bit slower than when I remote desktop to Windows XP.  Is this typical?  Is RDP inheriently faster than VNC?

2)  How about Telnet?  How can one setup a Telnet server so one can remotely get a command prompt?

3)  Does Ubuntu support VPN - aka say if from home I want to Remote Desktop via a VPN channel to a Windows 2003 Server?


Any other neat remote access features?

Thanks

Carl

---

### Post by thnogueira on 2007-05-08
2 - Do not use telnet. Use ssh.

3 - Yes, linux is vpn capable. Maybe [http://ubuntuforums.org/showthread.php?t=91249]("http://ubuntuforums.org/showthread.php?t=91249") can help you.

4 - Take a look on [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Login_via_XDMCP]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Remote_Login_via_XDMCP").

To be honest, I don't think you are going to find anything as good as ms remote desktop soon.

Good luck.

---

### Post by byenary on 2007-05-08
ssh is what you need, install openssh-server on the ubuntu, than you can connect from either linux or windows, for windows i use something like ssh secure shell client..

---

### Post by gunthr on 2007-05-08
I use NoMachine NX for my remote desktop and it is very fast. I use it to conect to a Fedora server and it works great. I haven't had time to install it on my Ubuntu server yet, but I will definately use that instead of VNC just based on the speed alone. It runs over ssh, so security isn't an issue either.

---

### Post by cwmoser on 2007-05-08
> **gunthr said:**
> I use NoMachine NX for my remote desktop and it is very fast. I use it to conect to a Fedora server and it works great. I haven't had time to install it on my Ubuntu server yet, but I will definately use that instead of VNC just based on the speed alone. It runs over ssh, so security isn't an issue either.


I downloaded and looked at NoMachine NX.  Whew, to evaluate that is going to take a lot of effort.  There is no quick setup documentation.

Any words of wisdom?  Is NoMachine NX worth a big investment in learning time?

Carl

---

### Post by mayodreams on 2007-05-08
> **cwmoser said:**
> I downloaded and looked at NoMachine NX.  Whew, to evaluate that is going to take a lot of effort.  There is no quick setup documentation.

Any words of wisdom?  Is NoMachine NX worth a big investment in learning time?

Carl

I used nomachine for remote administration of 2 headless servers running 6.06 for about 6 months now and I have been very happy with it.  Yes, setup is kind of a pain, but it is VERY fast, and the client works on linux, windows, and mac os x.

---

### Post by cwmoser on 2007-05-09
Thanks. I followed your recommendation to invest in the time and effort to install ssh and NXServer. NXServer is definitely worth the effort and superior to VNC.

One issue I had with NXServer is that my main account on my system would not allow me to log in. I got NXServer to work by adding a new user via nxserver. With the free NXServer, we can only have two accounts but that is no problem.

Like you mentioned, NXServer does not take over the desktop but instead creates another user session -- I like that over the way VNC takes control of the existing desktop.

NXServer is a really nice addition for Ubuntu. Its also a brilliant marketing idea to allow for free 2-user access. Now that we have experience with NXServer, we might find some commercial applications that will need to purchase the ful version. Thanks for the recommendation.

Carl
Edit/Delete Message

---

### Post by RavUn on 2008-07-08
I'd like to setup NoMachine so I can access my linux computer from my windows computer.  The linux computer I'm trying to access is connected through a router.  I was going to make a host name using dyndns but the IP address I'm finding is to my router.  Is there a way to use NoMachine if my remote computer is behind a routher without having to do a lot of extra work with ports and a lot of other stuff I don't understand?

---

