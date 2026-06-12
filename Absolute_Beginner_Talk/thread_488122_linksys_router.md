---
title: "linksys router??"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by letitworknow on 2007-06-29
i just bought a linksys wrt54g  router and im not sure where to go from there.   i cant use the install cd cause its an exe file.    tried to open it with wine and it shows up for a second and then dis  appears.  i know that wine works cause i used it before. i know abut opeining a web page and going to 192.168.1.1 but the manual says that this is for advanced setup my pc should pick up router after i install the cd.    my pc shows that im connected to the internet but whn i open a web page nothing shows up.   any ideas??

---

### Post by Pollywoggy on 2007-06-29
> **letitworknow said:**
> i just bought a linksys wrt54g  router and im not sure where to go from there.   i cant use the install cd cause its an exe file.    tried to open it with wine and it shows up for a second and then dis  appears.  i know that wine works cause i used it before. i know abut opeining a web page and going to 192.168.1.1 but the manual says that this is for advanced setup my pc should pick up router after i install the cd.    my pc shows that im connected to the internet but whn i open a web page nothing shows up.   any ideas??


I have a WRT54GS and IIRC I was able to configure everything by connecting to [http://192.168.1.1](http://192.168.1.1)  and I did not use the CD to set it up.  The CD is for Windows users who generally don't know what they are doing, but it can be setup without that.

I later installed DD-WRT on the router in place of the original firmware.

---

### Post by gn2 on 2007-06-29
You need to enter your ISP user name and password and settings in the appropriate boxes.

It's all on the User Guide linked from this page: [http://tinyurl.com/fgj39](http://tinyurl.com/fgj39)

You may need to look on your ISP's help pages to find out the settings.

I've got a Netgear and it has it's own built-in Wizard for setting it up, but I don't know about Linksys.

You've got Linux, therefore you *are* an advanced user ;-)

---

### Post by caro on 2007-06-29
If you are familiar with setting up a router, then it is actually easier to go directly to 192.168.1.1 and set the router up manually.  An alternative would be to use a windows computer to set up the router (if you have one).  

Are you sure you are connected to the internet?  You may just be connected to your internal LAN.  What IP address do you have on your computer?

---

### Post by starcraft.man on 2007-06-29
> **Pollywoggy said:**
> 

I later installed DD-WRT on the router in place of the original firmware.

Seconded strongly. The DD-WRT firmware if you know what your doing is a vastly superior firmware than the crap linksys passes off. If you only need basic services though its not really needed unless you get a problem with yours.

Yes though, as stated you do not need the CD at all, I in fact tossed it out after I realized it installed garbage on my system (that linksys wireless program is bloated and useless when XP and Vista both handle it without trouble).

---

### Post by Rocket2DMn on 2007-06-29
Typically you can just plug the router into your modem through it's WAN port and go.  Very little configuration is needed (at least in the US) until you get the modifying the router to enable wireless encryption (which you SHOULD do!), port forwarding, and other such things.
The default login to the router is to open a web browser and go to 192.168.1.1, leave the username blank, and type in "admin" without quotes for the password.

edit: DD-WRT works best on the wrt54gl which has more onboard memory - I wouldn't suggest fiddling with this right now.  Get your router setup and working, then fool around later if you want.  Linksys' built in firmware, though minimal, works for most people (myself included).

---

### Post by santy_kushwaha on 2007-06-29
I'm using the same router but i never got the problem with that... U have to configure rightly u can do everything with 198.172.1.1  i used  CD but didn't help me a lot but when i used website it allows me to use more option and security try that speciafy what ur excat problem is then i might be able to help u

---

### Post by letitworknow on 2007-06-29
i really have no idea what im doing im just gettin into the world of the computer.  besides suffring the internet and some basic stuff that i learned over the past month.  i just figured that i would learn by doing.  and it has been working.  thanks for the help these forums are the best thing about ubuntu... that is for the novice like me.

---

### Post by oilchangeguy on 2007-06-29
> **letitworknow said:**
> i really have no idea what im doing im just gettin into the world of the computer.  besides suffring the internet and some basic stuff that i learned over the past month.  i just figured that i would learn by doing.  and it has been working.  thanks for the help these forums are the best thing about ubuntu... that is for the novice like me.

no one's asked yet, so i will. you are using a highspeed internet connection, and not dial-up, right?

---

### Post by caro on 2007-06-29
> **letitworknow said:**
> i really have no idea what im doing im just gettin into the world of the computer.  besides suffring the internet and some basic stuff that i learned over the past month.  i just figured that i would learn by doing.  and it has been working.  thanks for the help these forums are the best thing about ubuntu... that is for the novice like me.

If you are new, then here are a few helpful hints, in no particular order.  

[LIST]
[*]plug your router into your dsl/cable modem and make sure it is powered up
[*]you should see indicator lights telling you if you have a WAN connection (connection to the internet)
[*]connect your router to the modem and power it up
[*]depending upon your ISP, you may be able to set the router to automatically assign the DHCP addresses with no configuring needed on your part
[*]you may also have to enter an account name and password from your ISP
[*]if you aren't using a wireless connection, you can turn this off for now until you learn more
[*]some ISPs use the same IP scheme as the Linksys router so you will have a conflict.  If this is the case and you don't understand IP addressing, a quick call to your ISP or Linksys support can help you make the necessary changes
[/LIST]

Good luck.  (Hope I wasn't too basic for you...don't want to insult you.)

---

### Post by caro on 2007-06-29
Here is a screen shots to help you out...

---

### Post by letitworknow on 2007-06-29
ok so i went through the setup page and changed some things around.  im using comcastl cable internet.  i plug the comcast box into the router and my computer in to port one.  my pc then tells me "connection established"  but when i open the web page it just searches.

---

### Post by caro on 2007-06-29
> **letitworknow said:**
> ok so i went through the setup page and changed some things around.  im using comcastl cable internet.  i plug the comcast box into the router and my computer in to port one.  my pc then tells me "connection established"  but when i open the web page it just searches.

You may just be seeing a connection to your router.  What is your IP address?  (System > Administration > Network tools > Devices and select your Ethernet device)  Do you see an IP address like 192.168.x.x or 169.x.x.x?  If you see 169.x.x.x then you are not connected to the DHCP server and don't have a connection to the internet.  Have you entered your ISP username and password (if needed)?

You are obviously connected to the internet somehow since you are posting?  Can you use the other computer to configure your router?  I have the same router, and once I set it up (before I had Ubuntu) I was able to connect to it easily with Ubuntu.

---

### Post by letitworknow on 2007-06-30
the way i am posting is by hooking my pc directly to the cable modem which works fine.  yes when i checked my network tools it shows an i p address of 196.xxx .xxx .xxx   so what configuration do i change on the router to get to the internet using the router?

---

### Post by caro on 2007-07-03
196.x.x.x?  usually 169.x.x.x means you aren't getting an IP address from your router, modem, or other DHCP device.  192.x.x.x is usually set up as your internal network (behind your router or modem).

When you connect directly to your modem, check your IP address as described earlier in this thread.  Then once you are connected to your router, check it again.  If you can access the internet when you are connected to your modem and you have a 192.x.x.x address, and you can't connect to the internet when connected to your router and have a 169.x.x.x address, your modem and router are not playing well together.

When connected to your router, can you ping the modem or connect to it via the browser?

Can you post your IP settings from your modem and from your router?  Perhaps that will show where your difficulties lie.

---

