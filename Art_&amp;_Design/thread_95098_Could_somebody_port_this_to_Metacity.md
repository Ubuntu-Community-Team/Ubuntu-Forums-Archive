---
title: "Could somebody port this to Metacity?"
date: 2005-11-25
forum: Art &amp; Design
---

### Post by Gnobody on 2005-11-25
This would be an incredible decoration for Metacity, especially if it picked-up your GTK colours.

---

### Post by bvc on 2005-11-25
pretty snazy!
I agree it would be nice to see someone do a class job with metacity code on this though, so the gtk colors are used. I can tell ya the code for metacity is a cross between;
Clearbox
[http://gnome-look.org/content/show.php?content=25060](http://gnome-look.org/content/show.php?content=25060)
and SystemG
[http://gnome-look.org/content/show.php?content=19800](http://gnome-look.org/content/show.php?content=19800)
but mostly SystemG...
...then change buttons.

Oh, and don't expect small top corners like that either. They can either be big or square. At least, I don't know how to make them small.

---

### Post by towsonu2003 on 2005-11-25
nice stuff... tempting me to try Fedora Core 5 when it is out... :p

---

### Post by bvc on 2005-11-26
until someone does this....see alternative download here
[http://gnome-look.org/content/show.php?content=31741](http://gnome-look.org/content/show.php?content=31741)

---

### Post by bvc on 2005-11-26
[QUOTE=Gnobody]This would be an incredible decoration for Metacity, especially if it picked-up your GTK colours.[/QUOTE]BTW: where would someone find the original? source? That's xfce4 but I do not see that at xfce-look. Does it come with the latest version or something?

---

### Post by Gnobody on 2005-11-27
[QUOTE=bvc]BTW: where would someone find the original? source? That's xfce4 but I do not see that at xfce-look. Does it come with the latest version or something?[/QUOTE]

I've seen it in several screenshots of XFCE 4.3, I'm guessing it is a default theme.

---

### Post by tanari on 2005-11-27
**Gnobody**
How did you make nautilus to look in such way?

---

### Post by bvc on 2005-11-28
I've been tinkering so that it'll use gtk colors...but I need those buttons....don't feel like making them :???: 
[IMG]http://kwh.kernow-gb.com/~bvc/theme/devel/port.png[/IMG]
big round or cornered? Metacity can not do small round. Round will be hard for me in metacity code, but I'll give it a go.

---

### Post by Gnobody on 2005-11-28
Squared looks great, Ill try to make the buttons if I get time.

---

### Post by bvc on 2005-11-29
shouldn't they be here? ....somewhere? I don't know the name of the theme.

[I'm almost ready for them.]("http://kwh.kernow-gb.com/~bvc/theme/devel/port1.jpg")

---

### Post by graphic23 on 2005-11-29
[QUOTE=bvc]BTW: where would someone find the original? source? That's xfce4 but I do not see that at xfce-look. Does it come with the latest version or something?[/QUOTE]

Hey, 
    Thats the new default theme for Xfce SVN. Its pretty awesome (the xfwm4 theme and xfce4 svn) :)

---

### Post by bvc on 2005-11-30
[QUOTE=bvc]shouldn't they be here? ....somewhere? I don't know the name of the theme.

[I'm almost ready for them.]("http://kwh.kernow-gb.com/~bvc/theme/devel/port1.jpg")[/QUOTE]

silly me...forgot to put the link :???: 

here
[http://svn.xfce.org/svn/xfce/xfwm4-themes/trunk/themes/](http://svn.xfce.org/svn/xfce/xfwm4-themes/trunk/themes/)
but which one is it?

---

### Post by bvc on 2005-11-30
[IMG]http://kwh.kernow-gb.com/~bvc/theme/devel/port2.png[/IMG]
I finally got the light line on the left and right titlebar to be gradient. I then gave it an actual border instead of the sudo 1px/the rest bg[NORMAL] mess that looks bad in a trans terminal, as in the previous screenshot and the xfce4.3 screenshot. It's a 3px border making it more usable, but 4px was too big for the sleek look of the theme. What do ya think?
Just have to get the maximized and shaded states.

[http://kwh.kernow-gb.com/~bvc/theme/devel/port3.jpg](http://kwh.kernow-gb.com/~bvc/theme/devel/port3.jpg)

---

### Post by graphic23 on 2005-11-30
[QUOTE=bvc][IMG]http://kwh.kernow-gb.com/~bvc/theme/devel/port2.png[/IMG]
I finally got the light line on the left and right titlebar to be gradient. I then gave it an actual border instead of the sudo 1px/the rest bg[NORMAL] mess that looks bad in a trans terminal, as in the previous screenshot and the xfce4.3 screenshot. It's a 3px border making it more usable, but 4px was too big for the sleek look of the theme. What do ya think?
Just have to get the maximized and shaded states.

[http://kwh.kernow-gb.com/~bvc/theme/devel/port3.jpg](http://kwh.kernow-gb.com/~bvc/theme/devel/port3.jpg)[/QUOTE] 


[http://svn.xfce.org/svn/xfce/xfwm4/trunk/themes/default/](http://svn.xfce.org/svn/xfce/xfwm4/trunk/themes/default/) 

This is what you are looking for. Thanks for the nice theme. I cannot wait for it to release! :D is there a way to get the theme as it is in development?

---

### Post by Gnobody on 2005-11-30
Good, now I don't have to finish my buttons!  They were turning out like crap anyway.

---

### Post by bvc on 2005-12-01
[QUOTE=graphic23][http://svn.xfce.org/svn/xfce/xfwm4/trunk/themes/default/](http://svn.xfce.org/svn/xfce/xfwm4/trunk/themes/default/) 

This is what you are looking for. Thanks for the nice theme. I cannot wait for it to release! :D is there a way to get the theme as it is in development?[/QUOTE]Thx for pointing it out!!! Here's the undone devel version
[http://kwh.kernow-gb.com/~bvc/theme/devel/undone.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/devel/undone.tar.gz)

[QUOTE=Gnobody]
Good, now I don't have to finish my buttons! They were turning out like crap anyway.[/QUOTE]Thx for the effort anywhoo!

---

### Post by bvc on 2005-12-02
finished the maximized and shaded states (I think)
[SystemGX]("http://kwh.kernow-gb.com/~bvc/theme/mcity/SystemGX.tar.gz")
Please inform me of any problems.
[Screenie]("http://kwh.kernow-gb.com/~bvc/theme/screenshots/SystemGX.jpg")

---

### Post by Gnobody on 2005-12-02
^ That looks great, your a theming machine BVC!  I can't wait to see the finished theme with buttons!! :p

---

### Post by graphic23 on 2005-12-02
[QUOTE=bvc]finished the maximized and shaded states (I think)
[SystemGX]("http://kwh.kernow-gb.com/~bvc/theme/mcity/SystemGX.tar.gz")
Please inform me of any problems.
[Screenie]("http://kwh.kernow-gb.com/~bvc/theme/screenshots/SystemGX.jpg")[/QUOTE]

Really Nice. Where can i get the Clearlooks-6x theme, btw? It looks nice. :)

---

### Post by bvc on 2005-12-03
[QUOTE=graphic23]Really Nice. Where can i get the Clearlooks-6x theme, btw? It looks nice. :)[/QUOTE]
Thx! Here's 6x
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks-6x.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks-6x.tar.gz)
just threw it together so everything may not be 'exactly' like the default for clearlooks-0.6.x but I know the SELECTED color and bg is.

[QUOTE=Gnobody]^ That looks great, your a theming machine BVC! I can't wait to see the finished theme with buttons!![/QUOTE]Thx!
Hopefully tomorrow!!!

---

### Post by bvc on 2005-12-03
Gonna be busy for the rest of the day so here's what I have so far;

download
[http://kwh.kernow-gb.com/~bvc/theme/devel/undone.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/devel/undone.tar.gz)

screenie
[http://kwh.kernow-gb.com/~bvc/theme/devel/port4.jpg](http://kwh.kernow-gb.com/~bvc/theme/devel/port4.jpg)

need to redraw the right titlebar because I need to move the buttons over as they're too close to the edge. Let me know of any other issues...like inactive window prelight buttons, because I can't seem to invoke the state. Anyone know a sure way to invoke this? Seems to happen whenever it decides to or something. I realize the shaded window close button changes color, but I kinda like it. You?

---

### Post by Gnobody on 2005-12-03
EXCELLENT! My precious! My precious! ;)

---

### Post by graphic23 on 2005-12-03
[QUOTE=bvc]Thx! Here's 6x
[http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks-6x.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/clearlooks/cairo/Clearlooks-6x.tar.gz)
just threw it together so everything may not be 'exactly' like the default for clearlooks-0.6.x but I know the SELECTED color and bg is.

Thx!
Hopefully tomorrow!!![/QUOTE]


Thank you very much! and I'm awaiting the "complete" release. :) But it looks really great now!

---

### Post by bvc on 2005-12-03
Oh, then I won't bother making it better :p

just joking!
[http://gnome-look.org/content/show.php?content=32167](http://gnome-look.org/content/show.php?content=32167)
[http://gnome-look.org/content/show.php?content=32169](http://gnome-look.org/content/show.php?content=32169)

---

### Post by raublekick on 2005-12-03
excellent! i've been following this from the beginning, glad to see the finished product.

---

### Post by graphic23 on 2005-12-04
Nice Job! I love it! Exact copy of the Xfce Default theme. I liked the SystemGX and Unity. :)

---

### Post by Gnobody on 2005-12-04
It's great but the button spacing is still dependant on the font size and the title text doesn't fade as it gets near the buttons like in SystemG or Clearlooks.  But keep up the excellent work!


Also, AFAIK the reason metacity doesn't support "mini-round" boarders is because it doesn't support transparent png images as edges, like XFWM.

---

### Post by curtis on 2005-12-04
Where can I actually download the theme for XFWM?
As I run that inside GNOME instead of Metacity...
Thanks.

---

### Post by Gnobody on 2005-12-04
XFCE svn has it, it's the default theme for 4.399+



BVC, what GTK theme is [this]("http://gnome-look.org/content/preview.php?preview=2&id=32167&file1=32167-1.png&file2=32167-2.jpg&file3=&name=Unity&PHPSESSID=012e78decca719fcd47977099aa508df")?

---

### Post by graphic23 on 2005-12-04
[QUOTE=Gnobody]XFCE svn has it, it's the default theme for 4.399+



BVC, what GTK theme is [this]("http://gnome-look.org/content/preview.php?preview=2&id=32167&file1=32167-1.png&file2=32167-2.jpg&file3=&name=Unity&PHPSESSID=012e78decca719fcd47977099aa508df")?[/QUOTE]

I believe that is Human-In-Blue. 

@ Curtis, the theme is actually part of the SVN Xfwm4 so you can run svn co on the svn xfwm4 and then you'll have the theme.

---

### Post by bvc on 2005-12-05
> **Gnobody]It's great but the button spacing is still dependant on the font size and the title text doesn't fade as it gets near the buttons like in SystemG or Clearlooks.  But keep up the excellent work!


Also, AFAIK the reason metacity doesn't support "mini-round" boarders is because it doesn't support transparent png images as edges, like XFWM.[/QUOTE]
Since the buttons are pixmap and not scalable the button spacing should be dependant on the font size, because little buttons would look really silly too close to each other on a fat titlebar, so it helps equal out the look and feel.

Text doesn't fade on any theme. It just disappears based on said:**
> Human-In-Blue[/URL]

[QUOTE=curtis]Where can I actually download the theme for XFWM?
As I run that inside GNOME instead of Metacity...
Thanks.
wget -r --level=1 [http://svn.xfce.org/svn/xfce/xfwm4/trunk/themes/default/](http://svn.xfce.org/svn/xfce/xfwm4/trunk/themes/default/)

---

### Post by bvc on 2005-12-05
oh yeah...> Also, AFAIK the reason metacity doesn't support "mini-round" boarders is because it doesn't support transparent png images as edges, like XFWM.are you saying....in code, it is not possible? I find that, well, just about impossible. But then I'm not a coder. Seems to me someone just needs to edit the source to make it possible. If not, then what is metacity gonna do with cairo? Nothing? If metacity can't, and gnome wants a unified desktop (as everyone claims), someone better get to developing gnome's next wm ;)

---

### Post by bvc on 2005-12-07
Just a quick mockup of what I mean by mini round to better match the clearlooks widgets.
[http://kwh.kernow-gb.com/~bvc/theme/devel/22.png](http://kwh.kernow-gb.com/~bvc/theme/devel/22.png)
...ooops...forgot to put opus3 in there....
I have been looking through the source code but.. :???:

---

### Post by bvc on 2005-12-08
:???: 
I added opus3 to the mockup
:rolleyes: 
I'm shocked that an option for number of pixels to round doesn't interest anyone.

BTW: what I'm talking about has nothing to do with trans png edges, but only the number of pixels that round. Currently it is 5px. Some nice mac themes go 7px. I'd like to see a way to set a value="" for each corner starting at 7px down to 1px, and if a value is not set then default to the current 5px so not to mess whith all the current round themes.

What I have found in the source and changed to 3 from 5 did nothing, so I'm missing something or a lot, but do not know what, since I don't understand the code :???:

---

### Post by bvc on 2005-12-13
[QUOTE=Gnobody]It's great but the title text doesn't fade as it gets near the buttons like in SystemG or Clearlooks.[/QUOTE]
I figured that out :rolleyes: 
You'll have to excuse the old pixmap themer :p 

Since gnome-look is still down I thought I'd tell ya'll about it
[http://kwh.kernow-gb.com/~bvc/theme/mcity/Unity.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/mcity/Unity.tar.gz)

and the updates the SystemGX
-added an Unfocused version
-touched up all buttons
-more noticable prelight buttons
-new restore buttons
[http://kwh.kernow-gb.com/~bvc/theme/mcity/SystemGX.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/mcity/SystemGX.tar.gz)

---

### Post by bvc on 2005-12-14
There were a few probs with the above version of SystemGX and SystemGX-Unfocused that are fixed now. Hopefully I'm done.
[http://gnome-look.org/content/show.php?content=32169](http://gnome-look.org/content/show.php?content=32169)

---

### Post by bvc on 2005-12-14
[TODO]just thought of one more update coming that will improve performance.

---

### Post by curtis on 2005-12-15
[QUOTE=bvc]
wget -r --level=1 [http://svn.xfce.org/svn/xfce/xfwm4/trunk/themes/default/](http://svn.xfce.org/svn/xfce/xfwm4/trunk/themes/default/)[/QUOTE]
I just ended up getting the whole trunk, wanted to get the latest XFCE anyway :)

---

### Post by bvc on 2005-12-17
[Updated Unity]("http://gnome-look.org/content/show.php?content=32167")
-button spacing is now independent from font size (had several request for it so, majority wins)
-active window font is now white and not from gtk bg[NORMAL] color, which caused problems with themes with a dark bg[NORMAL]

[Updated SystemGX]("http://gnome-look.org/content/show.php?content=32169")
-active window font is now white and not from gtk bg[NORMAL] color, which caused problems with themes with a dark bg[NORMAL]

---

### Post by bvc on 2005-12-17
[SystemGX Update]("http://gnome-look.org/content/show.php?content=32169")
-new inactive buttons that match the inactive title

---

### Post by bvc on 2005-12-24
[Unity Update]("http://gnome-look.org/content/show.php?content=32167")-new title adds more readabilty, especially on lighter themes where the white blended into the titlebar.
[screenshot]("http://gnome-look.org/content/pre2/32167-2.png")

---

