---
title: "Sound from more than one app?"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-04-12
Hello guys!

I was wondering, is it only possible to play sounds from one application at a time?

When I use any mp3 player and view something on the net that uses sound, there is no sound. Or if im viewing something from the web, my mp3 players or movieplayers wont play sound?

Is it possible to fix this?

---

### Post by evilgold on 2006-04-12
what sound system are you using... alsa shouldnt have problems playing more then one sound.

---

### Post by aktiwers on 2006-04-12
[QUOTE=evilgold]what sound system are you using... alsa shouldnt have problems playing more then one sound.[/QUOTE]

I am using Alsa.

Nvidia nForce2 (Alsa Mixer)

But I still have this problem?

---

### Post by micke1m on 2006-04-18
I've got exactly the same problem with a Soundblaster Audigy LS and ALSA. =(

---

### Post by mostwanted on 2006-04-18
Are you using Breezy or higher?

---

### Post by OffHand on 2006-04-18
How do you check which you are using?
I would like to hear two sound sources too. (music + game for instance)

---

### Post by mostwanted on 2006-04-18
[QUOTE=subsonic_shadow]How do you check which you are using?
I would like to hear two sound sources too. (music + game for instance)[/QUOTE]

What did you download? :p

Anyway, System > About Gnome

If it's 2.12 you have breezy

The others:
2.14 - dapper
2.10 - Hoary
2.8 - Warty

---

### Post by meborc on 2006-04-18
i think i solved that problem by installing alsa-oss and switching all programs output to alsa... it was a while ago though...

---

### Post by OffHand on 2006-04-18
[QUOTE=mostwanted]What did you download? :p

Anyway, System > About Gnome

If it's 2.12 you have breezy

The others:
2.14 - dapper
2.10 - Hoary
2.8 - Warty[/QUOTE]
<---- Like my info says I am running Breezey. I meant to say how do I check which 'driver' my sound is using? And how can I change it to another 'driver' that allows 2 sources.

---

### Post by meborc on 2006-04-18
[QUOTE=subsonic_shadow]...I meant to say how do I check which 'driver' my sound is using? And how can I change it to another 'driver' that allows 2 sources.[/QUOTE]
just open bmp (or whatever you use for music) and go options, output or smth... there should be a selection of what driver the player uses... and so with all apps... you have to change them all :mrgreen:

---

### Post by OffHand on 2006-04-18
[QUOTE=meborc]just open bmp (or whatever you use for music) and go options, output or smth... there should be a selection of what driver the player uses... and so with all apps... you have to change them all :mrgreen:[/QUOTE]ohh bummer, too bad I cannot change it in general. Thanks for the info.

---

### Post by micke1m on 2006-04-18
I've tried that but I still have the same problem.

---

