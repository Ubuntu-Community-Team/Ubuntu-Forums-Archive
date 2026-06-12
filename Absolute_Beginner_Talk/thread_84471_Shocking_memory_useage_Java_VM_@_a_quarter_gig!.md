---
title: "Shocking memory useage: Java VM @ a quarter gig!"
date: 2005-10-31
forum: Absolute Beginner Talk
---

### Post by Doc.Caliban on 2005-10-31
I know that Firefox has memory issues (and that they blame a lot of it on extensions), but what the heck is up with Java?  I just looked in System Monitor for something else and noticed that Java VM was using 250+MB of memory!

When I shut down Firefox, JVM still sat there at a quarter gig.  The instant I started Firefox again, JVM completely vanished.  

1. Is a quarter gig normal memory useage for JVM?

2. Is it normal that closing Firefox does not shut down JVM, but restarting it does?

-Doc

---

### Post by Kyral on 2005-10-31
Yah, the Java VM is a pain in the arse. It IS normal for it to take that much. Try running Azureus and the same thing will happen.

As for the Firefox closing the JVM, I actually don't know, I try to avoid Java as much as I can. That and I don't use Firefox anymore (Epiphany :D)

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=Kyral]Yah, the Java VM is a pain in the arse. It IS normal for it to take that much. Try running Azureus and the same thing will happen.

As for the Firefox closing the JVM, I actually don't know, I try to avoid Java as much as I can. That and I don't use Firefox anymore (Epiphany :D)[/QUOTE]


Thanks for the reply.

What is a good alternative for Azereus?  I hated it in WIndows because of the Java dependency as well.

-Doc

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=Kyral](Epiphany :D)[/QUOTE]


If it has tabbed browsing, I'll switch right now. 

Going without tabs in a browser now would be much too painful.   Firefox eating my memory in the background unnoticed is preferable to being miserable without tabs every time I use the browser.  I'm hooked.

-Doc

---

### Post by tonysathre on 2005-10-31
azereus altertives would be qtorrent or bittorrent, torrentflux, there are tons of them, just search synaptic or google for them

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=tonysathre]azereus altertives would be qtorrent or bittorrent, torrentflux, there are tons of them, just search synaptic or google for them[/QUOTE]

I'll check them out, but I was wondering if there's a general consensus on which are the better ones in Linux?

-Doc

---

### Post by Kyral on 2005-10-31
[I] If it has tabbed browsing, I'll switch right now. 

 Going without tabs in a browser now would be much too painful. Firefox eating my memory in the background unnoticed is preferable to being miserable without tabs every time I use the browser. I'm hooked.

 -Doc
[/I]  
It does

---

### Post by tonysathre on 2005-10-31
it kinda an odd problem to me...i havent noticed firefox having memory leaks

---

### Post by Kyral on 2005-10-31
It isn't Firefox. Its the JVM itself. You'd hit the same thing with Azureus.

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=Kyral]It isn't Firefox. Its the JVM itself. You'd hit the same thing with Azureus.[/QUOTE]


This seems to be the case.   

I'm running both Firefox and Epiphany right now and they're staying within 10MB of each other, and I'd expect Firefox to run a little heavier because I have several extensions installed whereas Epiphany is bare bones right now.

I'll probably stick with Firefox then.

So now I need a recommendation for a good non-Java Bittorrent client.

-Doc

---

### Post by tonysathre on 2005-10-31
bitcomet and bitlord are very lightweight

---

### Post by bored2k on 2005-10-31
[QUOTE=tonysathre]bitcomet and bitlord are very lightweight[/QUOTE]
Those are Windows clients.

---

### Post by tonysathre on 2005-10-31
sorry my bad... i just did a quick google query

---

### Post by Kyral on 2005-10-31
BitTornado is nice :D

---

