---
title: "Wireless Problems, help need:-?"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by newlinuxuser on 2006-02-21
Hi, I posted yesterday about my INPROCOMM IPN2220 Wireless LAN Card and how to get it up and running, I got some good responses but im having problems locating a drive online and after some googling it doesnt seem I am the only one having problems with this card, is this card totally impossible to get working, I really like Ubuntu its the only Linux dis. thats tempted me to throw out windows totally but I really need to use the internet as im a student. Is it possible to extract the driver from my windows system as thats how i connect at the moment, if so how would I do that? thanks in advance:)

---

### Post by fuscia on 2006-02-21
[QUOTE=newlinuxuser]Is it possible to extract the driver from my windows system as thats how i connect at the moment, if so how would I do that? thanks in advance:)[/QUOTE]

you could do a search for .inf files and see if that finds it. sorry, i'm not much help beyond that suggestion.

---

### Post by newlinuxuser on 2006-02-21
No luck with searching for *.inf files - I have a restore disk fox XP, is there anyway to extract the drivers from that disk?

---

### Post by tgoose on 2006-03-29
The files neccessary (and perhaps some not) are:
i2220ntx.cat
i2220ntx.sys
neti2220.inf and
neti2220.PNF

If you find these on the XP disc then it is certainly possible to extract them. Otherwise I'd suggest looking around the Acer website (or the brand of your laptop; I think a number of different ones use them) - I think that's where I found them. A word of warning: I (and another user: see [http://www.ubuntuforums.org/showthread.php?p=873467#post873467](http://www.ubuntuforums.org/showthread.php?p=873467#post873467)) have been unable to set this up with WEP. If the place you study at uses WEP (although probably it will have a more sophisticated system than this, in which case you'll be OK; mine did) then you will obviously not be able to connect in this way without doing something that I don't know how to yet...

If you want any help with setting it up without WEP, there should be enough information on these forums to get you going, but if not I can probably get you through it; I'm no expert but I've fiddled enough to get it set up.

---

