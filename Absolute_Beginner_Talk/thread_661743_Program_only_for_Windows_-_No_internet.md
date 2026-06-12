---
title: "Program only for Windows - No internet"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by Yuliya on 2008-01-08
I hae just installed ububntu on a new computer, but the internet cds are only for Microsoft and I cant get Wine because I have no internet yet. Is there any way this problem can be solved without internet?

I have a ADSL connection from T-Com (German telephone provider)

---

### Post by frup on 2008-01-08
The CD isn't so important if you know the information it provides. Do you have a USB or Ethernet ADSL modem/router.

---

### Post by Yuliya on 2008-01-08
Ethernet. the cd comes with a program and so far, we've only been able to connect through that program

(another computer I had also used Ubuntu, but then the computer inmediatly recognised the connection - without program or passwords ... but this time its not like that)

---

### Post by frup on 2008-01-08
The program should merely configure windows to understand what it is doing them.

If you have not changed the routers configuration it should be as simple as setting an internal IP, subnet mask and gateway. Do numbers such as 255.0.0.0 and 192.168.1.2 look familiar at all?

---

### Post by Yuliya on 2008-01-08
those numbers dont look familiar at all and I dont understand much of what you say there. So can I run internet without the T-Com software?

and If so, how do I configurate it? (everythign in details and I need to write this down and then go home and try it by myself)

---

### Post by Sef on 2008-01-08
> Ethernet. the cd comes with a program and so far, we've only been able to connect through that program

(another computer I had also used Ubuntu, but then the computer inmediatly recognised the connection - without program or passwords ... but this time its not like that)

If you have asdl that should be automatically recognized.   Have you checked out your internet card?  I wonder if it is bad or does it work with 
Windows?

---

### Post by Yuliya on 2008-01-08
It works with windows. For days Ive been struggling with the internet, and after this program it connected automatically, but I have no ideas about the codes or anything. The computer was set for wireless internet before though - does that make any difference?

I went to the company and the said they couldnt help me, as they only have support for Microsoft

---

### Post by frup on 2008-01-08
So it is wireless? Do you know which kind of card it is? It doesn't matter if you don't know as other people on the forums will be able to help you find out how. If you are able to do a non wireless internet connection an see if that works though it might help in finding out what the problem is (This means simple configuration or driver issues)

---

### Post by Yuliya on 2008-01-08
We had a wireless configuration, but we had a problem with internet and on the meantime the company gave us an Ethernet modem and we cant connect. I cannot do anything and I completely uninstalled windows, where the internet works, so I have so way of getting the information right now, as I would have to go home.

Is there any way this can be solved without internet?

---

### Post by frup on 2008-01-08
Have you configured the new router?

Try [http://192.168.1.2](http://192.168.1.2) or [http://10.0.0.2](http://10.0.0.2) in your web browser and see if that gives a password dialogue.

On the actual hardware do the lights show actual internet access is available.

How are you accessing the internet now?

---

### Post by Yuliya on 2008-01-08
Im on an internet place, about 3 streets from my house. Should I wirte that down, go back and try it?

---

### Post by benrboone on 2008-01-08
Yes, I think it can be fixed
First we need to know a few things about your setup
Do you have a wired or Ethernet connection and a wireless?
A wired connection is usually quite a bit easier to setup, if you have that i suggest we start there.
Also if possible please post your Ethernet / wireless connection info (easiest way to do this is probably by going to the terminal window and typing: ifconfig)

---

### Post by djbsteart1 on 2008-01-08
also try [http://192.168.0.1]("http://192.168.0.1") that is the default for my netgear router so it might be for others

---

### Post by Yuliya on 2008-01-08
okay, I have a Ethernet, wired, connection at the moment.
(why doesnt Ubuntu recognised it automatically this time)

thanks for the other info. Ill try it.

---

### Post by stalkingwolf on 2008-01-08
You can try this.  It may give you access to the internet , then you can fix your problems.
Go to System > Administration > Network > Hosts > find , FF02::2 ip6 All Routers > click add.

This has worked for me to establish both wired and wireless connections.

Hope this helps.

---

### Post by frup on 2008-01-08
if it is ipv6, I have no experience with that.

With a plain wired connection I personally can't see how ubuntu doesn't work. trying DHCP and static etc should get some action.... I'm intoxicated so cloudiness is setting in and I think I might resign from attempting to broaden my ego (lol). I wish you luck. I feel that it is very unfortunate when people have problems with things that should be so simple. It may be something simple and you may smack your own head or it may be something complicated where you are just unfortunate. Good luck to you and lets all hope you sort it out soon. Ubuntu is an awesome system, Personally I am not happy using any other operating system.

---

### Post by Perkins on 2008-01-08
Ok, so if I'm understanding this correctly, you have a DSL modem with an ethernet port, and an ethernet port on your computer, and you're trying to make them talk.

The configuration software that came with the modem only works on Windows.

We can work with this.

Odds are, the configuration software is just to make it easy for the average Windows user, but I have seen a few exceptions.  The first thing to do is to find out.  I would start by examining the modem.  Most of them have their default address printed on a sticker somewhere.  A goodly number have the default username and password as well.  

If it doesn't, then look through the manual which probably came with the device.  They should be in there.  

If there is no manual, then see if you can find the brand name of the device.  With that you should be able to search the internet for those three pieces of information.  Once you have them, post them here and we should be able to help you make it work.

---

### Post by Yuliya on 2008-01-12
okay here is the information you requested. I just received the new modem, definite onw, and its supposed to be wireless but it has an Ethernet connection, which I've plugged tot he computer.

eth0      Link encap:Ethernet  HWaddr 00:0C:76:76:85:B5  

          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0

          inet6 addr: fe80::20c:76ff:fe76:85b5/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:499 errors:0 dropped:0 overruns:0 frame:0

          TX packets:147 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:31639 (30.8 KB)  TX bytes:14170 (13.8 KB)

          Interrupt:21 Base address:0xb000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:132 errors:0 dropped:0 overruns:0 frame:0

          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:6600 (6.4 KB)  TX bytes:6600 (6.4 KB)



wlan0     Link encap:Ethernet  HWaddr 00:60:B3:95:2E:6C  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



wlan0:ava Link encap:Ethernet  HWaddr 00:60:B3:95:2E:6C  

          inet addr:169.254.6.90  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1



wmaster0  Link encap:UNSPEC  HWaddr 00-60-B3-95-2E-6C-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


und here are the modem details:


Speedport W 502V Typ A
Seriennummer: 607542
MAC: 001D19294793
Gerätepasswort: 294791


Please I need the help as soon as possible, as I've been without internet for more than a week now.

I was also given a connection number and password.

---

### Post by Yuliya on 2008-01-12
Pleassssseeee - I need help as I need to come to a place to get online and I cant stay here forever

---

### Post by Perkins on 2008-01-12
And I just woke up.  Patience, we do the best we can.

Ok...  Looking at what you posted, it's probably a pretty standard setup.

The address which your computer has been given is 192.168.2.100.  Since you don't say anything about having set that yourself I am assuming that the new modem is working and gave it to you.

Most modems which give that address range over DHCP have a default address of 192.168.2.1.  You can check that by using the route command in a terminal.  You're looking for the default route.  The address it points to is almost certainly your modem.

You should be able to type the modem's address into a browser and get into its configuration pages.  My German is rather rusty, but I believe that Gerätepasswort: 294791 is probably the default password.  I do not know what the default username is, and all the webpages I find about this device are in German, which I am guessing you probably read much faster than I do.  If it's new, there is probably a manual that arrived with it.  The manual would likely have this information.

The manual probably also has instructions for setting up the device through your browser.  If it does not, then I will try to find some way to help you with it, but it will not be easy.  So read the manual first.

---

### Post by Yuliya on 2008-01-13
ohhhhh thanks!!! It works now. Thank you very much,

I want to download things through the Add/Remove Application but it tells me I need a working internet connection (and as you can see I am connected) what can I do?

---

### Post by Perkins on 2008-01-13
That means that it cannot talk to the server for some reason.  Since you're posting here, and not complaining that other sites don't work, I'll assume that your DNS and everything is working properly.  So, if you click on the preferences button in the add/remove program, it should let you change which server you're using.  Try that and see if it helps.

---

### Post by ugm6hr on 2008-01-13
In Add/Remove Preferences, make sure you have the top four boxes ticked in Software Sources.  That sometimes works.

---

