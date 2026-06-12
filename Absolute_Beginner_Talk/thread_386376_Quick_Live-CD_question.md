---
title: "Quick Live-CD question"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Retrograde on 2007-03-16
Hello all, 

I just got done testing out an Ubuntu Live cd to see how my hardware would handle it and everything was ok except for my network card. Should the live cd enable my network card or is that something that will only "turn on" when i do a full install. Played around for a little while trying to get it to enable but couldn't find anything that appeared to display a dhcp-enabled ip address.

For reference it's an integrated nic (realtek rtl8169/8110)

yup i feel like the ultimate n00b now. :-|

---

### Post by metroknight on 2007-03-16
You will have to activate it each time you use the live cd.

Go to System > Admin > Networking and put in the correct info. This worked for me. If you are using a wireless card then it is alittle harder (more complicated) but it does usually work.

---

### Post by deadbeef on 2007-03-17
> **metroknight said:**
> You will have to activate it each time you use the live cd.

Go to System > Admin > Networking and put in the correct info. This worked for me. If you are using a wireless card then it is alittle harder (more complicated) but it does usually work.



Ok.  I'm having the same problem, except with a wireless card.  Any general advice?

---

### Post by metroknight on 2007-03-17
> **deadbeef said:**
> Ok.  I'm having the same problem, except with a wireless card.  Any general advice?

My wireless card loaded the first time but I think I just got lucky. I keep reading about ndiswrapper in various threads. If you go to the homepage (click on home up above), there is a list of keywords that start an autosearch, try wireless and start reading.

There is this thread.

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

Since you didn't mention what type of wireless card you have, I'm guessing and taking potshots in the dark. Sorry that I couldn't help you any more than that.

---

### Post by Retrograde on 2007-03-18
Well I've figured out how to activate it but I'm still not getting an ip address. There is a drop down box in one of the network tabs thats says "Loopback Interface" but I'm unable to select anything else. I suspect this is a driver issue (in that i have none installed), am i correct and in that case i guess i gotta go find drivers right? Thanks to everyone who's helped so far

---

### Post by Retrograde on 2007-03-18
Alright never mind, I'm just a moron who never checked the box next to my Ethernet adapter! All connected and posting from ubuntu now, despite me being dumb at least i learned how to install drivers even though it was probably redundant.

---

### Post by metroknight on 2007-03-18
I've learned that nothing is redundant. Now that you've learned something, you can help some else if they have a problem similar to what yours was. That was how I started learning.

---

