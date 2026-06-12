---
title: "web"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by SnowLinux on 2007-06-11
For those of us who don't know html coding yet,
what software is available for website building?

Is there anything for Linux that compares to the likes of Serif Webplus?
I.E. graphical rather than coding!

---

### Post by HotShotDJ on 2007-06-11
NVU -- use add/remove software or synaptic to install.  I don't know anything about the software you mentioned, so I can't tell you how it compares.  I use a text editor myself. :)

---

### Post by jcronkhite on 2007-06-11
You may also want to try [Blue Fish]("http://bluefish.openoffice.nl/index.html").  Also, if your wondering about other applications you should check out [The Linux Alternative Project]("http://www.linuxalt.com/").  Hope that helps!

---

### Post by rapolas on 2007-06-11
> **HotShotDJ said:**
> NVU -- use add/remove software or synaptic to install.  
It's not available on feisty repositories, anyway you can download it from here: [http://www.nvu.com/download.php](http://www.nvu.com/download.php)

---

### Post by HotShotDJ on 2007-06-11
:mad: Your right!  It was there in the Edgy repositories.  I wonder why they removed it from Feisty?!?

---

### Post by paparucino on 2007-06-11
> **SnowLinux said:**
> 
Is there anything for Linux that compares to the likes of Serif Webplus?
I.E. graphical rather than coding!
And don't forget **Amaya**, from w3c.

---

### Post by thesonisshining on 2007-06-11
how do you install amaya from terminal?

---

### Post by HotShotDJ on 2007-06-11
> **thesonisshining said:**
> how do you install amaya from terminal?
Hold that thought! :)  I never heard of Amaya before and just googled it.  Looks good -- and I trust the source!  Let me experiment a little bit and I'll post back.

---

### Post by thesonisshining on 2007-06-11
i just installed it through add/remove; but i would still like to know how.......maybe that's another thread.

---

### Post by paparucino on 2007-06-11
> **thesonisshining said:**
> how do you install amaya from terminal?
Go here [http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)
Get this [http://wam.inrialpes.fr/software/amaya/amaya_wx-9.55-1_i386-pre1.deb](http://wam.inrialpes.fr/software/amaya/amaya_wx-9.55-1_i386-pre1.deb)
Then open a terminal, move where you downloaded the above file an type
```

dpkg -i amaya*.deb

```

When finished you can type **amaya** from the terminal or go to the menu w look for it

---

### Post by HotShotDJ on 2007-06-11
```
apt-get install amaya
``` worked for me!  Looks NICE!  I'll have to play with it some. :)  Its a somewhat older version though... maybe I'll tempt fate and try downloading a more recent .deb from W3C. :)

---

### Post by thesonisshining on 2007-06-11
thanks paparucino.
thanks hotshotDJ.

---

### Post by H3g3m0n on 2007-06-11
I highly recommend you take the time to learn xhtml/css, it will be much better in the longrun, its fairly simple to learn. Although having a decent environment is still defiantly a good idea, just try and stay away from WYSIWYG editors.

---

### Post by jcronkhite on 2007-06-11
To add to the comment of avoiding WYSIWYG editors, I must say that most of the time, the useful feature is NOT the ability to make a web document, but to manage the site you're building.  That's why (at least to me) most of these editors have a CODE view for editing.  Most developers would highly recommend using the code view to create your pages.  This means you need to know XHTML/CSS at least.  But don't be intimidated.  It's really not that hard.  Spend a day or two with the basics and you'll feel relatively comfortable.  To learn quickly, go to [www.w3schools.com]("http://www.w3schools.com").  It's all there.

---

