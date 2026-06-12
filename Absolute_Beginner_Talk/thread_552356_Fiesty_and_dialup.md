---
title: "Fiesty and dialup"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by phil66 on 2007-09-16
Will Ubuntu ever offer help to dial up users for the fiesty distro

Not all Ubuntu users are fortunate enough to have dsl broadband available

I have used breezy and dapper and would like to use fiesty

At this time i have no Ubuntu installed because of the non existence of dial up in Fiesty

I have had to install PCLinuxos 2007 to have a linux distro that will recognize dial up

Would someone please rectify the dial up problem

---

### Post by schorsch on 2007-09-16
[Look here ...]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#dialup")

EDIT: Uhm, sorry, I did not know that you want to use a  serial modem and not a winmodem .... but you did not mention this in your first post .... ;-)

---

### Post by poe503 on 2007-09-16
I use 7.04 with just a 56k dialup modem.  If your modem is capable of being recognized by linux, you initially have to connect to the internet by configuring System>Administration>Network.  Once online, quickly download and install Gnome PPP, works like a charm.

I agree that they should consider us dialup users when concocting the distro.

---

### Post by phil66 on 2007-09-16
> **schorsch said:**
> Why complain?
[Look here ...]("https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#dialup")

If you had better knowledge of modems you would not recommmend finding drivers for a winmodem when this is a serial external modem 

The post you evidentally did not read explained how many different distro's worked with this modem

Please reread this post and adjust your answer correctly

---

### Post by sir_cheats_a_lot on 2007-10-31
no idea why people are saying system>administration>network doesn't/hasn't worked since dapper.  the only release i've had any trouble with it at all is in fiesty.  not sure about gutsy, as i don't have a copy of it yet. 
   for some reason eth0 interferes with dial up with my external serial modem, i simply disable the lan card and disable check the settings  and re-enable ppp0 then dial-up works again.    its weird i know.. perhaps i'm just lucky?  *shrugs*  its just a pain sometimes. 
but anyhow no need to do the whole run around others suggest by installing anything extra like gnome-ppp and wvdial.   on the previous install it wouldn't work at all.  wiped off the CD and retried and it worked.

if i dont disable the onboard lan i get this after i try to dialup. (from dmesg) 
[   54.616099] ADDRCONF(NETDEV_UP): eth0: link is not ready

no idea why though.  at least i have dialup working at the moment.    hopefully someone else will find this useful.

---

