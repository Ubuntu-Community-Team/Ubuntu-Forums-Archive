---
title: "D-Link DWL G630 Wireless cardbus"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by drowner on 2006-08-06
Hey guys. Have done a coupla searches for this on the forum. Not really able to understand :D or get the card working.

Could someone really dumb it down for me?

I have the XP driver copied across.

I did ndiswrapper -i to the driver, and that worked. Then i went to modprobe wlan0, and the cursor  just flashed at me, im not sure if anything happened.

No lights on the card.

Thanx.

---

### Post by drowner on 2006-08-06
Yeah, update:

I did cardctl ident

and so far i got

Socket 0:
   no product info available

Socket 1:




and thats it, its hung, or thinking, or something.

:confused:

---

### Post by drowner on 2006-08-08
no love? fair enough :D

---

### Post by drowner on 2006-08-19
Ill try one more bump....

i would really appreciate some help.

---

### Post by psycosmyth on 2006-08-19
just a guess since you are getting o's(know how you feel)
I found that the common Atheros driver works on most D-link things.
My pcmcia card run's great out of the box. Atheros does'nt have their chips in all the D-link stuff though, just a suggestion.

---

