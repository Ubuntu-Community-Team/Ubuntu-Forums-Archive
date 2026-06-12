---
title: "is xVidTune the trick?"
date: 2006-01-21
forum: Apple PPC Users
---

### Post by erlyrisa on 2006-01-21
Hmmm I had this problem while I was using my studio G3 (semi opaque) 21" studio display with MS. - The studio display hasn't got manual display dimensioning and the soforth. Luckily I was able to find a refresh rate and resolution that almost fills the screen properly.

Now I'm using Kubuntu instead on the same monitor. Sadly it's refresh rates and resolutions that are selectable are unsuitable. - in all cases theres up to 3cm worth of black bordering the output.

Should I use xvidtune to try and change things, or can I make manual adjustments through xorg.conf.

-If xorg.conf is the only way to go I guess I'll have to make up values in there. (I think there is the next higher res but less bpp that will make everthing looks as it sort of should)

--but is there some sort of may to do manual dimensioning for the xserver's output , eg width height, rotation etc. ie just like the original os9 mac software driver could do?

ps - it's an offf the shelf standard g3 450 yosemite PowerMac.

Any suggestions would be great (I don't want to buy a flat panel just yet - besides it looks great having a neat g3 with KDE on - shame it's not on the screen properly)

---

### Post by erlyrisa on 2006-01-21
actually - I discoverd that yes it is. - You have to run it as the current xsession user. Then have a look at its modeline output (you press the button on the bottom which sends the current mode as a modeline config that is useable in xorg.conf to the terminal)

Now you have to copy that ouput and paste it into xorg.conf
under the monitors section. preceding it with the word 'Modeline' (try the man xorg.conf)

Whallaa!

---

