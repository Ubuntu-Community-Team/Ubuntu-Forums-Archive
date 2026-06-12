---
title: "wine wants &quot;gecko&quot; when trying to run cs 1.6 server"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by eidam655 on 2007-11-01
hi,

finally succeded to run cs 1.6 :)

problem is, that when i try to run new server (for single player purposes only, e.g. with bots), the game stucks with "Parsing game info...", then a Wine message pops up - Wine needs Gecko... download? (this is not an exact description :)) when i agree with downloading, everything just freezes :(

what am i supposed to do? wait som 30 minutes and download it, or is there any other option how to run cs with bots?

thank you. :)

---

### Post by Factory on 2007-11-01
I've heard of a similar fix to get the gecko package... All I had to do was run Internet Explorer in Wine and it installed without a hitch.

---

### Post by snkmad on 2007-11-01
Type this in the terminal: wine iexplore [www.winehq.org](www.winehq.org)
Itll install gecko for you.

---

### Post by eidam655 on 2007-11-02
thanks :)

just one more question: how long does it take to download? i mean, how big is the package?

because now, when prompted, agree with downloading & installing the gecko, but then the download "freezes," i.e. doesn't do anything...

or maybe it's because i access the internet from behind a proxy? does wine need any special proxy settings? because in the Network Proxy preferences i have it correctly set up...

thx

---

### Post by snkmad on 2007-11-04
Well i never messed with proxy under linux.
But the install should be pretty much straight forward.

---

### Post by aikishugyo on 2007-11-12
See the 2 following explanations:

[http://www.winehq.org/pipermail/wine-users/2006-December/024103.html](http://www.winehq.org/pipermail/wine-users/2006-December/024103.html)

OK, I looked at the source code, and the installer just download the 
file from [http://source.winehq.org/winegecko.php](http://source.winehq.org/winegecko.php), so I did it myself:

wget [http://source.winehq.org/winegecko.php](http://source.winehq.org/winegecko.php)
cabextract wine_gecko.cab
mv wine_gecko ~/.wine/drive_c/Program Files/
wineboot
rm wine_gecko.cab

It worked perfectly.

[http://www.winehq.org/pipermail/wine-users/2006-December/024104.html](http://www.winehq.org/pipermail/wine-users/2006-December/024104.html)

Well, it wasn't exactly enough, I also had to add a key in the registry, 
using regedit : in HKCU/Software/Wine/MSHTML, the key GeckoPath with the 
value C:\Program Files\wine_gecko.

Cheers, G.

---

