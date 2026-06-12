---
title: "Just installed on a new PC, net wont work... no idea where to start"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by joesmith1234 on 2008-01-19
I just installed Gutsy on an out of the box pc.  It originally had Linpus on it.

Anyways, the pc wont connect to the router.  It's directly connected with an RJ45, so no WiFi.

The network slot is on the mobo, I don't know if that changes anything.

Where should I start??? :-?

---

### Post by philinux on 2008-01-19
One thing to try is to shutdown pc, power everything off. Power on router until broadband link established then power on pc.

On mine the LAN light on the router only comes back on after logging in.

This is weird as router should just work. :confused:

---

### Post by joesmith1234 on 2008-01-19
Hmm, I will try restarting, but I don't know if it's really a router issue as I'm surfing on the same router right now.

---

### Post by joesmith1234 on 2008-01-19
nope, didn't work...

any other ideas?

I'm pretty sure it's a driver issue, but I don't know what to do.

---

### Post by philinux on 2008-01-19
Its probably the way the router is set up. Is thera a networking icon in notification area?

Can you ping the routers address from a terminal?

---

### Post by joesmith1234 on 2008-01-19
> **philinux said:**
> Its probably the way the router is set up. Is thera a networking icon in notification area?

Can you ping the routers address from a terminal?

I don't think that's it.... I have another Ubuntu machine with connects just fine when it's wired or when it's WiFi.

I think it has to do with the hardware itself... Ubuntu doesn't recognize it...

Also, when I type "ifconfig", no "eth0" shows up... only an "lo"

---

### Post by joesmith1234 on 2008-01-19
> **joesmith1234 said:**
> I don't think that's it.... I have another Ubuntu machine with connects just fine when it's wired or when it's WiFi.

I think it has to do with the hardware itself... Ubuntu doesn't recognize it...

Also, when I type "ifconfig", no "eth0" shows up... only an "lo"

I just pinged the router address... it said "network unreachable"

---

### Post by philinux on 2008-01-19
So its the gutsy machine thats not playing ball. Makes one suspect the ethernet card or cable or like you say the gutsy internet set up.

What about the gutsy live cd? Can that see the router?

---

### Post by joesmith1234 on 2008-01-19
> **philinux said:**
> So its the gutsy machine thats not playing ball. Makes one suspect the ethernet card or cable or like you say the gutsy internet set up.

What about the gutsy live cd? Can that see the router?

No, that didn't work either...  Ethernet cable was plugged in, but I got the "could not update packages" error during the install.

---

### Post by philinux on 2008-01-19
Sorry does the live cd boot up and see the router.

Also its best to have internet on when installing as without it messes with the sources list as you will have no doubt found out.

---

### Post by philinux on 2008-01-19
Use the command 

[FONT="Times New Roman"]lspci[/FONT]

in terminal to see if network card getting detected.

---

### Post by joesmith1234 on 2008-01-19
> **philinux said:**
> Sorry does the live cd boot up and see the router.

Also its best to have internet on when installing as without it messes with the sources list as you will have no doubt found out.

ok i have the live cd in and the pc running...

if I do "ping 192.168.1.1" I get "network unreachable"

ifconfig only shows for "lo" and no "eth0" is present.

So, same behaviour as on the installed version on my hd

---

### Post by joesmith1234 on 2008-01-19
> **philinux said:**
> Use the command 

[FONT="Times New Roman"]lspci[/FONT]

in terminal to see if network card getting detected.

lspci on the live cd gives, among others...

00:04.0 Ethernet controller: Silicon integrated systems sis 191 Gigabit ethernet adapter rev 02

---

### Post by philinux on 2008-01-19
Just seen this.

[http://ubuntuforums.org/showthread.php?t=556999](http://ubuntuforums.org/showthread.php?t=556999)

---

### Post by philinux on 2008-01-19
Theres's bad news here

[http://ubuntuforums.org/showthread.php?t=645175&highlight=Silicon+integrated+systems+sis+191+Gigabit+ethernet+adapter](http://ubuntuforums.org/showthread.php?t=645175&highlight=Silicon+integrated+systems+sis+191+Gigabit+ethernet+adapter)

Scroll down to the last two posts.

It says the sis 191 ethernet card is not supported. That might explain why gutsy os borking at it.

---

### Post by joesmith1234 on 2008-01-19
> **philinux said:**
> Theres's bad news here

[http://ubuntuforums.org/showthread.php?t=645175&highlight=Silicon+integrated+systems+sis+191+Gigabit+ethernet+adapter](http://ubuntuforums.org/showthread.php?t=645175&highlight=Silicon+integrated+systems+sis+191+Gigabit+ethernet+adapter)

Scroll down to the last two posts.

It says the sis 191 ethernet card is not supported. That might explain why gutsy os borking at it.

voi vittu....  Good thing I have a spare card laying around.

Well, thanks for the input.  Hopefully it will be working in Heron.

How do I figure that sort of thing out, anyway?  That is, how do I know if a piece of HW is supported or not?

---

### Post by philinux on 2008-01-19
There is a list somewhere. I guess you were just unlucky with that card. If mannufacturers of proprietry drivers dont make code available then the open source os cant recognise em I guess.

If you were insistant you could try sis's website but my take is you would have to compile a driver for gutsy yourself.

Spare NIC anyone :roll:

---

