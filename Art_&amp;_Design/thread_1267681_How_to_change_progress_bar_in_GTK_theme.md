---
title: "How to change progress bar in GTK theme??"
date: 2009-09-16
forum: Art &amp; Design
---

### Post by maxsideburn on 2009-09-16
Ok guys after doing tons of research the one thing I cannot seem to find any info on his how to actually change the look of a progress bar in a GTK theme. 

Basically what I'm wanting to do it take the standard "Human" progress bar, but instead of it being light-orange/darker-orange candystriped, I want to make it white and a very dark grey (very contrasting).

I give up on figuring this one out myself. Someone must know. GTKRC files don't seem to contain much stuff about progress bars, but apparently they're somehow getting drawn. I really wish it was just a graphic file I could edit in Gimp.

---

### Post by maxsideburn on 2009-09-16
I'm basically wanting to do something like this:

[[IMG]http://img12.imageshack.us/img12/7180/screenshotdj.png[/IMG]](http://img12.imageshack.us/i/screenshotdj.png/)


I did that in the Gimp using a screenshot I took of Human GTK. I just can't seem to find where in the GTKRC that those colors are defined.

---

### Post by maxsideburn on 2009-09-16
anybody?

or can someone at least point me to a forum where someone would know? somebody, somewhere must know how to edit these files, I mean people make GTK themes all of the time so somebody knows.

---

### Post by carolinason on 2009-10-19
same questions here too..., Anybody?

---

### Post by iKonaK on 2009-10-20
The answer is probably at :
```
http://live.gnome.org/GnomeArt/Tutorials/
```

---

### Post by Exodist on 2009-10-21
> **maxsideburn said:**
> I'm basically wanting to do something like this:

[[IMG]http://img12.imageshack.us/img12/7180/screenshotdj.png[/IMG]](http://img12.imageshack.us/i/screenshotdj.png/)


I did that in the Gimp using a screenshot I took of Human GTK. I just can't seem to find where in the GTKRC that those colors are defined.

As much as I would love to explain it step by step, I would end up typing a wall of text a mile long. So I will try to point it out as best as I can short and to the point.

- First you will have to use the Pixbuff (pixmap) engine for this.
- You will be using 2 layers, a main tilled layer for the candycane background (stretch set to false). The second top layer (overlay) will be a highly translucent overlay that makes the image appear beveled. The overlay stretch will be set to true.
- Also currently no way to animate it.. /cry 


Hope that helps..

---

