---
title: "GDM - need help with positions of objects"
date: 2007-02-26
forum: Art &amp; Design
---

### Post by zami on 2007-02-26
I'm working on a GDM theme but I need some help.

I'm starting with the Ubuntu "Circles" them - it's basic and has the general layout I want, and I'm sure I'd be totally lost if I tried to start from scratch.

Anyhow, what I need help with is understanding the position terms, such as -

    <pos x="-20" y="-37" anchor="se"/>

anchor="se"
Am I right in assuming this means the "start point" for this object is the bottom-right corner?
And anchor="n" would be the top center?  And anchor="w" would be the left.  And so forth?

x="-20"
I assume this means -20 "somethings" to the left (x being left/right, y being up/down), but what are those "somethings"?  Is that pixels? Is that 20 out of 100? 20 out of 2000?  And what's going on when I see x="-%50" ?

Any help in this would be very appreciated.  I've looked around for some tutorials and came across this -
[http://live.gnome.org/GnomeArt/Tutorials/GdmThemes](http://live.gnome.org/GnomeArt/Tutorials/GdmThemes)
wich is a nice starting point, but doesn't go into this positioning jargon at all.

And of course I've tried just outright tinkering with the positions, but I haven't discovered any rhyme or reason to the coordinates.  All my changes to the .xml file result in a)no noticeable change, or b)my object goes right off the screen.  

Thanks!

-zami

---

### Post by zami on 2007-02-26
Well, I found a partial answer here
[http://www.gnome.org/projects/gdm/docs/2.8/thememanual.html](http://www.gnome.org/projects/gdm/docs/2.8/thememanual.html)

Still a little confusing as the x/y stuff is NOT going the directions I expected, and works from an edge instead of the center, but at least all the info is there!

Yes yes, I'm replying to my own question.  Someone might come to these forums with the same question... anything is possible, right?  Right??

:D

-zami

---

