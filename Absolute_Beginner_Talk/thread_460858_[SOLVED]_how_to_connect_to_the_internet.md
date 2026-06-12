---
title: "[SOLVED] how to connect to the internet"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by potatoehead64 on 2007-06-01
Hi Folks,

I downloaded and installed Ubuntu version 6 yesterday (close 6 coz it said there is longer support). I'm running my internet connection currently through XP with a "talktalk" broadband modem. So, I now have both O.S. on my pc partitioned.
Is there a guide on how to set up my internet connection in Linux Ubuntu and can I get/find the appropriate drivers for my modem? 

Cheers

Marty

---

### Post by NeoLithium on 2007-06-01
Hmmm, do you use PPPoE to connect? (Username and password?) I just did a quick search and I THINK that is what your service requires.  You can open up a terminal window (Applications -> Accessories -> Terminal) and type:

sudo pppoeconf 

It will walk you through everything you need for that.  Hopefully this helps.

---

### Post by potatoehead64 on 2007-06-01
> **NeoLithium said:**
> Hmmm, do you use PPPoE to connect? (Username and password?) I just did a quick search and I THINK that is what your service requires.  You can open up a terminal window (Applications -> Accessories -> Terminal) and type:

sudo pppoeconf 

It will walk you through everything you need for that.  Hopefully this helps.

OK. Thanks for your help on this. I have made some progress and have an understanding on how some of this works. I've entered the username/password section on the "dial" window (like on MS windows).
on using your advice, the command you gave me detected one ethernet device, however, with a broadband connected via USB I suspect this is not what I need (sorry, I'm a bit technically inept here).
The results of the command said (paraphrased) "access concentrator of provider did not respond, check cables..... or another pppoe process controls the modem"

I'm wondering if I need to manually configure drivers for the modem. If so, any idea how I do this/what the command is?

---

### Post by zvacet on 2007-06-01
I hope that some of this pages wil be usefull to you.

[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=usb+modem&titlesearch=Titles]("https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=usb+modem&titlesearch=Titles")

---

