---
title: "[SOLVED] Screen a lot darker in linux than in windows"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by ClearyA on 2008-03-30
Hey! i used to be a windows user, i grew tired of it, so now i use linux (FREEDOM AT LAST)! the only problem is, my screen is so much darker in linux than it ever was in windows... Ive tried all the obvious tricks of lightening it up using the Fn Brighten keyboard function, and it says it is as light as it goes... im still really just getting the hang of linux, so any ideas on how to brighten it? because it is actually causing me to be notious its so hard to read some things.. Thanks!

---

### Post by YldGuy on 2008-03-30
my screen was bit brighter to my liking.. decreasing the brightness brings down the color and the vibrance of the desktop. i found this little app called xgamma in cairo-dock which can adjust the gamma settings. it was defaulted to 1.00 but i put it at 0.70 and it gave great results.. black looked more black.. red came out nicely and the fonts were so good to look at. later when i removed cairo-dock and put AWN (avant window navigator) i searched for a similar app but couldnt get any as the Gamma wasnt permanent. After 5 mins of googling i found out that you can actually change the gamma settings in the "xorg.conf" file. I put the "Gamma 0.70 0.70 0.70" in the monitor section of my xorg and restarted the X. Bingo!. Gamma changed permanently and for good. Try increasing the Gamma a wee bit. Might solve your problem.

---

### Post by ClearyA on 2008-03-30
Hey thanks for the suggestion, ill tweak that a bit.  But i solved my problem by restarting and configuring some things in the system BIOS.  Thanks though!

---

### Post by Miljet on 2008-03-30
Is there any possibility that you could share just what you tweaked in the BIOS? It would be nice for others who may be experiencing the same problems.

---

