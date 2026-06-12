---
title: "How am I managing to lock out the keyboard?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by silkstone on 2007-03-21
It's happened twice now. I've been typing an email (Thunderbird), and my fingers have slipped so I'm probably pressing something like <CAPS> <CTRL> and maybe ! at the same time.... and then the keyboard no longer responds. The mouse is fine, but none of the keys do anything at all. I've tried pressing what I thought I'd pressed again to see if that unlocked it, but no joy. I have to shut down and reboot.

Any idea what I'm doing here?

---

### Post by mahy on 2007-03-21
Add the following line:

Option      "SHMConfig"      "on" 

to the touchpad section of your /etc/X11/xorg.conf

---

### Post by mahy on 2007-03-21
Sorry, silly me, bad advice. Won't help...

---

### Post by Ozor Mox on 2007-03-21
Incidentally, I've had the problem occur once or twice for seemingly no reason. I have not yet found a solution. I can only assume it's a very strange bug of some kind. Luckily it shows up very rarely, at least for me.

---

### Post by silkstone on 2007-03-21
So is this a bug or an obscure 'lock keyboard' key sequence?

---

### Post by Diabolis on 2007-08-26
I'm very interested in this topic, since this happens a LOT to me. Probably it occurs like 4 to 5 times a day. Since both mouse and touchpad still work, sometimes I just keep working like that. A better workaround for this problem is to **suspend** the computer, after this, the keyboard will work again. I wish this was a problem related to ubuntu because in that way  probably I could find more info about it. I think It is not related with linux because this happened to me a few months ago with windows xp when I didn't even know what ubuntu was.

Maybe if everyone who has had this problem posts the circumstances in which the problem appeared, we could point out common factors.

I use:
Ubuntu feisty fawn
Acer TravelMate 2420

I think that the model of the keyboard for my laptop is: Acer Ferrari 4000

---

