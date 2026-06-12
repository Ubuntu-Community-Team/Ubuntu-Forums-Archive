---
title: "Can't figure out WINE -- help!"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Ian Adkins on 2007-02-07
Having trouble with WINE.  Install programs *seem* to work, but all the text in the dialogue boxes are in Unicode soup.  If I manage to successfully guess the right boxes to click, the devil only knows where my program was installed to and how to execute it.  The program in this case is CorelDraw, which I assumed would work with WINE, given Corel's brief collaboration with the WINE developers.  I've also tried installing Windows drivers for my peripherals (no Linux option), likewise no dice.  What am I missing?  Keep in mind, when making your replies, that I am an Ubuntu neophyte with little understanding of terminal functions, kernels, sudo and whatever else.  I just wanted to break free from bondage under Microsoft, but I'm hoping to reclaim some of the functionality I had under Windows.  CorelDraw and printing, among them.

---

### Post by Patrick K on 2007-02-07
I can't really help much, but if the fonts are too small, I know how to fix that. 

Run regedit in winefile (type winefile in a terminal). It's in the C:\windows dir (click the C:\ button on the top). Important, make sure you're not in the real windows registry. Go to ```
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Hardware Profiles\Current\Software\Fonts
```There change, if it exist, or add the key LogPixels as a DWORD with a decimal value of 120, or 140 if 120 is too small. The larger the number the larger the font. I just found this today, so it's still fresh in my mind.

---

### Post by bodhi.zazen on 2007-02-07
[http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)

---

