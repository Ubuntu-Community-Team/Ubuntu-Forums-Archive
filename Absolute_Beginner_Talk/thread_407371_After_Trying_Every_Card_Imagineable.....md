---
title: "After Trying Every Card Imagineable...."
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by su_penguin on 2007-04-12
...I FINALLY got it working.

I think I've been to Staples purchasing / exchanging more wireless cards than any user in this ENTIRE forum. I stuck to my guns and I got Eft online. ::Takes a bow::

For some reason, my Linksys WMP300N pci card, the last card I decided on,  wasn't being recognized.
Then, like magic almost, there it was...

sudo ndiswrapper -i driver.inf
 ndiswrapper -l  ---> driver installed device installed
modprobe ndiswrapper

Turned the pc off and on about three times ( lol )......and there it was!!! (I'm SOOO FREAKIN' HAPPY RIGHT NOW! YOU HAVE NO IDEA!!!!) 

I will be a faithful user of this forum now that I have this problem resolved and I'll try to go into a bit more detail as to what one can do if they are having wireless card problems. ( TRUST ME I'VE SEEN THEM ALL INSTALLED )

-Wp

The WMP300N is wireless capable, the drivers are on the CD and it works right out of the box. I HIGHLY RECOMMEND THIS CARD!!! It's expensive but go get it. Also, the Wireless Configuration pages stating that some cards work right out of the box are false. I wish I would have noted each one but I was to focused on getting something that worked. More later......:)

---

### Post by justleen on 2007-04-12
Good on you!!

---

### Post by orb9220 on 2007-04-12
Good going sticking to your guns! But to keep it running you must:

> Sacrifice! one Virgin Microsoft employee to the Fires of the Ubuntu Goddess! And all will be Well.

---

