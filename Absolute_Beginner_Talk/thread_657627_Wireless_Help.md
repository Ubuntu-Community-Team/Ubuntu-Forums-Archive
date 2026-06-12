---
title: "Wireless Help"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by fireboy129 on 2008-01-03
Ok, i just FINALLY dual booted Gutsy and XP. but when i log on to ubuntu, it won't recognize my wireless. it shows that there is a network there, but it won't let me log onto it. it doesnt even show that it has a connection with the network, but the network is there.

i can use the internet from my windows. thats how im posting this.

its quite frusterating.

---

### Post by eolson on 2008-01-03
If your running a secure router you will need to set all that in Ubuntu also.   That's the only thing I can think of.

---

### Post by fireboy129 on 2008-01-03
> **eolson said:**
> If your running a secure router you will need to set all that in Ubuntu also.   That's the only thing I can think of.

there is no encryption or anything like that...

no idea wats wrong.

---

### Post by fireboy129 on 2008-01-04
bump.

running a linksys wireless G PCI adapter model WMP54GS

please help!!! i can use the internet from windows but not ubuntu.

---

### Post by ugm6hr on 2008-01-04
What is the output from:
```
lspci
```

I suspect that one of the lines will say something like:
Broadcom Corporation BCM4306 802.11g (rev 03)

I believe Gutsy allows use of Restricted drivers with Broadcom chipsets to install this, but you need to already be online for it to work (i.e. with a wired internet).

Otherwise you will need to use ndiswrapper with the Windows driver .inf and .sys files.

---

### Post by EduardoAB on 2008-01-04
Same happens to me with my WMP54GS. Any help from you guys?

---

### Post by fireboy129 on 2008-01-04
> **ugm6hr said:**
> What is the output from:
```
lspci
```

I suspect that one of the lines will say something like:
Broadcom Corporation BCM4306 802.11g (rev 03)

I believe Gutsy allows use of Restricted drivers with Broadcom chipsets to install this, but you need to already be online for it to work (i.e. with a wired internet).

Otherwise you will need to use ndiswrapper with the Windows driver .inf and .sys files.

how do i check that? jw... cause i really want 2 connect. 

cant get full compiz w/out internet.

---

### Post by ugm6hr on 2008-01-04
> **fireboy129 said:**
> how do i check that? jw... cause i really want 2 connect. 


Look at the Terminal link below - it explains where to enter the code.

---

### Post by fireboy129 on 2008-01-04
fixed!!!

it was my card. google "install linksys wireless-g with speedbooster on ubuntu"

first entry. its on the forums. works perfectly.

---

