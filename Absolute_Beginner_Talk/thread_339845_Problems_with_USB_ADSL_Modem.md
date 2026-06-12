---
title: "Problems with USB ADSL Modem"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by ghicking on 2007-01-16
I have used the help from Forums to connect my new Ubuntu 6.1 to the internet via a speedtouch 330 USB ADSL modem.  Var/Logs/Messages confirms the connection is made on bootup.  Neither Firefox nor Evolution can see the connection.  They are connected to the ethernet loop 'lo'.  In Firefox preferences/Advanced, the usb link is not in the pulldown list of connections - only 'lo' is available.  How can I make Evolution and Firefox recognise the connecction.  I noted another thread outlining a problem with USB ports in general - any connection?

---

### Post by deadgobby on 2007-01-16
[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)
It may take some work to get it going. How ever, that is why copy and paste can be so handy dandy. 
Gobby

---

### Post by ghicking on 2007-01-16
Thanks for the advice - but it was that help link that got me to the point where the modem is connected to the internet. But,  the software doesn,t recognise the connection - see original message.

---

### Post by deadgobby on 2007-01-16
Well I am dumb founded. 
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)
What country in this vast world do you live in. The reason why I ask, because that may be the source of the problem.
Gobby

---

### Post by ghicking on 2007-01-16
Thanks Gobby.  I'm in the UK, mate.  Incidentally, I can't ping either.  Does this suggest the Ubuntu doesn't recognise that the connection it has made is an internet one?  When I put 'lsusb' in a terminal, I get the usb list including the Thomson Alcatel USB ADSL Modem.
By the way, my windows IE is having trouble finding your second link.  I'll try again in a minute.

---

### Post by deadgobby on 2007-01-16
OK that does mean some thing liven in the UK.
[https://help.ubuntu.com/community/UKSpeedtouchDSLHowTo](https://help.ubuntu.com/community/UKSpeedtouchDSLHowTo)
Did you try the above link.

---

### Post by teaker1s on 2007-01-16
furthest I got with thompson speedtouch 330 at christmas was connected pppoa, but ARP error which is bug in pppd package-I looked round and couldn't find a solution

---

### Post by ghicking on 2007-01-18
Thanks Gobby and Teaker1s.  I'm back to square one.  Var/log/message says I'm connected.  No other part of the software recognises it.  Where do I go from here?  I hopeit's not back Microsoft.](*,)

---

### Post by teaker1s on 2007-01-18
think you'll find it's ARP ISSUE my thread below
[http://ubuntuforums.org/showthread.php?t=325805]("http://ubuntuforums.org/showthread.php?t=325805")

can't sit in front of the pc I tried it on as 200 miles away, but if i remember it was either demsg or opening /var/log/messages that showed the problem

---

### Post by tyler_roach on 2007-01-18
ghicking.

Try going to System> Administration > Networking, then double click on your Ethernet adapter, and uncheck the box that says "enable this connection." If that doesn't work, (for some reason it would keep re-checking itself with me) try disabling your network card in your BIOS.  I'm assuming, of course, that you're not using it.

---

### Post by laidback on 2007-01-18
I sense that your modem isn't working correctly, which may be to do with the installation/microcode.

I used to use one of these modems when I first connected to the internet and after some playing I did get it to work. The source of the working solution was [http://steve-parker.org/speedtouchconf/](http://steve-parker.org/speedtouchconf/)

Now there was another issue. My modem is black, so I followed the black modem instructions from Steve's site, no go, once I followed the grey modem instructions all was sweetness and light. I've had it running in Mandriva but not Ubuntu. The black/grey issue may affect you too. I have a feeling that you may be using the wrong microcode. See Steve's site and further references.

Another tip. I used DNS rather than DHCP for the connection. I still do even after moving to a router/modem and Ubuntu which seems to want to install itself as DHCP, I use the Network Settings to make my own connection replacing the default.

I was advised to ditch the Speedtouch which after saving up for a router/modem I did. And what good advice it was, if you can afford it it's the way to go. So much better and a firewall built in as well. Since moving to router/modem solution I have used several distros, all of which connected quite easily. The most I have to do is select DNS and type in my DNS addresses. I've used Fedore, Damn Small Linux, Mandriva, Knoppix, Ubuntu 6.06LTS, Ubuntu 6.10 et al. All went onto the internet without the issues created by the Speedtouch. 

I paid £32 for my router/modem. Not an expensive one but I'm very pleased with it.
Treat yourself.

Laidback

---

### Post by tyler_roach on 2007-01-18
I don't think steve's script will work with Ubuntu; at least I couldn't get it to work with me. The only tutorial I could get to work was:
[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html)

By the way, ghicking, when you say that var/log/messages says that you're connected, what EXACTLY does it say? Note: I'm currently using the same modem with Edgy, and I think I might have had the same problem.

---

### Post by laidback on 2007-01-18
I used to use one of these modems when I first connected. At the time I used Mandriva. Solution to my problems was found at 
[http://steve-parker.org/speedtouchconf/](http://steve-parker.org/speedtouchconf/)  .
However the best advise was to buy a router/modem.

You may find that your microcode is wrong. Speedtouches come in black or grey. Mine is black and I followed the instructions accordingly. Still couldn't get it to connect. So I decided to use the instructions for the grey modem. No problems, off it went and I used it for some time. It appears that the different coloured modems use different code, or are supposed to!

If you can afford it buy a router/modem. Mine cost me £32 and I've not looked back since.

---

### Post by corella on 2007-01-18
I never saw ubuntu before today. got a hardcopy at the sydney Linux conf. Put it on my old laptop about 1 hour ago. On it now ( running  Motorola Surfboard on optic cable) runs at 12MB. It did the same thing to me that it did to you. My fix was new Driver for Linux, the windows driver sees it but the window is CLOSED. I have a long night ahead getting the rest of the drivers I need.

---

### Post by old_dog on 2007-01-18
I have been trying to connect to NTL via speedtouch adsl I gave up the other day and ordered 2port adsl2/2+ modem router cost me 20 quid from e-buyer arrived 2 hours ago straight up and away within an hour....have a problem with speed but I'm sure that will be easy to resolve!
Cheers

---

### Post by laidback on 2007-01-18
Apologies for all the above repitition etc.....didn't think my posts were being accepted!! my fault.

---

### Post by xpod on 2007-01-18
> I have been trying to connect to NTL via speedtouch adsl I gave up the other day and ordered 2port adsl2/2+ modem router cost me 20 quid from e-buyer arrived 2 hours ago straight up and away within an hour....have a problem with speed but I'm sure that will be easy to resolve!
Cheers

I`m with NTL myself but i got some NTL cable modem off them for that particular connection..
I`ve watched many a struggling speedtouch 330 user and always thanked myself lucky that NTL did`nt hand them out......seems i was wrong.

You could always try and get the NTL modem off them instead,it works great without any configuring......usb or ethernet works fine.

EDIT:....never read it properly...doh.Glad you got it sussed

---

### Post by ghicking on 2007-01-21
Tnaks to everyone who has helped.  I've decided to do the sensible thing and buy a proper router/modem.  You never know, I might be asking for help on that later!  I'll post message to let you know if I'm up and runnibg.  Thanks again!
Graham

---

### Post by xpod on 2007-01-21
Good luck Graham.

Graham:D

---

### Post by ghicking on 2007-04-20
Thanks for your support, everyone.
I have taken the easy way out and bought an ethernet modem router and it works fine.

Thanks for your support - I'll no doubt need it again!

Graham

---

### Post by =CrAzYG33K= on 2007-04-29
Couldn't get my USB ADSL modem work as well  .. :(
Any manual config help for a Conexant type ADSL modem?

---

