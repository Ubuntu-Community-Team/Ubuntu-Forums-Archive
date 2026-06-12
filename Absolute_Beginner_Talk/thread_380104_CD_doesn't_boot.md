---
title: "CD doesn't boot"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by girizano on 2007-03-09
*** I'm very new to Ubuntu, just an old Windows hack, so pardon my stupidity. ***



Downloaded 6.10 and burned it to CD. All well, md5 ok too. Booted, choose option 'Install/run", saw some percentage boxes showing 'loading Unix' or something, then the Ubuntu logo and underneath the left-to-right ping-pong bar. That's it, I don't get any further, it's like it froze right there.

Also no CD-spinning, no keyboard lights, nada. Anyone?

Pentium 3 Ghz, nVidia fx5200, MS multi media keyboard (wired), MS wireless mouse.

---

### Post by oilchangeguy on 2007-03-09
i don't know if this will make a difference, but do you have a ps2 mouse you can try?

---

### Post by astrolabio on 2007-03-09
Look i had some problem installing from the Live cd.
The problem were related to my Acer notebook with Ati graphic card messy support.

I solved it simply using the alternate cd and installing edgy in text mode.
It worked very well and it's not more difficult at all (at least if you know to use tab to move from field to field).

You can find the alternate cd in ubuntu site. This for example is a link to the kubuntu alternate cd:
[http://ubuntu.supp.name/releases/kubuntu/edgy/kubuntu-6.10-alternate-i386.iso](http://ubuntu.supp.name/releases/kubuntu/edgy/kubuntu-6.10-alternate-i386.iso)
 
After you installed edgy in this way, if you still experence problems, they may be video card related.

You can solve that by installing envy
sudo apt-get install envy 
Envy is able to install and configure NVidia and Ati video card drivers. So if you have a different brand don't use it. 

It's a good thing to install the drivers anyway if you plan to use GoogleEarth, Beryl or some game like EnemyTerritory :guitar: 

To use envy just type envy in a console.
Then is pretty easy to use. Perhaps is better if you use it in recovery mode and then restart the system back in normal mode. 

This is what solved all my installation problems. I hope my experience might be of help for you.

---

