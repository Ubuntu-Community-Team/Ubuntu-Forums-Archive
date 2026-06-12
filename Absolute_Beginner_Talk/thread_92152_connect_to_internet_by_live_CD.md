---
title: "connect to internet by live CD"
date: 2005-11-18
forum: Absolute Beginner Talk
---

### Post by purplefeltangel on 2005-11-18
Okay, I am using the Live CD of Ubuntu to learn how to use it before I actually install.

My question is, HOW ON EARTH DO I CONNECT TO THE INTERNET?!?!! :confused: :confused: :confused: 

I have a cable modem, which I *think* I configured correctly. I entered my IP address, too. However it is still not connecting.

It would help greatly if someone could explain to me, clearly and step-by-step, exactly what I have to do to get on the Internet. I have been using Windows for ten years so don't use any overly jargon-y words. :D

(Oh, by the way, don't give me any "you are already on the Internet, silly!" :P I have two computers.)

EDIT: My mother figured it out. ^_^;

---

### Post by darth_vector on 2005-11-18
welcome to ubuntu :)

you need to connect to the internet by specifying the gateway ip - the internal ip address of the cable modem. you do this by executing a command as follows:

route add -net <network ip> netmask <netmask> gw <gateway ip>

so, for example i would do

route add -net 192.168.0.0 netmask 255.255.255.0 gw 192.168.0.1

that should do it.

EDIT: it would probably be easier to set up your cable modem so that it runs DHCP. then your ubuntu box will set itself up on startup.

---

