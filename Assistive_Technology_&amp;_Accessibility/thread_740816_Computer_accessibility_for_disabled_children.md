---
title: "Computer accessibility for disabled children?"
date: 2008-03-31
forum: Assistive Technology &amp; Accessibility
---

### Post by duckgoesoink on 2008-03-31
Hi,

I have a 5 year old with cerebral palsy, and I'm looking for a way for him to control the computer using a **symbol-based on-screen keyboard** (like [http://www.sensorysoftware.com/computercontrol.html](http://www.sensorysoftware.com/computercontrol.html)), to use the computer for **symbol-based augmentive communication** (like [http://www.sensorysoftware.com/symbolchat.html](http://www.sensorysoftware.com/symbolchat.html) or [http://www.pvoice.org:20080/showpage/en/pvoice](http://www.pvoice.org:20080/showpage/en/pvoice)), and to use it for **school quizzes and activities** (like [http://www.chooseitmaker2.com](http://www.chooseitmaker2.com)). 

Is this possible in Ubuntu yet? Or will he have to stick to Windows for now?

Thanks a lot :-)

P.S. I tried running pVoice in Wine without success. I don't (yet) have the other programs at home to try in Wine.

---

### Post by duckgoesoink on 2008-04-03
OK well I guess either this is not at all possible yet or no-one knows. I wonder how labour-intensive it would be to build very basic versions of these kinds of programs (especially the first and last ones).

Does anyone else here have or know of disabled children who can't access a computer in a normal way?

---

### Post by stoodleysnow on 2008-04-07
You don't need to panic yet - Ubuntu has plenty of accessibility programs. Under System - Preferences - Universal Access, you will find pre-installed helpers such as screen readers and magnifiers. An on screen keyboard is available somewhere (I forgot exactly where, have a look around). Some touch screens work with Ubuntu, and a large keyed USB keyboard is available from Keyneeds via Scan Computers. This thread may prove interesting:
[http://ubuntuforums.org/showthread.php?t=628600&page=6](http://ubuntuforums.org/showthread.php?t=628600&page=6)
Particularly the description and the 'whole room' pictures.
GCompris may be a suitable educational suite to begin with.
All applications can be installed using Applications - Add/Remove :)
Hope this is helpful.

---

### Post by frafu on 2008-04-07
Hello, 

Unfortunately, I don't know whether there are application that provide out of the box what you are looking for. 

Apart the Screenreader, there are also 3 onscreen keyboards: 
- onboard is a simple, now hassle onscreen keyboard 
- xvkbd: onscreen keyboard with word completion 
- gok (gnome onscreen keyboard): it is possible to use it as a secondary pointer, it should be possible to define custom keyboard layouts (though I don't know whether pictures can be used in the keys),... 

In fact, Ubuntu uses GNOME for its desktop, and you should try to also ask your question to the gnome-accessibility-list: 
[http://mail.gnome.org/mailman/listinfo/gnome-accessibility-list](http://mail.gnome.org/mailman/listinfo/gnome-accessibility-list)
(You have to subscribe to the mailing list to post to it.) 

Among others, the maintainer of gok is also subscribed to that list. 

Have a nice day. 

Francesco

---

### Post by duckgoesoink on 2008-04-08
> **stoodleysnow said:**
> You don't need to panic yet - Ubuntu has plenty of accessibility programs. Under System - Preferences - Universal Access, you will find pre-installed helpers such as screen readers and magnifiers. An on screen keyboard is available somewhere (I forgot exactly where, have a look around). Some touch screens work with Ubuntu, and a large keyed USB keyboard is available from Keyneeds via Scan Computers. 
GCompris may be a suitable educational suite to begin with.
All applications can be installed using Applications - Add/Remove :)
Hope this is helpful.

Thank you for your help, but I'm not sure the pre-installed accessibility options are suitable for a child (just learning to read, severe motor delays, normal intelligence, vision fine).

I tried GCompris, but I don't think it's switch-accessible, so it's hard for him to play alone (that last link I gave in the original post - [http://www.chooseitmaker2.com/](http://www.chooseitmaker2.com/) - was to ChooseIt Maker - it allows one to create switch-accessible multi-choice activities/games with pictures and sound).

But I appreciate your trying to help. :-)

---

### Post by duckgoesoink on 2008-04-08
> **frafu said:**
> Hello, 

Unfortunately, I don't know whether there are application that provide out of the box what you are looking for. 

Apart the Screenreader, there are also 3 onscreen keyboards: 
- onboard is a simple, now hassle onscreen keyboard 
- xvkbd: onscreen keyboard with word completion 
- gok (gnome onscreen keyboard): it is possible to use it as a secondary pointer, it should be possible to define custom keyboard layouts (though I don't know whether pictures can be used in the keys),... 

In fact, Ubuntu uses GNOME for its desktop, and you should try to also ask your question to the gnome-accessibility-list: 
[http://mail.gnome.org/mailman/listinfo/gnome-accessibility-list](http://mail.gnome.org/mailman/listinfo/gnome-accessibility-list)
(You have to subscribe to the mailing list to post to it.) 

Among others, the maintainer of gok is also subscribed to that list. 


I had a look at onboard and gok - I'm not sure if it's possible to customise the layouts with picture symbols, but I think they use SVG files for the visual layout so in theory it should be possible?

Thanks for the link to the mailing list - I'll try asking there too.

---

### Post by frafu on 2008-04-08
Hello, 

There is also a program called [Dasher]("http://www.inference.phy.cam.ac.uk/dasher/"): I did not mention it in my previous email because it is normally used for text input. Maybe that it might nevertheless interest you due to its very unconventional gui. 

It is also available from one of Ubuntu's repositories.

Have a nice day.

---

