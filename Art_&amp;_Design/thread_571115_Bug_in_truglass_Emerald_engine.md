---
title: "Bug in truglass Emerald engine"
date: 2007-10-08
forum: Art &amp; Design
---

### Post by VictorR on 2007-10-08
There is a bug in the engine called truglass (for Emerald window manager), I don't know where to report it to.

[IMG]http://home.graffiti.net/vrull/truglass-bug.png[/IMG]

The gray line straight through the centre of the buttons, it is visible both on active and inactive headers. Can't get rid of it, no settings affect it.

Edited: Solved - change Glow Height to 11.5, so the line went BETWEEN physical pixels.

---

### Post by FuturePilot on 2007-10-09
Sure it's just not the theme?
I can't reproduce this.

---

### Post by VictorR on 2007-10-09
Yes, I am sure. The line is located at the top of Glow Height, and has the colour of Shadow :confused:

I changed all components to 100% transparency, and moved the line up (reduced Glow Height to 2). Here is the result:

[IMG]http://home.graffiti.net/vrull/truglass-bug-1.png[/IMG]

It is always window-wide, and can go beyond visual boundaries. And it is part of the shadow :lolflag:

---

### Post by JBAlaska on 2007-10-09
I think it's supposed to be a 3d effect-Bevel, if you modify the drop shadow it will look thusly;
[IMG]http://img360.imageshack.us/img360/2797/bevelqo2.png[/IMG]

---

### Post by VictorR on 2007-10-09
The bevel is clearly visible if one sets the contrast colours to some components. It goes on the same level as this line, but rounds down like the window corner. On the first picture on the inactive window the line becomes thicker from that point.

So it is not bevel. Seems it is something made for debugging and not removed in the final release.

---

### Post by FuturePilot on 2007-10-09
> **VictorR said:**
> Yes, I am sure. The line is located at the top of Glow Height, and has the colour of Shadow :confused:

I changed all components to 100% transparency, and moved the line up (reduced Glow Height to 2). Here is the result:

[IMG]http://home.graffiti.net/vrull/truglass-bug-1.png[/IMG]

It is always window-wide, and can go beyond visual boundaries. And it is part of the shadow :lolflag:

I mean try a completely different theme. I'm not seeing anything:confused:
Edit: Which Emerald are you using? The one in the Feisty repos?

---

### Post by VictorR on 2007-10-09
The theme is what I am trying to make. Here is how it looks currently:
[IMG]http://home.graffiti.net/vrull/theme.screenshot.png[/IMG]

The engine used on the picture is vrunner.
I would like it were like this:
[IMG]http://home.graffiti.net/vrull/truglass-bug-3.png[/IMG]

with truglass engine. It gives some volume to the window header, but it also draws this nasty line. Even on such a motley background this line is visible both on active and inactive titles.

Emerald themer is 0.5.2, engines: truglass 0.5, vrunner 0.2. Everything is from Ubuntu repositories.

The theme itself is published here
[http://gnome-look.org/content/show.php/Neutrino?content=67394]("http://gnome-look.org/content/show.php/Neutrino?content=67394")

---

### Post by VictorR on 2007-10-09
Where I was wrong that I had put the Glow Height exactly to 12.0, so this line went through physical screen pixels. After shifting it to 11.5 it virtually disappeared.

Thanks to everybody who tried to help me.

---

### Post by graigsmith on 2007-10-09
wow, this looks cool, how do i get this to work with my ubuntu? :)

---

### Post by VictorR on 2007-10-09
Sorry, did not understand your question.
> how do i get this (WHAT?) to work with my ubuntu?

---

