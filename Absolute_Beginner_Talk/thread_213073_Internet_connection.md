---
title: "Internet connection"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by tiger99 on 2006-07-10
Hi 
I have a general question about internet connection.
I have a weird house host, she doesn't want to give me the wireless password for internet connection. she has one computer in a room for all my roommates. Everyone has limited permission on that computer except her son. So that means I can't setup the VPN to connect to my school library database. 
So does anyone know if there is a way to connect my laptop to my house host's computer and get the internet connection for my laptop(without knowing the wireless router password)? 

I am thinking to connect the two with a ethernet cable. Will that work? 
If any of you guys know how to resolve my problem, I will be really appreciated if you can give me a detailed setup procedure

P.S. I am new in linux and I just installed the latest ubuntu
Everytime I need to use internet, I have to come to school and use PPTP for wireless connection

Thanks  in advance for any input

---

### Post by Maggot on 2006-07-10
Yes, technically it can be done.  You'd still have to have her computer configured to act as a gateway though.

You'll need a cross-over cable.

[http://www.homenethelp.com/network/ethernet.asp](http://www.homenethelp.com/network/ethernet.asp)

---

### Post by verbatim210 on 2006-07-10
the wireless password is irrelevant
as long as you have connection, no problem

how is the wireless password stopping you from creating successful VPN connection?  maybe you are referring to computer password?

either that or firewall, but definately not wireless password.

using a secondary computer is quite clever, i would imagine the primary computer prevent you from installing VPN client.  if no firewall set up or set up poorly, you can achieve your goal easily.

---

### Post by Maggot on 2006-07-10
> **verbatim210 said:**
> the wireless password is irrelevant
as long as you have connection, no problem

My guess is the wireless is encrypted with WEP, WPA, etc. He'll need that to use it.

---

### Post by verbatim210 on 2006-07-10
yeh but that is house owner's concern 
tiger99 concern is to connect remotely

no need for wireless password
only need access (connectivity)so...

the main computer is the only thing stopping this and possibly firewall.  if tiger99 connect laptop to main computer and treat it like a gateway as maggot said.  there is no problem.

---

### Post by woedend on 2006-07-10
you'll probably need a crossover(patch) cable...sometimes its autodetecting and enet will work but most i've seen need crossover.

---

### Post by Maggot on 2006-07-11
> **verbatim210 said:**
> yeh but that is house owner's concern 
tiger99 concern is to connect remotely

no need for wireless password
only need access (connectivity)so...

the main computer is the only thing stopping this and possibly firewall.  if tiger99 connect laptop to main computer and treat it like a gateway as maggot said.  there is no problem.
Im still a bit confused on how this 'main' computer is setup but either way I think you'll need access to this computer and administrator rights to set it up for what you want to do. It sounds like you won't be able too either ;)

---

### Post by verbatim210 on 2006-07-12
| 
INTERNET CONNECTION |
^^^^^^^^^^^^^^^^^^  |
[main computer] <===cross-over-network===>[your computer]
_ _ _ _ _ _ _ _ _ _ | 

tell me when you successfully access 
the internet from [your computer]

---

### Post by verbatim210 on 2006-07-12
_ _ _ _ _ _ _ _ _ _ _ _ _ _ 
INTERNET - CONNECTION  |
^^^^^^^^^^^^^^^^^  |
[main computer] <===cross-over-network===>[your computer]
_ _ _ _ _ _ _ _ _ _ _ _ _ _ | 

sorry that didnt come out right
hope this makes more sense

---

### Post by Maggot on 2006-07-12
That would work but I believe you have to tell the main computer to act as a gateway.  I assume its running windows?

Once her computer is set, configure yours (running ubuntu) by:

[LIST]
[*]SYSTEM
[*]ADMINISTRATION
[*]NETWORKING
[/LIST]
then click on your ethernet card
[LIST]
[*]PROPERTIES
[*]check ENABLE THIS CONNECTION
[/LIST]

then under Configuration, 

[LIST]
[*]select STATIC IP ADDRESS (if you know for sure, the main computer has DHCP Server service running, leave as DHCP. Nothing else required at this point).
[/LIST]

If using STATIC IP

[LIST]
[*]ADD IP ADDRESS (Must different from main computer)
[*]SUBNET MASK (Must be same as main computer)
[*]GATEWAY (IP address of main computer)
[/LIST]

Is she gonna allow you to configure her computer to accommodate this?

---

### Post by verbatim210 on 2006-07-13
there is no higher administrative power
than physical access.

verbatim

---

