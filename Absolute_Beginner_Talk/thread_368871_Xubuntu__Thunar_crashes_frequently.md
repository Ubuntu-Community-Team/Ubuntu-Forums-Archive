---
title: "Xubuntu:  Thunar crashes frequently"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-02-23
Am I the only one to be at loggerheads with Thunar?:confused: 
It hangs frequently without any obvious cause, and then I have to term it.
Is Thunar sucky or is it just me?

---

### Post by kerry_s on 2007-02-23
Mine works fine, maybe yours is corrupt, have you tried reinstalling it? 
Are there any clues in your xsession-errors? 
Have you tried deleting the .config folder to get everything back to stock?
You can use a different file manager, i use emelfm most of the time because it's just simple and fast.

---

### Post by Cyvros on 2007-02-23
Not sure if it helps, but Thunar always crashes or freezes when I use the tree (the tree itself frequently malfunctions, too). When I'm just using the Places sidebar, everything's just peachy. Mind you, I usually Thunar with Openbox on Ubuntu, not Xubuntu.

---

### Post by Blofeld on 2007-02-24
Guys ...
* I'm reinstalling Thunar, we'll see if this helps.
* I have also noticed that the tree (the pane on the right) often plays up (displays one folder multiple times, etc).
* I'm also a big fan of emelFM (emelFM2 to be precise).  However it plays up when handling exotic characters in file names, and somehow I can't get it to open .rtf-files with Abiword.
Thanks!

---

### Post by kerry_s on 2007-02-24
You'd probably have better luck opening the rtf with the OO word proccessor since rtf is a microsoft format and open office deals with MS formats better.

Yeah, i don't much care for emelfm2, they took a dirt simple thing and made it complicated. With emelfm i can make it do anything i want and do it fast.

---

### Post by picpak on 2007-02-24
I'm having the opposite problem, Thunar won't crash enough. I click the Close button, and it just hangs. I have to xkill it.

Any ideas?

---

### Post by kerry_s on 2007-02-24
I don't think this really matters, but what xfce version are you guys running have you updated to 4.4.0?

deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0

---

### Post by Blofeld on 2007-02-25
Kerry:  Do you think it's safe (and worth it) to update?  I was wondering about this as I have heard that Thunar has been much improved.

---

### Post by kerry_s on 2007-02-25
I'm been using it now for a week and don't have no problems. The only one thing that was goofy was mousepad kept leaving zoombies everytime i used it. But it wasn't doing that to anyone else, so i just uninstalled it and use the original leafpad, which is what mousepad is made from. Other than that everything just works, even composite, though i have mine turned off because its just to slow on my dualhead setup, works fine if i use clone view, but than whats the point of dual monitors. :)  I can't say if you might have problems as i have uninstalled alot of stuff and replaced others with faster apps so i'm not actually using a full blown xubuntu, but i do still have most of the xfce4 stuff and have no problems.

---

### Post by Blofeld on 2007-02-26
OK, I'm a have-a-go type of guy, so I'm having a go.
Fingers crossed!

---

### Post by hackworth on 2007-02-28
Any luck? I *just* re-installed after a HDD crash, and now Thunar is acting up for me, too. Very slow to open, and once open, it will sometimes freeze up, but will sometimes "unfreeze" if it let it sit long enough. and like i said, i just reinstalled xubuntu, so everything is pretty clean. 

the only thing i can think of that might be different from the old, problem-free set i had before was my partition scheme, which was a much smaller PATA drive vs. my new SATA drive, which has a very large FAT32 partition on it (~150GB). Could that large, non-ext3 partition be slowing it down for some reason?

---

### Post by Blofeld on 2007-03-01
I only have a 10 GB pATA hard disk and yet Thunar still froze, so the Thunar freeze problem doesn't have to be size-related.
I don't think Thunar has frozen since the update.  But now I'm having difficulties with evolution-alarm often crashing from the get-go.

---

### Post by hackworth on 2007-03-09
ahh, to stop the evolution-alarm errors, go to Settings > Autostarted Applications and click off evolution-alarm.

---

### Post by Blofeld on 2007-03-09
Oh, yeah.  Duh!  Thanks.

---

### Post by arlohh on 2007-03-11
Hi there,  I also experience seeing folder icons multiple times when using the tree. After sometime of using it, Ill click on some folder and Thunar zombies out for a bit, then comes back. Ill try emelfm and see what happens. Other than that, its fine.

---

