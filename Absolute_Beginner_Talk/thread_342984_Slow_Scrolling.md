---
title: "Slow Scrolling"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Duppy on 2007-01-20
Scrolling in Firefox2,  OpenOfficeWord and just about every other program is really slow and quite jumpy.
How do I sort this?

Also when moving windows around the desktop they go all jumpy and slow. 
When I open system monitor, it shows the CPU peaks when windows are moved around and scrolling. My laptop isn't really low spec so why is this happening?

I'm on a laptop, 512mb ram, 1.5ghz celeron M, and wireless Internet.
Ubuntu Edgy and Firefox 2.

---

### Post by jamesmorad on 2007-01-20
just a guess, seeing as how I dont know much about linux, but this always happened to me in windows in safe mode, when no graphics drivers were loaded. maybe you should try installing the drivers for your graphics card?

---

### Post by Duppy on 2007-01-20
VIA UniChrome SG3

Where will I find the drivers?

---

### Post by Duppy on 2007-01-22
Forget it, sorted it now.

---

### Post by mikewhatever on 2007-01-22
Why don't post the exact solution, so that others may benefit from it too.

---

### Post by DougS on 2007-02-06
Yes please let us know. This thread has come to a full stop and there must be loads of users having the same proble?
I really like the changes made in Edgy but it is useless to me if this scrolling problem isn't sorted.
There always seems to be a disappointing something which stops the setup being absolutely user friendly, especially New User Friendly.

Does anyone know why this is happening, please (ideally not just a do this then that then it's sorted because it usually isn't  - it's understanding I'm pleading for)
Thanks in anticipation...?

---

### Post by DougS on 2007-02-11
Well, I adjusted the colour depth by editing /etc/X11/xorg.conf (as I think I saw somewhere)  and whilst it did seem to make a difference (got down to 8 bit and horrible colours) it still wasn't back to normal speed scrolling so it looks as though it's something deeper (maybe drivers for my Gigabyte S series MB?)


It looks as though Edgy is off limits so I'll have to wait for the next version?

---

### Post by Tsi on 2007-02-18
That problem just started for me last night. 

I've been running Kubuntu since the end of last year and now I'm suddenly facing a problem to where it seems that every time I scroll a window, it renders itself again and again.

Anyone have any clue on how to fix this?

---

### Post by Birdman1962 on 2007-10-29
I solved the same problem by removing XGL that was installed with compiz fusion,
go to synaptics select All and search for XGL Right Click and remove...
XGL uses nearly 100% cpu time and not a lot of  GPU time........... open system monitor look at xgl in running programs and drag window ...........if this helps -: >} deseminate thru other forums.  If not let me know.......create new test user and try on that first.

os ubuntu gutsy
window manager gnome

                      Cheers

---

