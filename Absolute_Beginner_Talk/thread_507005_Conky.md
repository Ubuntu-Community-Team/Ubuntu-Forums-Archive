---
title: "Conky"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by KIFIKA on 2007-07-22
I recently installed conky and all, and it works great, does what i want it to do and everything. However one small problem is that every second or so it blinks, to refresh i guess? it just gets wicked annoying..anyone know how to stop this? or for it to do it less often.

---

### Post by felicity on 2007-07-22
Try adding 
```
Load “dbe”
```
in the Section “Modules” area of your xorg.conf file.

---

### Post by KIFIKA on 2007-07-22
> **felicity said:**
> Try adding 
```
Load “dbe”
```
in the Section “Modules” area of your xorg.conf file.


hmm, what is the directory for the xorg.conf ? 

like i mean /usr/ blah?

---

### Post by tomcheng76 on 2007-07-22
/etc/X11/xorg.conf

---

### Post by JesterDev on 2007-07-22
```

sudo gedit /etc/X11/xorg.conf

```

I suggest you make a backup first (any time you hacking/changing xorg.conf make a backup!)

```

sudo cp /etc/X11/xorg.conf xorg.conf.backup_Date

```
Where Date is put in the current date i.e. 08-23-07 or 082307

A backup most likely already exists, however if you've installed video drivers or other apps have made changes it's default conf. So make a new one. :)

---

### Post by KIFIKA on 2007-07-22
weird, just by putting in that line it, it completly destroed the whole xorg.conf file and made that whole blue screen come up and stuff, i was abloe to fix it, but that doesnt help my conky problem, since i put it back to normal..... :(

---

### Post by walkerk on 2007-07-22
> **KIFIKA said:**
> weird, just by putting in that line it, it completly destroed the whole xorg.conf file and made that whole blue screen come up and stuff, i was abloe to fix it, but that doesnt help my conky problem, since i put it back to normal..... :(

did you type it correctly?

first backup xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

my Module section: (add Load "dbe")
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
	**Load	"dbe"**
EndSection

```

this shouldn't hose your xorg config. if it does use the terminal to reset your xorg.conf from the backup..
 
perhaps you fat fingered something?

---

