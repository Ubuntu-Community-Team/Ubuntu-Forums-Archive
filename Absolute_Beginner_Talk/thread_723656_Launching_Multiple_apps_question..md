---
title: "Launching Multiple apps question."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by artilec on 2008-03-13
Hi, I been looking through the forums for this to no avail so was hoping for some help, so anyway here it goes!

I want to be able to launch the Terminal, Gedit and Nautilus into pre-determined positions on my desktop, simultaneously, would I need a script for this? or is this possible using something like compizconfig-settings-manager?  I been launching my apps with compiz (key binding) and hoped i could use this.

(edited)

Ok, so I now have 3 apps opening at once in desired locations on my desktop.

screenshot 1 shows (compizconfig-settings-manager - general options - commands) command line 7.

screenshot 2 shows (compizconfig-settings-manager - place windows - fixed window placement) 

screenshot 3 after (super)z is pressed.

Thanks to all that have replied to my post, I,m kinda there where i want with this for now  as I am stuck doing it via command line. This option has it's limitations!!

---

### Post by derekr44 on 2008-03-13
It is possible to have multiple programs open at the same time with a script.  As to the positioning... maybe someone else knows better than I...

---

### Post by dcraven on 2008-03-13
Many GTK apps come with a --geometry=GEOMETRY command line option. Have a look at 'gnome-terminal --help' for example.

~djc

---

### Post by artilec on 2008-03-13
Yes, I dont want the windows to overlap and want share the desktop between the three open windows, i,d prefer this for drag and drop folders to Terminal and copy and paste to terminal from gedit without window switching or workspace switching for that matter!

---

### Post by derekr44 on 2008-03-13
> **artilec said:**
> Yes, I dont want the windows to overlap and want share the desktop between the three open windows, i,d prefer this for drag and drop folders to Terminal and copy and paste to terminal from gedit without window switching or workspace switching for that matter!

probably a pooey question anyway , may not make much sense to u guys, not sure!

Oh don't worry.  I think your question makes sense.  I only know half the answer :lolflag:

---

### Post by p_quarles on 2008-03-13
Thread moved to Absolute Beginner Talk (the Cafe is mostly for off-topic discussions). :)

---

### Post by BluntBox on 2008-03-13
I use --geometry to position some terminal windows. And it is possible to use it on Nautilus too. But gedit doesn't have that option, and I can't find any other option to do the same thing.

To give you an example of --geometry though. here are my launchers for Irssi and rTorrent, to position them exactly where I want them:
```

gnome-terminal --window-with-profile=irssi --geometry=120x30+600+620 -x irssi
gnome-terminal --window-with-profile=rTorrent --geometry=120x30+600+200 -x rtorrent
```

Basically in the case of terminal windows: --geometry=AxB+C=D. Where A = width of the window in character columns, B = height in lines, C and D = distance from the top left of the screen in Pixels.

For nautilus though, A and B are pixel values as well.

You could look at Devilspie, though I have never used it so can't speak of its usefulness.

---

### Post by artilec on 2008-03-14
Thanks for your help guys, I have edited my original post with an update as problem solved.

---

