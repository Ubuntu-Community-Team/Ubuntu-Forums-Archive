---
title: "Wireless problems with an IBM laptop and a Linksys router"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Ulysses on 2006-07-09
Hello,

Laptop IBM thinkpad X22
128MB RAM
Pentium 3
Despite the speed and the RAM, 6.06 runs very, very well
Router Linksys 2.4GHz 802.11b model BEFW11S4 V.2
Wireless card Linksys 2.4GHz 802.11g Notebook adaptor

Yes, I have access to the internet through a standard connection. But that means having to be in the basement all of time. I only want to be down here some of the time.

Yes, I have a b router and a g card - the router and the laptop were a handmedown and there was no card and the only card I could buy was a g. When there was windows on the latop there wasn't an issue. I don't think there should be an issue with Ubuntu - but I can't get it to work, either, so who knows?

Yes, the driver for the card works. No problems, there. I don't think.

Yes, I have followed the troubleshooting guide as best I can but I am still getting nowhere with making a connection. The router works, all of the lights are on for the connections.
The Power light is on.
The WLAN link light is on.
The WLAN Act light does come on but doesn't stay on. Does that mean that the router is not broadcasting?

Someone, please help.

And in reference to the excellent post about who should use Ubuntu, I WANT to use the command line. I just want to be pointed in the right direction.

RAR

---

### Post by OpsVentus on 2006-07-09
Hello Ulysses,

First, it dosn't matter that your card is g becauss it can switch back to b if needed. Like in your case.

Second, on the most routers the Ack light will flash when data is being send/received so it dosn't have to be on all the time. So it's normal that, that light is off now.

But to help you further, I will need more information. 
1: Information on the network. Do you use WEP or WPA or no encryption? DHCP or static?
2: (And this is the part where you can dive into the terminal) Start the terminal and type these command's:
#iwlist scan
#iwconfig
Then comeback here and tell us what the output is.
(you can select the text, right mouse click, copy and then paste in the message here)

Cheers,
Bart.

ps.
iwlist scan, gives a list of the networks found by your networkcard
iwconfig, tells us what the card is connected to now

---

### Post by Ulysses on 2006-07-09
Hey

Thanks for replying so quickly
I figured that it wouldn't be an issue with a g connecting to a b, but I wanted to put as much information as possible in my post. And I felt silly talking about the little lights, but d****t, I was getting frustrated.

And to answer the questions, here goes...
1: Information on the network. Do you use WEP or WPA or no encryption? DHCP or static?
A: No encryption. When I was learning how to set it up I decided not to encrypt anything in case I screwed something up. Once I got it set up I never went back to encrypt it. And it is DHCP, not a static IP.
2: (And this is the part where you can dive into the terminal) Start the terminal and type these command's:
A: Wheee - terminal mode. Here we go. Results from:
#iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

#iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

I'm still messing around with it, going through the wireless troubleshooting, hoping that I might strike it lucky.
Somehow, I've managed to freeze the machine 4 times now, twice when I was trying to reply to this thread using Evolution.

Thank you, thank you, thank you.
My next step is to try and upgrade my desktop to 6.06. THAT crashed 3 times yesterday.
And if it wasn't for these two computers this weekend, I could be cutting my lawn or digging a garden for my wife. Thank you, ubuntu, for setting me free....

RAR

---

### Post by OpsVentus on 2006-07-11
#iwlist scan
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
irda0 Interface doesn't support scanning.
eth1 No scan results
sit0 Interface doesn't support scanning.

Tells me that eth1 is your wireless networkadapter.

"No scan results" tells me that the networkadapter was not able to find an wireless network.

"eth1 IEEE 802.11b/g ESSIDff/any Nickname:"Broadcom 4306"
Mode:Managed Access Point: Invalid Bit Rate=1 Mb/s"

"Nickname:"Broadcom 4306"" is strange if you got an linksys networkadapter.
Check your device manager and lookup your networkadapter to see what ubuntu thinks it is.

If your planning to upgrade to 6.06 you might want to do this first, becaus this can fix your problem.

So my advise:
Do a "fresh" install but keep your /home, this way you keep most of your settings.
Then check if "#iwlist scan" still give the same output.

Good luck.

---

