---
title: "Can't connect to Internet... help! :("
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by ramcosca on 2006-06-04
Hello. :mrgreen: 

I found out about Ubuntu yesterday, while listening to the live podcast some guys from my old college do every month ([iWannabes]("http://rfatoday.explorercompany.com/?cat=12")). It really called to my attention, so I decided to download it.

I burned it and am running it as a Live disc on a laptop I have here at home. The problem is, I just can't really get it to connect to the Internet. Here at home we have a [2Wire]("http://www.2wire.com") [Homeportal 1000SW]("http://www.pcliquidations.com/ais/item_images/homeportal1000sw.JPG") that was provided by my [DSL service]("http://www.dmaxpr.com"). I haven't even tried connecting wirelessly, only trying wired. For wireless I use a USB Wi-Fi adapter, which would make things a little bit more complicated.

What do I need to do to connect it to the Internet? I have searched the forums and have found nothing that could help me with this. Maybe I'm not searching right. :confused: 

Any help will be appreciated! Thanks in advance.

---

### Post by sherlock-holmes on 2006-06-04
[QUOTE=ramcosca]Hello. :mrgreen: 

I found out about Ubuntu yesterday, while listening to the live podcast some guys from my old college do every month ([iWannabes]("http://rfatoday.explorercompany.com/?cat=12")). It really called to my attention, so I decided to download it.

I burned it and am running it as a Live disc on a laptop I have here at home. The problem is, I just can't really get it to connect to the Internet. Here at home we have a [2Wire]("http://www.2wire.com") [Homeportal 1000SW]("http://www.pcliquidations.com/ais/item_images/homeportal1000sw.JPG") that was provided by my [DSL service]("http://www.dmaxpr.com"). I haven't even tried connecting wirelessly, only trying wired. For wireless I use a USB Wi-Fi adapter, which would make things a little bit more complicated.

What do I need to do to connect it to the Internet? I have searched the forums and have found nothing that could help me with this. Maybe I'm not searching right. :confused: 

Any help will be appreciated! Thanks in advance.[/QUOTE]


configure the network-manager and use DHCP to connect wired if u dont have a static ip...

you could install network-manager-gnome for wireless stuff...and then reboot...

---

### Post by cromestant on 2006-06-04
Does this "wired"conection use the ethernet card? or is it also a usb adapter..?

If this is an ehternet, then you must check wether or not your ethernet card was "installed"by ubuntu, you could do an : "sudo lsmod" to see wether or not the module for the card is up, or just ifconfig. If you have something like eth0 then you are good to go, if you have just the "lo"card then you've got to get the card working first.

If the card is working then you mus see wether you can just get an ip address with DHCP, which you can do on the network config utility System/administration/networks.

If you dont have dhcp then in that configo you must manually configurate the network parameters, which is pretty easy, just like in windows and mac.

---

### Post by ramcosca on 2006-06-04
I'll try to do what sherlock mentioned. [Edit] How do I install that? How do I find it?

As for cromestant's: I think it's an integrated card, it's a laptop. No PCMCIA card, no USB ethernet. It's the default slot that comes on laptops.

Question: how do I do a "sudo lsmod"? This is the first time I've touched a Linux system. 

It does show the eth0 you mentioned. I did get the IP and Subnet from the Networks app, entered it in the Network Settings > Interface Properties dialog boxes. Still, nothing happens. FireFox cannot detect a connection to the Internet.

---

### Post by roachk71 on 2006-06-04
Do you have the DNS addresses from your service provider? This has to be entered too, about half the time, especially if you're using a static IP address.

If this is a cable modem connection, leaving the DNS fields blank (for automatic detection) with DHCP should work, but some providers require that information anyway. And if you don't have a router (a direct PC-to-DSL connection) try installing the packages pppoe and pppoeconf (Synaptic can help you there.) Hopefully they're on the CD.

Whoa! Looks like you do have a router!! Oops...

Some users have had trouble with networking from the live CD, as well.

---

### Post by ramcosca on 2006-06-04
Uhm...
I was browsing through the 2Wire and found the 'broadband link details'. These include (edited some for obvious privacy reasons):
    
> DSL Connection Details 
DSL Line (Wire Pair):  Line 1 (inner pair) 
Protocol:  G.DMT 
Downstream Rate:  512 kbps 
Upstream Rate:  256 kbps 
Channel:  Interleaved 
Current Noise Margin:  38.0 dB (Downstream), 30.0 dB (Upstream) 
Current Attenuation:  31.1 dB (Downstream), 18.0 dB (Upstream) 
Current Output Power:  18.7 dB (Downstream), 8.0 dB (Upstream) 
DSLAM Vendor Information:  Country: {0} Vendor: {GSPN} Specific: {700} 
PVC Info:  0/35 
 
Internet Connection Details 
Connection Type:  PPPoA  
Username:  the username
Internet Address:  numbers
Subnet Mask:  numbers 
Default Gateway:  numbers 
Primary Domain Name Server:  numbers
Secondary Domain Name Server:  numbers 

Domain:   
Maximum Transmission Unit (MTU):  a number 
Gateway Ping:  Successful  
DNS Communication:  Successful  
Configuration Server Post:  Successful  

Which of these do I need to put into the settings for it to work?

---

### Post by ramcosca on 2006-06-04
[QUOTE=sherlock-holmes]you could install network-manager-gnome for wireless stuff...and then reboot...[/QUOTE]Ok, so I learned how to install this, but couldn't. It says I have to download some stuff from the Internet... and I have no connection to it! ](*,)


[Edit]
There's light at the end of the... network cable. The laptop appears as being connected to the router thing... but it doesn't connect to the Internet through Firefox. Any suggestions?

---

### Post by ramcosca on 2006-06-04
Uhmmm... so, yeah, nevermind. I rebooted the system and it connected like nothing had happened. Thanks for all the help, guys.

---

### Post by sherlock-holmes on 2006-06-04
[QUOTE=ramcosca]Uhmmm... so, yeah, nevermind. I rebooted the system and it connected like nothing had happened. Thanks for all the help, guys.[/QUOTE]


sorry was kinda away for some time...

now that you have connection go ahead and install network-manager-gnome....

```
sudo apt-get install network-manager-gnome
```

that will get you the nm-applet too .... 

here you will get some info ....
[http://doc.gwos.org/index.php/Category:Wireless](http://doc.gwos.org/index.php/Category:Wireless)

---

