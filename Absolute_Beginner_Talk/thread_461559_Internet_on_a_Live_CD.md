---
title: "Internet on a Live CD?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Madejyalook on 2007-06-01
I got Ubuntu to run off the live CD after several tries. Now I'm wondering, am I able to get online with just the live disk or do I need to install it? And if I can, how do I do so?
Any help is appreciated. :)

**Edit:** I'm still using the live CD, I have a DSL ethernet connection with an Intel 2200 modem, and I still can't get it to connect. I tried looking at [this]("http://ubuntuforums.org/showthread.php?t=183062&highlight=pppoe") thread, but it says I have to install several things, and if it's running off a CD is there anywhere for it to go? I've also seen something about "sudo pon dsl-provider", but that didn't work either. And, stupid question, am I supposed to put in my dsl provider, or type literally "dsl-provider"?
Any help would be greatly appreciated with this.

---

### Post by abn91c on 2007-06-01
depend on how you normally access the internet, if cable modem ubuntu should detect it, if you have a wireless card you may need to do a manual network setup for drivers SSID, etc

---

### Post by Madejyalook on 2007-06-01
> **abn91c said:**
> depend on how you normally access the internet, if cable modem ubuntu should detect it, if you have a wireless card you may need to do a manual network setup for drivers SSID, etc

Ack, sorry, forgot about that. I have a DSL connection.

---

### Post by Hendrixski on 2007-06-01
hhhmmm.  Normally when I ran the liveCD it just worked and the internet was up... no configuration required.

If your DSL provider requires that you provide a password, then under System-->administration-->network there's a few things you can tinker with to provide that password.

---

### Post by stmiller on 2007-06-01
Live CD defaults to DHCP / automatic network setup through the wired connection. When it boots up, you can do other configurations if you don't use DHCP.

---

### Post by Madejyalook on 2007-06-05
Bump. See edit.

---

### Post by irish_flu on 2007-06-05
Assuming that you have Windows set up on the machine when you're not booting from the Live CD, how is the networking set up on it?  Does it automatically receive an IP address, or have you assigned a "static" IP address to it?

Also, it might be helpful to note whether you connect through a separate router, or directly through your DSL modem.

---

### Post by Madejyalook on 2007-06-05
> **irish_flu said:**
> Assuming that you have Windows set up on the machine when you're not booting from the Live CD, how is the networking set up on it?  Does it automatically receive an IP address, or have you assigned a "static" IP address to it?

Also, it might be helpful to note whether you connect through a separate router, or directly through your DSL modem.

It automatically receives an IP address, and it's directly through the DSL modem.

---

### Post by God_of_Belac on 2007-06-06
I have this same question.  I made a live CD to test ubuntu out and got everything relevant to work except for the internet.  

I have DSL, an At&t 2701HG-B modem, set up with a wireless network that's wep encrypted.  I've input the name and key into the network connections utility, and it claimed to be connecting but never actually connected.  I think it automatically receives an IP address, as I never assigned it one.

Thanks for any help you can provide.

---

### Post by nutz on 2007-06-06
> **Madejyalook said:**
> I got Ubuntu to run off the live CD after several tries. Now I'm wondering, am I able to get online with just the live disk or do I need to install it? And if I can, how do I do so?
Any help is appreciated. :)

**Edit:** I'm still using the live CD, I have a DSL ethernet connection with an Intel 2200 modem, and I still can't get it to connect. I tried looking at [this]("http://ubuntuforums.org/showthread.php?t=183062&highlight=pppoe") thread, but it says I have to install several things, and if it's running off a CD is there anywhere for it to go? I've also seen something about "sudo pon dsl-provider", but that didn't work either. And, stupid question, am I supposed to put in my dsl provider, or type literally "dsl-provider"?
Any help would be greatly appreciated with this.

The live CD has my network drivers built in. So when I boot to it the internet is already connected and ready to go. Perhaps if that is not the case with you then it does not have the drivers your NIC needs...

---

### Post by NeoLithium on 2007-06-06
For those that use DSL with a username and password, in the liveCD environment you can simply open the terminal and type ```
sudo pppoeconf
``` and fill in the options, it's what I had to do with my old ISP.  As for the wireless, I have no clue about that, so hopefully someone else can lend a hand with setting it up for you all :)

---

### Post by Kiwilad on 2007-06-07
OK, I'm also very new to this and have only just managed to get the live CD to work on the last 2 occasions. I still haven't worked out how to access the internet but I'm hopeful regarding the previous comment where you have to type code into the terminal.... now here comes the real newbie question.... how do I open the terminal?

---

### Post by NeoLithium on 2007-06-07
Go into Applications -> Accessories -> Terminal

It'll run you through the setup for PPPOE connections, where you enter your username and password for internet access.

---

### Post by God_of_Belac on 2007-06-07
I attached an ethernet cable to my modem, went to the terminal and typed sudo pppoeconf, and got the following:

"I found 2 ethernet devices:  Eth0  Eth 1.  Are all of your ethernet devices listed?  If no, modconf will be started."

Choosing no did not launch modconf.
Choosing yes led to it trying to find ppoe access concentrator.  It couldn't, and displayed

"Sorry, I scanned 2 interfaces, but access concentrator did not respond.  Please check network and modem cables [I did, they're fine].  Another reason may be another running pppoe process which controls the modem."

I have no idea how to deal with the last part.

---

### Post by NeoLithium on 2007-06-07
Hmmm, so when you were in windows, did you ever need a username and password to connect to your ISP, or was it just plug and play. If I remember right you just go straight from your DSL modem to your computer, without a router, right?

---

### Post by Kiwilad on 2007-06-07
I got same results as God_of_Belac, except my ethernet devices were eth0 and eth0:avah. I have a broadband connection but always connect manually using a user name and password. I'm using an external Home DSL modem.

Thanks for you help, much appreciated

---

### Post by God_of_Belac on 2007-06-07
"Hmmm, so when you were in windows, did you ever need a username and password to connect to your ISP, or was it just plug and play. If I remember right you just go straight from your DSL modem to your computer, without a router, right?"

The 2wire gateway is a wireless router.  I connect with a wep key that's unique to the modem (and printed on it).  During the setup phase of the network, I had to input my account name and password with SBC/At+t into part of their website, but otherwise I don't use any password.

---

