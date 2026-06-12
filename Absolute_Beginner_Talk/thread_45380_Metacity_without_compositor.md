---
title: "Metacity without compositor"
date: 2005-06-29
forum: Absolute Beginner Talk
---

### Post by Zaare on 2005-06-29
I would like to use metacity without the compositor (since I want to use  xcompmgr instead). I suspect I have to compile it myself. I've searched the net and tried to do this but I can't make it work.
I would appreciate it if someone could give me a step by step guide on how to do this.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=Zaare]I would like to use metacity without the compositor (since I want to use  xcompmgr instead). I suspect I have to compile it myself. I've searched the net and tried to do this but I can't make it work.
I would appreciate it if someone could give me a step by step guide on how to do this.[/QUOTE]


I use xcompmgr with metacity as it is...I don't really know what you want.

---

### Post by Zaare on 2005-06-30
Well, here's the whole story:
When I installed gdesklets, they desklets couldn't be transparent. I searched and found this: [http://gdesklets.free.fr/board/viewtopic.php?t=68](http://gdesklets.free.fr/board/viewtopic.php?t=68).
I followed the instructions except for the compiling of metacity. It all works nicely except for two things:
1. When I minimize a window it leaves a black "dot" on my desktop
2. And when I put xcompmgr among startup programs my top panel disappears and the "log out screen" won't work. When click "log out" in the "System menu" my computer stops responding.

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=Zaare]
I followed the instructions except for the compiling of metacity. It all works nicely except for two things:
1. When I minimize a window it leaves a black "dot" on my desktop
2. And when I put xcompmgr among startup programs my top panel disappears and the "log out screen" won't work. When click "log out" in the "System menu" my computer stops responding.[/QUOTE]


Now you are dealing with the bugs of xcompmgr. Its bleeding edge stuff so there is no way around it. I don't know if gutting metacity will even help one bit.

1. Are you using the fading effect? Do you have an nvidia card (only newer nvidia cards really can do xcompmgr right)? 

2. Use this command to fix the panel thing:

> killall gnome-panel

and as far as the logout screen goes....its still there....just hit enter.

But there is no way to fix this stuff other than waiting till it stabilizes more in the future.

---

### Post by Zaare on 2005-06-30
I see. In that case there's not much I can do about it, I suppose.
I use ATI Radeon Mobility 9000.
Do you have any problems with xcompmgr?

---

### Post by poofyhairguy on 2005-06-30
[QUOTE=Zaare]
Do you have any problems with xcompmgr?[/QUOTE]

Yep. But its still the best eye candy one can get. In fact, recently I bought a $30 Nvidia 5200 FX JUST for xcompmgr (once you see fading on an Nvidia card you can't go back). But I have to live with the fact its buggier that Window's ME.

I turn it off if I have to download thing overnight.

EDIT: If you really want it...KDE plays better with xcompmgr..

---

### Post by Zaare on 2005-06-30
Hehe, yea, it's a pretty thing.
I'll have to consider KDE, but I really like the "simplicity" fo Gnome and KDE reminds me of Windows a bit. I'm not too fond of that.
Thanks for the help. :)

---

