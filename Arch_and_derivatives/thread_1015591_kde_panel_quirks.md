---
title: "kde panel quirks"
date: 2008-12-18
forum: Arch and derivatives
---

### Post by zephyrus17 on 2008-12-18
This is going to seem very elementary, but this is the first time I'm seriously using kde after 2 years with gnome. I'm using kdemod 4.1.

Anyway, when playing around with the items on the panel, I'm trying to arrange their orders. I added a new panel at the top and added a systray, but the systray takes up the whole panel. I've added kicker, digital clock, etc, but the remainer space has been taken up by the systray. I can't move, for example, the pager right next to my systray icons so there's no space in between. It seems there's this property with digital clock as well. How do I take away that space?

[[IMG]http://img384.imageshack.us/img384/3466/panelqw0.th.jpg[/IMG]](http://img384.imageshack.us/my.php?image=panelqw0.jpg)

---

### Post by mips on 2008-12-19
I use kdemod 4.2 but here goes:

Unlock widgets-> Panel Options-> Panel Settings
Hover mouse over systray and a double arrow should appear, now simply drag it to where you want it.

You could drag it to your desktop and try to resize it there.

---

### Post by chucky chuckaluck on 2008-12-19
you could bang your head on something like that.

---

### Post by zephyrus17 on 2008-12-19
> **mips said:**
> I use kdemod 4.2 but here goes:

Unlock widgets-> Panel Options-> Panel Settings
Hover mouse over systray and a double arrow should appear, now simply drag it to where you want it.

You could drag it to your desktop and try to resize it there.
Do you mean the 4sided arrow? It only moves the systray within it's allocated 'section', and if I move it more, it just swaps with the other launchers.

By the way, I thought kdemod was at 4.1 only?

> **chucky chuckaluck said:**
> you could bang your head on something like that.
Do you mean my question?

---

### Post by chucky chuckaluck on 2008-12-19
> **zephyrus17 said:**
> Do you mean my question?

no, i meant the panel at the top of the screenshot.

---

### Post by zephyrus17 on 2008-12-19
> **chucky chuckaluck said:**
> no, i meant the panel at the top of the screenshot.
Sorry, I'm confused. Do you mean it's thickness, it's arrangement?

---

### Post by mips on 2008-12-19
> **zephyrus17 said:**
> Do you mean the 4sided arrow? It only moves the systray within it's allocated 'section', and if I move it more, it just swaps with the other launchers.

By the way, I thought kdemod was at 4.1 only?


4.1 might be different, things change quickly these days on kde.

You can install KDEmod 4.2 from the Unstable repos. Please keep in mind that the kdemod domain name is in the process of changing to the chakra project so repos will have to be updated as well. [http://kdemod-old.ath.cx/bbs/viewtopic.php?id=1393](http://kdemod-old.ath.cx/bbs/viewtopic.php?id=1393)

[http://chakra-project.org/repo/](http://chakra-project.org/repo/)

Edit: 4.2 beta is much better than 4.1.x btw incase you are wondering.

---

### Post by zephyrus17 on 2008-12-19
Hmm.. Unstable. Have you experienced any crashes or anything?

---

### Post by mips on 2008-12-19
> **zephyrus17 said:**
> **Hmm.. Unstable.** Have you experienced any crashes or anything?

The bold is where the contradiction is if you ask me. 4.2 beta in the Unstable repos has less bugs than 4.1.x and is way faster. It might be in the unstable repo but it's way ahead of 4.1.x. Yes I find it more stable.

---

### Post by zephyrus17 on 2008-12-19
Hmmm..... Interesting.

So the server is:
```
[kdemod-unstable]
Server = .../unstable/x86_64
```right?

I guess I'll have to completely remove kde4.1? And what do you install? pacman -S kdemod4.2?

---

### Post by mips on 2008-12-20
> **zephyrus17 said:**
> 
So the server is:
```
[kdemod-unstable]
Server = .../unstable/x86_64
```right?


Correct. Just one thing, the beta has no locale files at this stage last time I checked but you can verify this for yourself. Also disable your current repo before syncing.


> **zephyrus17 said:**
> 
I guess I'll have to completely remove kde4.1? And what do you install? pacman -S kdemod4.2?

Yes, you would have to completely remove kde4.1 as well as QT else you will have conflicts unless you install it under a different user name. [http://chakra-project.org/download-kdemod-step1.html](http://chakra-project.org/download-kdemod-step1.html)

You have a several installation options,
pacman -S kdemod-kdebase  (Very minimal, only base system)
pacman -S kdemod  (Minimal usable desktop, my choice)
pacman -S kdemod-complete  (Complete kde4, not my choice at all)

The above will list the packages that will be installed. You might have to use the 'force' switch in pacman, was initially the case dunno if it still is.

---

### Post by zephyrus17 on 2008-12-20
Opps. Sorry, I did mean to say that I have kdemod4.1

Well, my pacman -Syu isn't showing any updates. Do I move [kdemod-unstable] above [kdemod-core] in pacman.conf? Or do I comment out [kdemod-core] totally?

---

### Post by mips on 2008-12-20
> **zephyrus17 said:**
> Opps. Sorry, I did mean to say that I have kdemod4.1

Well, my pacman -Syu isn't showing any updates. Do I move [kdemod-unstable] above [kdemod-core] in pacman.conf? Or do I comment out [kdemod-core] totally?

You have to **remove** your kdemod4.1 & comment out the [kdemod-core] repo before installing 4.2.

---

### Post by zephyrus17 on 2008-12-20
I can't overwrite it? or do a normal upgrade?

Alright, I'll do that.

---

### Post by mips on 2008-12-20
> **zephyrus17 said:**
> I can't overwrite it? or do a normal upgrade?


Not as far as I recall. There were some major changes somewhere with QT or something like that but can't really remember.

---

### Post by zephyrus17 on 2008-12-20
Hoho.. Kdemod4.1.85 does not like 64bit, that's for sure. Had to remove 4.2 beta and install 4.1 again.

Just on a side note, how do you mass uninstall kdemod-kde<something>? I had a case where I had a ton of kdemod-kdegames- stuff install and I wanted to remove it all. But pacman -Rd kdemod didn't touch it. I tried pacman -Rsn $(pacman -Qs kdemod-kdegames), but that didn't work

---

