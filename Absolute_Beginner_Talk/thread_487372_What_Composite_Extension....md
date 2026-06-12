---
title: "What Composite Extension..."
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by toasty_ghosty on 2007-06-29
Been using Ubuntu for about 12 hours and loving it. But after installing the ATI drivers and fixing the resolution and the such I went to enable the desktop effects and got "The Composite extension is not available". Any ideas?

---

### Post by swisscow on 2007-06-29
It's those ATI drivers thing again...

The fglrx drivers don't seem to play nicely with composite - I can't have the two together(can depend on the particular card though I believe).

I'm sure if you did a search with your card model you'l find a solution and get those effects back. The solution will probably involve reverting to the Ubuntu radeon drivers and AIGLX or using the fglrx drivers and XGL.


Best of luck

---

### Post by starcraft.man on 2007-06-29
> **toasty_ghosty said:**
> Been using Ubuntu for about 12 hours and loving it. But after installing the ATI drivers and fixing the resolution and the such I went to enable the desktop effects and got "The Composite extension is not available". Any ideas?

(assuming your card supports it)
Have a look at your xorg, I noticed this oddly enough in lots of other folk though its never happened to me. Scroll to the bottom and check the section should be labelled composite extension, make sure its set to either 1 or enable.

To get to the xorg.conf run this command:

```
gksudo gedit /etc/X11/xorg.conf
```

If you don't see it or are unsure what to edit, paste it here in code tags. I'm tired so I'm gonna turn in, someone else can help ya if ya run into any trouble. Gnight.

---

### Post by toasty_ghosty on 2007-06-29
I take it that this is what your talking about

EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

but when I change that to one I still get the same error...no I take that back. I get that they cannot be enabled. awesome.

---

### Post by swisscow on 2007-06-29
The fglrx drivers do not support composite, so enabling it won't work. 

If you want the desktop effects do a search for ATI and Beryl or ATI and effects - there are plenty of guides out there. But be aware, not all seem to work so take note which guides you are following

You will either end up with radeon+AIGLX or fglrx+XGL

---

### Post by toasty_ghosty on 2007-06-30
What about Compiz? Is that the same as well?

---

