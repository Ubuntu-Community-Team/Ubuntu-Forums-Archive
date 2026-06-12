---
title: "Urgent Help!!!!"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by mahela007 on 2008-03-18
I accidentaly srewed up the refresh rate of my monitor on ubuntu so now i cant see a thing.. (i cant make out a single letter on the screen. Does anyone know some keyboard shortcuts or **something / anything **that will help me reset the screen? pls help!!!

---

### Post by Wobedraggled on 2008-03-18
(ctrl alt f1) <------this will get you to console

Login as root, edit xorg.conf 

"nano /etc/X11/xorg.conf" find the section that shows the screens refresh rates, edit as needed.

now you can go back into X (ctrl alt f7) and then do a (ctrl alt backspace) or simply reboot.

That should do the trick.

---

### Post by mahela007 on 2008-03-18
thanks so much for the fast rep. could you explain a bit more pls? I'm quite a newbie to linux and even in windows i havent done anything outside games and other software

---

### Post by Wobedraggled on 2008-03-18
> **mahela007 said:**
> thanks so much for the fast rep. could you explain a bit more pls? I'm quite a newbie to linux and even in windows i havent done anything outside games and other software


The stuff in () hit those keys together, the stuff in "" just type as I did.

The section in xorg.conf will look something like this.


> Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	[B]Horizsync	31.5-65.5
	Vertrefresh	56.0 - 65.0[/B]


Edit the bolded part to match the settings for the monitor.

---

### Post by Dr Small on 2008-03-18
Open up a console by pressing:
```
CTRL + ALT + F1
```

Login, and then run:
```
sudo nano /etc/X11/xorg.conf
```

Scan down and find:
```
Section "Monitor"
```

You can set your refresh rate in this section.
Save it, by pressing:
```
CTRL + O
```

And exit:
```
CTRL + X
```

Then switch back to your display:
```
CTRL + ALT + F7
```

And restart X:
```
CTRL + ALT + SHIFT + BKSPC
```

See if that helps.

Dr Small

---

