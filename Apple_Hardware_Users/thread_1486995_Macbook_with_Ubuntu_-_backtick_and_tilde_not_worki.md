---
title: "Macbook with Ubuntu - backtick and tilde not working"
date: 2010-05-18
forum: Apple Hardware Users
---

### Post by BrianK on 2010-05-18
I'm guessing this is a simple one, but I can't seem to find how to get my backtick/tilde key doing what it's supposed to.  Currently, I get these chars with that key:

§ ±

My keyboard is set to US Macintosh.

TIA.

---

### Post by BrianK on 2010-07-22
bump.  Anyone else experiencing this?

---

### Post by amolweb on 2011-08-05
Similar problem with backtick/tilde key which transmits a left/right angle bracket over NX Player (Preview 5, version 4.0.132) on OS X Lion (10.7)

Does anyone know if there is a workaround by remapping the keys in anyway?

---

### Post by Karedhuran on 2011-09-01
Similar problem here, it says


Versionsdaten des X-Servers:
The X.Org Foundation
11001000


 &#8226; das Ergebnis von xprop -root | grep XKB
 &#8226; das Ergebnis von gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

I cant switch my Keyboard setup at isnt working doesnt matter what i try, i even reinstalled ubuntu. 
Any help, i searched for 2 days in a row, but nothing could help me.

(EDIT)

I know how to change the third level choosers by the way. And I tried to reset the settings via terminal config.

---

### Post by emesjay on 2011-09-29
For NX Player + Mac OS X Lion on my Macbook Pro, I fixed my problem by doing the following on my Ubuntu box:

```


# find out what key code is mapping to the "less" and "greater" signs
$ xmodmap -pk | grep greater
     60    	0x002e (period)	0x003e (greater)	
     94    	0x003c (less)	0x003e (greater)	0x007c (bar)	0x00a6 (brokenbar)	0x007c (bar)	0x00a6 (brokenbar)

# edit (or create) ~/.xmodmaprc and include the following line in it
keycode 94 = grave asciitilde

# run xmodmap
$ xmodmap ~/.xmodmaprc


```

Note that I mostly use this Ubuntu box over NX, and I don't know how this solution will work with different keyboards, or if it will adversely affect some key usage when using the Ubuntu box directly.

---

### Post by Scott Deagan on 2011-11-16
Thanks [emesjay]("http://ubuntuforums.org/member.php?u=1455297")!!!!!!! Solved the key mapping issue on my MacBook Pro 8,2 with Ubuntu 10.10 :)

---

### Post by mörgæs on 2011-11-17
Moved to the Apple forum.

---

