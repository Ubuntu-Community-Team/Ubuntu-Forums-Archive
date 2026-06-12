---
title: "Couple of Questions"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by danthebugman on 2007-08-07
Ok so the Linux switch is going pretty well, but I have a few questions that I have not been able to find a satisfactory answer to so maybe someone can help me out??

1.)  Linux I've read doesn't have to be defragged like Windows did...awesome.  But I've been trying out a log of different programs lately to see what I like and am sorta concerned that maybe some dependencies that didn't get completely removed when I "uninstalled" them.  Should I be concerned?  Is there a program to help clean these up?

2.)  I've been trying for a while now to find a suitable method to copy my DVD's (I absolutely hate to loan out any DVD in my collection as they almost always come back to me in a terrible state and well I also have a problem being stingy amongst my friends so what ya gonna do lol).  When I used Windows I used DVD Decrypter to rip the movie to my hard drive, then used DVD Shrink to burn it to a normal DVD.  This set-up worked really well and was easy.  It seems the more I've looked into this topic with Linux, the more confused I've become about how to go about it.  I don't mean to ruffle any feathers here, but I thought Linux was supposed to make your life easier :confused:  Maybe I just haven't been looking in the right place??  I came across one tutorial that showed how to configure DVD Decrypter and DVD Shrink using Wine, but as tempting as this sounded I felt a little like I was cheating on my hot new gf going that route.  I think I've decided to use DVD::Rip to rip the movie then use Tovid to burn it to a DVD...will this work??  If not please give me guidance...

3.)  I've installed some programs with Wine (utorrent, BabasChess) and have found that I'd rather just make due without them or use a Linux program instead, but I can't seem to remove them...how does one go about doing this (and yeah I've tried removing them from the Wine Uninstaller)??

Any and all help would be greatly appreciated!!

Regards,
Daniel

---

### Post by PurposeOfReason on 2007-08-07
For #2 use acidrip. It's by far quicker and easier.

---

### Post by Gmbrdilos on 2007-08-07
1. there is a program that is capable of removing orphaned packages (dont remember the name)

2. there is a clone of dvd shrink for linux, you can install it through automatix

3. I guess you could delete the bottle. There are good native programs for torrents (Azerus for one) and there is also gnome chess installed by default

---

### Post by teknosexual on 2007-08-07
#2: I've found k9copy works very well for backing up DVDs. It's a lot like DVDshrink. k3b is a great burning utility.

---

### Post by danthebugman on 2007-08-10
Thank you to those that posted replies.

1.)  Anyone know of the name of the program that removes orphaned packages??

2.)  I finally settled on k9copy and k3b as DVD backup tools.  Burned my first one tonight and while it took longer than I think it should have I was satisfied with the results.

3.)  How does one "delete the bottle"??

Thanks,
Daniel

---

### Post by splintercellguy on 2007-08-10
1. Googling suggests invoking: deborphan | xargs apt-get remove Do so at own risk.

---

### Post by cobrn1 on 2007-08-10
Unless you're a bit low on disc space, do you realy want to get rid of the dependancies? I mean, I like to keep my installations and HDDs clean ( almost obsessively), but they might well be used again, and keeping them will save re-downloading them. Also, you might break something accidentally, so it may be more trouble than it's worth...


> **danthebugman said:**
> I felt a little like I was cheating on my hot new gf going that route. 

lol... :D But I understand what you mean too.

you may want to look up something called deluge, it looks alot like utorrent for linux, but open source and by different people... It has a nicer icon too... ;)

---

### Post by amazingtaters on 2007-08-10
utorrent is now the official BitTorrent client, at least on windows. As such, it is now closed source. I use utorrent on my windows box, but I will never upgrade it again because of that. I'd say try some torrent clients that run natively, like Ktorrent (it's very utorrent feeling)

---

### Post by cobrn1 on 2007-08-10
> **amazingtaters said:**
> utorrent is now the official BitTorrent client, at least on windows. As such, it is now closed source. I use utorrent on my windows box, but I will never upgrade it again because of that. I'd say try some torrent clients that run natively, like Ktorrent (it's very utorrent feeling)

Yes, the closed sourcing of utorrent and now the bittorent protocal distresses me slightly - go for the most open source alternative you can muster, and as far as I can see deluge fits the bill...

EDIT: oh yes, and I too would like to know how to / what the hell is 'deleting the bottle'...

---

### Post by ramjet_1953 on 2007-08-10
With copying DVD's I'd like to say that I have had good success with [COLOR="Blue"]k9copy[/COLOR] to compress and [COLOR="Blue"]k3b[/COLOR] to write.

Both are KDE applications, but work fine under GNOME. I have noticed under GNOME that k3b can take a few seconds to start-up. I can only assume that the necessary KDE files are being loaded first, to allow it to run.

When removing packages with Synaptic, when you right-click on a package, choose the [COLOR="Blue"]Mark for Complete Removal Option.[/COLOR]

That will get rid of all files that were installed with that application.

You may also want to check out[COLOR="Blue"] kleenswee[/COLOR]p and [COLOR="Blue"]deborphan[/COLOR] in the repositories.

Please read-up on using these apps first, as they can be a bit dangerous.

Regards,
Roger :cool:

---

