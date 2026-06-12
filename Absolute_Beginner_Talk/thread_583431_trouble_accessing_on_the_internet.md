---
title: "trouble accessing on the internet"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by leegumbrell on 2007-10-20
Hi,

I'm very new to Unbuntu and I'd be reallky thankful if anyone could help me.

I've just installed fiesty fawn on my laptop as I was having endless troubles with xp and felt like trying something new. the installation went fine and everything looks good, however i'm having some trouble getting on the internet.

I have a D link dwl-610 wireless card that i was using before but i cannot install it and it doesn't seem to recognise that its there (i ran in terminal a command that i read someone else had tried, but it didnt show the wireless card. i think it was lspci).

I've also tried plugging it straight into the router, and it appears to be connected, but i still cannot get on the internet. to get this connection i had to enter the ip address and some other bits that a guy at my old work explained to me how to find.

THe story gets a little more interesting now because my housemates and i have been having endless troubles with our internet as it is. we have virgin media broadband and 4 pcs. one is always plugged into the router and works fine. my laptop when i had xp on it would pick up the wireless, but not connect with a cable (it would find the connection but not allow me onto the net). the other 2 pcs have no connection to the internet whatsoever, despite our trying.

with this in mind, i dont know whether my inability to connect to the internet is the same problem i had before or if its something with ubuntu.

if someone could give me some advice for how to install this card, that would be excellent. if i have to download anything, i'll have to do it on my housemates pc.  i have only a little experience with unix from uni, and this is my first time using ubuntu, so the simpler the better please. if you need to know anymore information, i'll do my best to tell you.

thanks

lee

---

### Post by kyphi on 2007-10-20
Welcome to Ubuntu, lee.

You posed many questions, so where do I begin?

To have four computers connected to one router, while possible, presents some problems.  Remember that all signals have to pass through the one wire.

An wired ethernet connection is the easiest to set up.  Repeated connection and disconnection of the ethernet cable may cause damage to the cable and it may cease to function.

The easiest way to connect a computer is to buy an ethernet card (they are very cheap) and preferably use a wired connection.

Some of the built-in ethernet chips may not work with Linux and this also applies to some recent motherboards.

If you go to System and then Administration, then scroll down to Networking, you will find a screen listing your connections.  Mine gives two entries, one for a Modem connection (dial up) and the other for an Ethernet connection.  The default gateway device should read 'eth0'.  Click on the Ethernet connection entry and then on Properties.  'Enable this connection' should be ticked.  For 'Configuration' it should read DHCP.  Nothing else to put into that screen, so click OK.
Next go to the General tab.  The host name is the name that you have given to your computer.  The domain name is your email address.
On the next screen, DNS, you will need to enter your ISP's numerical address which looks like this: 000.000.000.000 Search Domains is the name of your ISP, virgin.com

That should be all.

I would get the ethernet connection working first before trying wireless.

---

### Post by leegumbrell on 2007-10-21
excellent! i'm now back on the internet. thanks alot.

---

