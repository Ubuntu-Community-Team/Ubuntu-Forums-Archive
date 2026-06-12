---
title: "Connecting to Internet(Make it easy guys)"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by santhinen on 2007-12-15
Hi everyone... I am new to ubuntu..used fc4 for an year..very excited to be a part of this community..
well to start with..i tried gutsy live version...
and problem started with connecting to internet..
I have a broadband connection via an ADSL modem..i.e PPPoE connection..
I tried to connect it in a similar fashion to windows or FC4.. but i didn't find any option for that in Preferences ... 
then searched in help and found few COMMANDS to be typed in the terminal...It was useful...

What i want to say is a normal user who is not in touch with a comp much and uses it just for some simple mail checking or browsing will be taken back when he has to type these commands...A setup wizard will help him better. A dial-up connection with a single click connection..

Is there no option to setup our internet connection with multiple options as we get in Windows or FC..like a network setup wizard kind of..

Note: I am new to gutsy..If such thing already exists..please forgive me and tell me how to do it!!

---

### Post by santhinen on 2007-12-15
Well is there any wizard to connect to internet like in fedora??
with diffeerent type of connection like.. LAN, PPPoE, wireless..in this fashion

---

### Post by kajillin on 2007-12-15
go to System> Administration> (then either) network (or) Network tools

And is it a wireless or a wired connection?

---

### Post by santhinen on 2007-12-15
its a wired..PPP over ethernet..an ADSL modem..
i checked out..even the documentation talked about commands but no wizard...

---

### Post by philinux on 2007-12-15
This is the reason I got a router.

1. Easier to set up - got its own like webpage
2. Built in hardware firewall
3. Couldn't get net access from ubuntu with my usb modem.

I'm sure in the intervening months someone has cracked it on here. Hopefully someone will give you the info you need.

---

### Post by kellsens on 2007-12-15
Hi santhinen !

Type in console: 

sudo pppoeconf

This, probably, will help you.

---

### Post by DezSP on 2007-12-15
The make/model of your modem would be useful.

---

