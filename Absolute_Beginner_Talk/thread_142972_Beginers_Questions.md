---
title: "Beginers Questions"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by TruthElixirX on 2006-03-11
I looked for about an hour for answers to these questions and couldn't find them...

So, I'm new to the world of Linux and Ubuntu. I currently have a Windows XP Service Pack 2 OS on my laptop. I want to dual boot(I think this is the proper term) Ubuntu and XP (Home Edition).  What steps do I need to take to assure I lose no data and that I don't screw up my XP install? I'm currently downloading the latest release and about to burn the ISO to a CD.

Also can someone explain the difference between KDE and Gnome? I looked on wikipedia and as far as I could tell it as just cosmetics, is it?

Anything I should do before taking the plunge?

EDIT:: Thanks for moving. Sorry for putting it in the wrong forum.

---

### Post by christhemonkey on 2006-03-11
I would suggest that you backup anything important first, and then defrag  like there is no tommorow!
KDE and Gnome or just two different desktop environments, there is also XFCE as another main rival.  They just work slightly differently and display programs with different toolkits of pictures and things.  Try looking at desktop environment on wikipedia.

---

### Post by aysiu on 2006-03-11
[QUOTE=TruthElixirX]
So, I'm new to the world of Linux and Ubuntu. I currently have a Windows XP Service Pack 2 OS on my laptop. I want to dual boot(I think this is the proper term) Ubuntu and XP (Home Edition).  What steps do I need to take to assure I lose no data and that I don't screw up my XP install? I'm currently downloading the latest release and about to burn the ISO to a CD.[/quote] What steps? Back up all your data first. That's the only way to be 100% certain your data won't be lost.

If you want to be 99% sure, follow these steps:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

> 
Also can someone explain the difference between KDE and Gnome? I looked on wikipedia and as far as I could tell it as just cosmetics, is it? My experiences:
[http://www.psychocats.net/essays/kdevsgnome](http://www.psychocats.net/essays/kdevsgnome)

> 
Anything I should do before taking the plunge? Yes. Ask questions (as you're doing now) *before* you try something new instead of afterwards. It's always better to say "Should I do this?" or "What's the best way to do this?" than to guess and then have to ask "How do I fix this?"

---

### Post by issueperson on 2006-03-11
for the differences between KDE and Gnome:

[http://ubuntuforums.org/showthread.php?t=142147](http://ubuntuforums.org/showthread.php?t=142147)

---

### Post by TruthElixirX on 2006-03-11
After I defrag and back-up, what steps do I need to take to dual boot XP and Ubuntu?

Thanks evryone for being helpful. ^_^

---

### Post by aysiu on 2006-03-11
[QUOTE=TruthElixirX]After I defrag and back-up, what steps do I need to take to dual boot XP and Ubuntu?[/QUOTE] These steps:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by TruthElixirX on 2006-03-11
Oh, its a whoel tutorial Thanks. :)

---

### Post by syg00 on 2006-03-11
[QUOTE=christhemonkey]I would suggest that you backup anything important first, and then defrag [/QUOTE]After that, enter the following from an XP command prompt "chkdsk /f". This will complain about being in use and ask ifyou want the check done on the next re-boot. Reply "Y", and re-boot immediately.
This will force a chkdsk and will fix any problems (like cross-linked pointers) it finds.

This is important if you want to use the resize option on the Ubuntu install - if there are any errors the resize will fail, and you'll be stuck and never know why.

---

