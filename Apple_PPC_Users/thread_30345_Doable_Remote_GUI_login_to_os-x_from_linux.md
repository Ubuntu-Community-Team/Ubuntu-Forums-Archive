---
title: "Doable?? Remote GUI login to os-x from linux??"
date: 2005-04-28
forum: Apple PPC Users
---

### Post by rhinocervs on 2005-04-28
First post!! First time I haven't found the info I've needed on this forum  :-) 

   I am just about to be handed down a Powerbook Wallstreet II 233.  O:) Planning to up the memery to 512mg (anyone want a 32mg stick??), and put a bigger HD in. Bit too expensive though to stick a bigger processor in, and it seems the 233 is a little underweight to run os-x. This should make a nice Ubuntu box though. There are maybe a few install probs with Ubuntu but nothing that can't be overcome.

Also currently saving up for a mac mini  to dual boot os-x and linux. 

Does anyone know if it willl be possible to remote GUI login to the os-x mini from ubuntu/linux on the powerbook??? I am completely new to mac but reasonably familar with linux and windoze and prepared to put in the time to get it going.

Ideally I am looking for something that works like X -query for linux-linux or rdesktop for  linux - windows.. I've currently got a P2 96mg thinkpad running fluxbox on ubuntu base and by logging into my amd2800+ dual boot windows/ ubuntu gnome using X -query and rdesktop, this ancient laptop runs a treat.. hoping i can get the same thing going with the mac-mini on os-x and the early g3 powerbook running linux. 

Why? For travelling!!. I would have a usable linux laptop (at about AUS$300 for the upgrade) and could also take the tiny mini (without having to take a screen, keyboard etc). Hopefully I'll be able to run os-x as a client? on the laptop (at a reasonable speed) from the mini. Can it be done???? 
I've found apps like vMac (only for os??) and MacOnLinux but not sure if they'll be able to handle it. 

Can anyone point me in the right direction? Thanks.
..and excuse the ramble.. never really worked out what concise meant.. :-P

---

### Post by 23meg on 2005-04-28
i'm not sure if you can login to osx from linux, but if you can't do it in the "native" way [tightvnc](http://www.tightvnc.com/) might help you.

---

### Post by spoetnik on 2005-04-28
It is possible.

You can ssh to your OSX. Ore use vnc.
If you enable "apple remote Desktop" in your sharing prefrences you can use VNC.
Enable "Remote login" and you can ssh to your Apple.

---

### Post by rhinocervs on 2005-04-28
Thanks. Starting to think this just may work.  :-) 

I'm not at all familar with os-x though. Have you any idea whether I'll be able to configure os-x on the mini to boot up without any peripherals attached (no monitor, keyb, mouse), only with a network connection (either direct or through a router), then login remotely through the powerbook?

---

### Post by farruinn on 2005-04-28
Once you have the mini configured for remote login, vnc, whatever you decide to use, it should run fine without any peripherals, you'll just have to have some way of knowing its IP address.  Remote login services aren't enabled by default though, so I don't see any way of doing an initial configuration remotely.

---

### Post by Bug on 2005-05-06
Most of the services are configurable from the command line, including remote desktop. check out the server manuals on Apple's website, then search for the section on command line tools. This will tell you how to configure it via ssh. They have man pages too, See;

[http://docs.info.apple.com/article.html?artnum=108030](http://docs.info.apple.com/article.html?artnum=108030)


You can then use vnc4 (vnc4viewer?) to connect (has to be a vnc 4 client). You'll be able to log in right from the login window and do your thang. I got a powerbook g4 laptop with a broken LCD I'm using this exact way as a headless Media Center (head=tv, but only when watching a movie or itunes effects). 

One problem I ran into was that the powerbook's buttons on the inside of the case (which I sealed shut). I bought a powerwave conntrol (little nob that glows blue, you can use it for anyhting) that also acts as a powerbutton if you push it down. Old iMac usb keyboards have a powerbutton too. Have fun!


Bug

---

