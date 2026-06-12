---
title: "Powerbook G3 Wireless Problems"
date: 2006-06-04
forum: Apple PPC Users
---

### Post by DJLC on 2006-06-04
I have Ubuntu 6.06 installed (and working wonderfully) on my Powerbook G3 Lombard. In OS X, I used my PCMCIA Sonnet Aria Extreme card for wireless. OS X saw it as an AirPort card, and it worked flawlessly with the AirPort driver. After following this tutorial: [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear), it still wouldn't work. The Networking program sees the card and can activate it. Network Manager says "No network devices have been found," and Wireless Assistant sees the network, but when I try to connect, it fails.

Does anyone know how I can get this card working? I really need wireless...

---

### Post by Down8ve on 2006-06-04
I have the exact setup you have, although it has the MacAlly wireless card.  I have not been able to install Dapper.  My machine hangs when booting the live CD as it initiates the network.  The CD checks out fine on my iMac.  How did you get it installed and how does it work overall?  Is it snappy?

DSM

PS

Sorry I don't have an answer for you.

---

### Post by DJLC on 2006-06-04
[QUOTE=Down8ve]I have the exact setup you have, although it has the MacAlly wireless card.  I have not been able to install Dapper.  My machine hangs when booting the live CD as it initiates the network.  The CD checks out fine on my iMac.  How did you get it installed and how does it work overall?  Is it snappy?

DSM

PS

Sorry I don't have an answer for you.[/QUOTE]

Mine booted off the live CD perfectly. What I'd suggest for you is to remove the wireless card before you boot off the CD. Dapper is very snappy on this old 'book. Much faster than 10.3. It makes this old Mac much more useful. Think the speed of  OS 9 with the modern conveniences of OS X.

I might have  to go back to 10.3 if I can't get  this wireless working. I hate having to use ethernet ](*,) .

---

### Post by DJLC on 2006-06-04
I found the problem.

I ran Wireless Assistant as root. It then successfully connected to my network.

Yay!

---

