---
title: "Belkin Wireless Adapter cannot see internet"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by unclescotty on 2007-01-05
Hi,

I am using the Belkin Wireless Adapter with Ubuntu- Dapper Drake, but the adapter cannot see my wireless internet from the router. :confused: 

I tried following the hack in Ubuntu Hacks, but it didn't do the trick.

Can someone help me get my desktop online?

Thanks, US

---

### Post by mahy on 2007-01-05
How about giving more details? The output of 'iwconfig' command and parameters of your wireless network, please. :cool:

---

### Post by unclescotty on 2007-01-05
iwconfig says 

lo no wireless extensions

eth0 no wireless extensions

wlan0 Auto: Access Point: Not-Associated
         Link Quality:0 Signal Level:0 Noise Level: 0
         Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
         Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions

As far as the network goes, I have a Belkin 54g wireless router. A Belkin Wireless G USB Network Adapter. The XP laptop on which I am writing this post is receiving its wireless signal from that router, so I know the signal is good. The green light is on in the USB adapter, but I cannot ping or load websites.

Is this helpful? US

---

### Post by mahy on 2007-01-06
It seems the wifi adapter is perfectly recognized by the system. Just gimme details about your wifi network, pls. WEP? WPA? DHCP yes or no?

---

### Post by unclescotty on 2007-01-06
This is what I saw when I logged into my router:

 WAN > Connection Type

 	
 	Select your connection type:
	Dynamic
 	A Dynamic type of connection is the most common. If you use a cable modem, then most likely you will have a dynamic connection. If you have a cable modem or you are not sure of your connection type, use this.

Security Mode 	64-bit WEP

DHCP Client List

  	
This page shows you the IP address, Host Name and MAC address of each computer that is connected to your network. If the computer does not have a host name specified, then the Host Name field will be blank. Pressing "Refresh" will update the list.
 
IP Address 	Host Name 	MAC Address
192.168.2.2	cuatro	00:90:4b:96:a9:19

I just noticed that the host name is cuatro, and I named my UBUNTU box cuatro as well. Might that be causing some kind of conflict?

Thanks, Scott

---

### Post by unclescotty on 2007-01-08
Mahy (or anyone else),

Can you help me resolve this problem?

Thanks, Scott

---

### Post by unclescotty on 2007-01-10
Help!! Someone!! Please!!! ](*,)

---

### Post by moshuptrail on 2007-01-10
First.  It should work.  I am using the exact same Belkin wireless card, and it works BETTER than it did under XP where the driver was flaky at best.  I am using 128-bit WEP.

I was successful using the gnome GUI utility for Network settings.  Have you tried that?
I think you may be making this too hard for yourself.

If you are still struggling with this, post again and we can compare congifurations.

---

### Post by unclescotty on 2007-01-11
Hi, Thanks for your reply.

So, should I change my security setting from 64-bit WEP to 128-bit WEP? I believe my ISP told me 64-bit WEP. As long as it doesn't effect my laptop's ability to see the wireless network, I am happy to do that.

Also, as far as the GNOME gui utility for network settings, I don't know what I need to do. How do you access the GUI? What are the proper settings?

Thanks much, Scott

---

### Post by unclescotty on 2007-01-15
Hi moshuptrail,

Are you there? Can you help me???:confused:

---

### Post by unclescotty on 2007-01-20
What is with this list? People say they will help, and then they disappear?! How can someone get help here????????????? ](*,) 

-Scott

---

