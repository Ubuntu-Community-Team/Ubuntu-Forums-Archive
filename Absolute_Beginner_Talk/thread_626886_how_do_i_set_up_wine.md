---
title: "how do i set up wine"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2007-11-29
what is the best way to set up wine? i have used it before, but most (if not all) of the programs i have run with it have been buggy or would refuse to start. some more info would also be nice. 

thank you

---

### Post by nikoPSK on 2007-11-29
sudo apt-get install wine
:)

---

### Post by zvacet on 2007-11-29
You can try [Wine-doors](http://www.wine-doors.org/wordpress/?page_id=3) or [wine review](http://wine-review.blogspot.com/)

---

### Post by nikoPSK on 2007-11-29
I never (even after reading the about) understood what wine0doors was for.

---

### Post by oeolycus on 2007-11-29
There's a whole [forum]("http://ubuntuforums.org/forumdisplay.php?f=313") [here]("http://ubuntuforums.org/showthread.php?t=624436") for [these]("http://ubuntuforums.org/showthread.php?t=497332") questions :)

---

### Post by PmDematagoda on 2007-11-29
Basically you install Wine using:-
```

sudo apt-get install wine
```

and configure it using either:-

```
winecfg
```

or Wine-doors.

nikoPSK, Wine-doors is a tool that can be used to install certain software and games on Wine and also configures Wine on it's first start-up.

---

### Post by nikoPSK on 2007-11-29
well, does it require you to have the thing? I tried getting some games but it froze....

---

### Post by PmDematagoda on 2007-11-29
No, it is not essential that you use Wine-doors, but what happened with the games? What went wrong?

---

### Post by nikoPSK on 2007-11-29
I tried to install half life just by selecting it and clicking install, but It froze. I managed to install ie (but who wants it...) but couldn't remove it.

---

### Post by PmDematagoda on 2007-11-29
I'm not sure about removing IE, but there is an option for installing Half-life 2 on WIne in Wine-doors but that may not work for you, what is the error you get when you try to run the game?

---

### Post by nikoPSK on 2007-11-29
no, the installation hangs....

---

### Post by PmDematagoda on 2007-11-29
Hmm, very strange, did you try installing the game in Windows to see if it is a problem with the CD?

---

### Post by nikoPSK on 2007-11-29
it's fine in windows....

---

### Post by thebestofall007 on 2008-01-16
i found a copy of windows xp professional that i have installed in innotek virtual box that i use to run windows applications in (thats if and only if the program only works with windows, I HATE WINDOWS TO BEGIN WITH).   Im just glad that I dont have to reboot my machine on that grotesque windows vista again if i need (need?) to run windows apps!!! 

btw, whats is the difference between using a virtual machine running windows versus wine?

---

### Post by nikoPSK on 2008-01-16
> **thebestofall007 said:**
> i found a copy of windows xp professional that i have installed in innotek virtual box that i use to run windows applications in (thats if and only if the program only works with windows, I HATE WINDOWS TO BEGIN WITH).   Im just glad that I dont have to reboot my machine on that grotesque windows vista again if i need (need?) to run windows apps!!! 

btw, whats is the difference between using a virtual machine running windows versus wine?

vm, 100% anything in windows will run. wine, sometimes glitchy and 75% or more or less will run.

---

### Post by thebestofall007 on 2008-02-29
> **nikoPSK said:**
> vm, 100% anything in windows will run. wine, sometimes glitchy and 75% or more or less will run.

Okay, i just found a problem with vm: when i tried to use the creative zen recovery tool from [www.creative.com](www.creative.com) support link that recovers the firmware on my zen stone through the virtual pc, it would stop at he point where it wrote the boot manager and then give an error. the process of updating my mp3 player stopped and bricked it, three times. unfortunately, i had to boot into that GROTESQUE vista. it worked in vista. why wouldnt vm fix my players firmware with the xp? if i could run this tool in wine, how do i do it and will it work?

---

