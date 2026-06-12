---
title: "xorg.conf question"
date: 2006-09-28
forum: Apple PPC Users
---

### Post by FoggyMtn on 2006-09-28
Hey Ya'll

I just installed ubuntu on my emac (I'm running a server install as well as xubuntu on two other computers).  I ran into the blank screen when x starts.  I dropped to commandline and edited my /etc/X11/xorg.conf (I couldnt copy my apple one as it was erased).  I changed the horizsync to  70-73 and the vertrefresh to 70-140.  Still no luck.  I had to add:

ModeLine "1024x768" 99.190000 1024 1072 1168 1376 768 769 772 810 +hsync +vsync
ModeLine "1280x960" 122.24 1280 1328 1424 1696 960 961 964 1002 +hsync +vsync


Now everything works fine.  THe only thing is the screen is slightly shifted to the right.  Can someone explain to me what those two modeline entries actually do?  I just used a cut and paste from another post.  How do I shift the screen back to the left a little? 

Thanks for any help of explanations

Rob

---

### Post by RHTopics on 2006-09-28
You can use the command line utility **xvidtune** to adjust your display and then copy the resulting Modeline from **xvidtune** into your xorg.conf file.

see xvidtune's man page for more information on how to use it.

Below is an explanation of Modeline from the man page for xorg.conf.

> ModeLine  "name" mode-description

This entry is a more compact version of the Mode entry,  and  it
also  can  be used to specify video modes for the monitor.  is a
single line format for specifying video modes.   In  most  cases
this  isn’t  necessary because the built-in set of VESA standard
modes will be sufficient.

The mode-description is in four sections,  the  first  three  of
which  are mandatory.  The first is the dot (pixel) clock.  This
is a single number specifying the pixel clock rate for the  mode
in MHz.  The second section is a list of four numbers specifying
the horizontal timings.  These numbers  are  the  hdisp,  hsync&#8208;
start, hsyncend, and htotal values.  The third section is a list
of four numbers specifying the vertical timings.  These  numbers
are  the  vdisp,  vsyncstart,  vsyncend, and vtotal values.  The
final section is a list of flags specifying  other  characteris&#8208;
tics  of  the mode.  Interlace indicates that the mode is inter&#8208;
laced.  DoubleScan indicates a mode where each scanline is  dou&#8208;
bled.   +HSync  and -HSync can be used to select the polarity of
the HSync signal.  +VSync and -VSync can be used to  select  the
polarity  of the VSync signal.  Composite can be used to specify
composite sync on hardware where this is  supported.   Addition&#8208;
ally,  on some hardware, +CSync and -CSync may be used to select
the composite sync polarity.  The HSkew and VScan  options  men&#8208;
tioned  above  in  the  Modes entry description can also be used
here.


---

### Post by FoggyMtn on 2006-09-28
Cool!  THanks!  THat's what I needed to know... some light reading for tonight! :)

Thanks again!

rob

---

### Post by RHTopics on 2006-09-28
You're welcome.

Report back on how xvidtune worked out for you.

---

### Post by FoggyMtn on 2006-09-28
> **RHTopics said:**
> You're welcome.

Report back on how xvidtune worked out for you.



Slick as a peeled onion!! 

I just backed up my current and then ran the -show option.  Then, away we go!  I adjusted left and widened slightly.  Then, another -show and I copied that into my xorg.conf.


Man, knowing the right commands sure does make things easy!! ;)


Thanks for the tips

rob

---

### Post by RHTopics on 2006-09-28
That is good news that it worked well you.

You are right, knowing the right tools and commands does make things easier.

---

