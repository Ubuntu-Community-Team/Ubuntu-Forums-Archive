---
title: "Firefox suddenly just won't start. :("
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by foundation on 2007-07-08
Okay, so I hit the Firefox icon and in the bottom panel it says "Starting Firefox" and stays there for 10 seconds or so then it just disappears and FF doesn't start.

Now, I hadn't used Ubuntu in about a week so nothing had changed. I tried reinstalling it via synaptic and it still won't start.

Any ideas why this would happen or common causes for this problem? Or is there a way I can make a log of FF starting and post it here to see what you people think or even fix the problem myself from looking at the log?

---

### Post by paradoc on 2007-07-08
possibly because you haven't got a wireless/wired connection to the Internet?

Thats the first place I'd look!;)

---

### Post by BL00dFox on 2007-07-08
Try This...

System -> Administration -> System Monitor
See if firefox is runnung and KILL the process. Try opening it again... Post back results

PS how are you accessing this forum w/out FF?

---

### Post by BL00dFox on 2007-07-08
> **paradoc said:**
> possibly because you haven't got a wireless/wired connection to the Internet?

Thats the first place I'd look!;)

Oh and BTW I dont think thats the case because if his connection was dead, FF would say "could not connect". It would have no problem Loading.

---

### Post by foundation on 2007-07-08
Well, I also have Opera, Epiphany and Konquerer installed so I have other means of posting on the net. :)

There was no Firefox process and I completely removed Firefox (And tt took a ton of other things with it), reset and then reinstalled and it still isn't starting. :(

---

### Post by jannevanhecke on 2007-07-08
i have that problem also sometimes, when you restart your pc the problem is over.

---

### Post by jrusso2 on 2007-07-08
If restarting does not work try starting it in safe mode.

./firefox -safe-mode

This happens sometimes due to using plugins

---

### Post by foundation on 2007-07-09
> **jrusso2 said:**
> If restarting does not work try starting it in safe mode.

./firefox -safe-mode

This happens sometimes due to using pluginsWhere should I run that from ? I tried Alt+F2 and in terminal and it says it cannot find ./firefox and I'm not sure where FF is installed exactly. D: Edit: I added -safe-mode to my FF icon and I've got into FF now (Thank you!) but for future reference how do I navigate through terminal to the base filesystem ?

---

