---
title: "step backwards"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by dmichaels on 2006-11-04
ok so obniously i made a huge mistake and decided to upgrade to edgy. bad idea. i sthere any way i can get back to dapper without losing any data?

---

### Post by blendmaster on 2006-11-04
I'm afraid the only way to go back to Dapper is by backing your files up, wiping your computer, and then reinstalling with Dapper.

If you could tell us the mistake (although you might have already), we might be able to fix it.

Also if upgraded through the terminal, that tends to cause problems for Edgy. If you upgrade by wiping the drive, and reinstalling with Edgy, the problems are usually a lot less frequent, and a lot more minor.

Sorry I can't help further!

---

### Post by dmichaels on 2006-11-04
well the message i get is:

ive deected another panel running and will now exit. 

thats when all the icons disappear and the display freezes

---

### Post by CatKiller on 2006-11-04
Apparently, if you do a ```
rm -r ~/.gconf/apps/panel
``` it deletes the panel configuration and goes back to the default. Perhaps that will help you?

---

### Post by PriceChild on 2006-11-04
> **dmichaels said:**
> well the message i get is:

ive deected another panel running and will now exit. 

thats when all the icons disappear and the display freezesThat's a TINY error.... hardly anything compared to most! :D You're upgrade went well! :)

Ctrl+alt+F1, log in then:> **CatKiller said:**
> Apparently, if you do a ```
rm -r ~/.gconf/apps/panel
``` it deletes the panel configuration and goes back to the default. Perhaps that will help you?then ```
exit
``` and Ctrl+Alt+F7 and you should be laughing!

---

### Post by CatKiller on 2006-11-04
> **PriceChild said:**
>  and Ctrl+Alt+F7 and you should be laughing!

I found something out the other day - you don't need the Ctrl. You need Ctrl-Alt-Fkey to get **out** of your graphical environment, but you only need Alt-Fkey to switch between your ttys and go back into it.

---

### Post by PriceChild on 2006-11-04
> **CatKiller said:**
> I found something out the other day - you don't need the Ctrl. You need Ctrl-Alt-Fkey to get **out** of your graphical environment, but you only need Alt-Fkey to switch between your ttys and go back into it.How cool! :D


Not up to the amazingness that was the day when i noticed highlight & middle click though!

---

### Post by CatKiller on 2006-11-04
> **PriceChild said:**
> Not up to the amazingness that was the day when i noticed highlight & middle click though!

My brain's still in bits from when I tried to wrap it around the concept of **screen**. I can start a process, detach from it, log out, wander off, log into a different computer, and attach to the process again to see how it's getting on. Complete insanity.

---

