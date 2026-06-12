---
title: "Finished my first theme =D"
date: 2008-05-26
forum: Art &amp; Design
---

### Post by oedipuss on 2008-05-26
Used the clearlooks engine + some pixmaps for the scrollbars. 
The selection/active color (the green one) is customizable, and I've included a small script to colorize some pixmaps that aren't affected by gnome appearance/color customization.

Gtk theme : [http://www.gnome-look.org/content/show.php?content=81872](http://www.gnome-look.org/content/show.php?content=81872)
Wallpaper : [http://www.gnome-look.org/content/show.php/socket+svg?content=81873](http://www.gnome-look.org/content/show.php/socket+svg?content=81873)
Emerald theme : [http://www.gnome-look.org/content/show.php/SoftWhite?content=81867](http://www.gnome-look.org/content/show.php/SoftWhite?content=81867)
Metacity/GWD : [http://www.gnome-look.org/content/show.php?content=82067](http://www.gnome-look.org/content/show.php?content=82067)


Comments/suggestions welcome =D

---

### Post by Redrazor39 on 2008-05-27
AWESOME!!!!


BOOK MARKING FOR SURE!!!!


will contact you with comments, suggestions, etc. If I find anything to say or if you want me to :)

---

### Post by Chokkan on 2008-05-28
I really like this. Quite a fun looking theme. I'd also like to add to your workload by asking for a non-Emerald option :)

Nice work.

---

### Post by oedipuss on 2008-05-28
Thanks  =D
I'm trying to come up with a metacity/gwd theme but it seems it's significantly more complex than emerald or even gtk where the engine takes care of most things.. 
I like the idea of it blending nicely even in customized colors though, which isn't possible in emerald.
I'll upload it too when it's done.

---

### Post by Redrazor39 on 2008-05-28
the emerald theme isn't working for some reason... I downloaded it but it won't show up in emerald theme manager!

---

### Post by Redrazor39 on 2008-05-28
My titlebars aren't working; that's why I wanted the emerald theme. Is there any way to get the titlebars like that (left side x and all) without emerald?

Otherwise, could you please help me get this theme working in emerald? Thanks!

---

### Post by Redrazor39 on 2008-05-28
What icons are you using?

---

### Post by oedipuss on 2008-05-28
I added a basic metacity theme : [http://www.gnome-look.org/content/show.php?content=82067](http://www.gnome-look.org/content/show.php?content=82067)
It blends a little better with the sides of the menubar, and is customizable.

redrazor39: If it doesn't install from emerald, rename it to softwhite.tar.gz and extract it into ~/.emerald/themes 
It should find it then. I wonder why tho, maybe I zipped it wrong. 

Also, to change the button layout, open gconf-editor, find the entry at /apps/metacity/general/ named "button_layout" and change it from "menu:minimize,maximize,close" to "close,minimize,maximize:menu".

The icon theme I'm using is called AllGrey  : [http://www.gnome-look.org/content/show.php/ALLGREY?content=76814](http://www.gnome-look.org/content/show.php/ALLGREY?content=76814)
There's an AllBlack too, but it's kind of contrasty for this theme..

PS: yep I zipped it wrong :P It should work now

---

### Post by Redrazor39 on 2008-05-28
WOW! Thank you so much!

I love your theme now! I'm using a different icon set that is very cartoony but matches it very well. It's called Dropline Neu.


I've been searching for a great theme for an extremely long time now, and I've FINALLY found it! Thank you so much!

---

### Post by Redrazor39 on 2008-05-28
One thing I've been looking for in themes for a very long time is if the menubar could be merged with the titlebar. I think you should keep the titlebar as it is, but left align the menus after the maximize button and then if the title gets longer than that, make it so the title takes over and the menus are collapsed into a button that is shaped like a pressed in circle (like your x, -, [] buttons) with a wide triangle pointing down in it. When this button is clicked, File, Edit, View, etc. will be shown as subcategories.

Then, make it so the gradient that used to combine the titlebar and the menubar now combines the titlebar and the main toolbar in most applications.



As a later priority, make it so firefox does the same or make a firefox theme that works this way (for firefox 3, of course)

Also, with OpenOffice.org, make it so the gradient that now combines the menubar and titlebar combines the titlebar with all toolbars on top.


That would be incredible and awesome. This could also work as the next human theme with the green replaced by a light, soothing orange, but right now keep the green :)




I know this will be a lot of work, but it would be the best theme ever for ubuntu if implemented!

---

### Post by smartboyathome on 2008-05-28
That can't happen right now, Redrazor. It would require metacity being combined with gtk, which is against concept, as GTK is a toolkit, while Metacity is a window manager. Unless I misunderstand you?

---

### Post by oedipuss on 2008-05-28
I'd love, LOVE the menubar to be more flexible.. Right now it isn't possible to merge it to the titlebar, let alone collapse it into a button =(

On a relevant note, can a metacity theme be aware if a window has a menubar or not, and if so, does GWD support such functionality ? I'd like windows without menubars to look blended too if possible.. Window types alone can't make that distinction if I understood them correctly.

---

### Post by Redrazor39 on 2008-05-28
If concept is the only thing it's against, I say we should go for it and call it something different, credit GTK and Metacity accordingly, and name it something new. We can also add support for transparency almost anywhere and a whole bunch of other stuff. It would have to be seriously lightened up though... but I don't see why that's not possible.

Then we could do all that creative stuff with the menubar, toolbars, etc.

---

### Post by Nikayah on 2008-05-30
I just got this, and its AWSOME!!! I just wanna change the green to blue, so i use colorize and i get this:```
Emerald theme not found, unable to apply colors to button glow.
```Error, also what do i do after I use colorize? do I Re-Compress the file?? or how am I SUPPOSED to use it?
I apoligize for all my noobishness, but that is in fact what I am. I just installed Ubuntu - Hardy yesterday :guitar:

---

### Post by oedipuss on 2008-05-31
You just go in Gnome/Appearance/Customize,  and edit the color from there (colors tab) . The colorize script is only for the scrollbars in mouse over state, and for the button glow of the emerald theme. It prints this if it doesn't find the emerald theme, which should be normal if you're not using it.
If you're using the metacity theme, it gets the correct color by itself, I believe.
Say you went and changed the green to #D5F5C5 in the colors tab . You then run 
./colorize D5 F5 C5 , and reload the theme in Gnome Appearance (just select a different controls theme in Customize, and then back to softwhite) .

---

### Post by Nikayah on 2008-05-31
Ah, but i do have the emrald theme installed. AND I want my buttons to glow that color too.

---

### Post by oedipuss on 2008-05-31
ok my bash scripting skills are obviously subpar :P 
Be sure to run colorize from within ~/.themes/softwhite, it uses a relative path to check for the .emerald directory.

Look, if worst comes to worst, its just a silly little script. It should be easier to just fix the image yourself in gimp 

Just load the file "buttons.glow.png" located at ~/.emerald/themes/softwhite , lock transparency (the little checkbox above the layers) , bucket fill it to the color you want, and reload the theme from emerald manager.

---

### Post by Nikayah on 2008-06-01
Thanks! It worked!!:) Is there a way to change the selection colour (both text and buttons) from green to some other colour (blue)?

---

### Post by Redrazor39 on 2008-06-01
I love your theme so much. I also like the green.

Is there any chance you could make one like this but replace the green and other colors with orange, brown, and other Ubuntu colors? We could have a light theme with all the ubuntu colors and right now I'm using very cartoony icons but we could find more elegant ones for the default theme.

Could you do that please?

---

### Post by Chokkan on 2008-06-01
Yes.
**Preferences** > **Appearance** > **Customize...** (bottom of the window) then click the **Colors** tab and you can change the selected items colour.

---

### Post by Redrazor39 on 2008-06-04
When I change the color for selected items, it does not affect the scrollbars. How can I make the scrollbars the same shade of orange when I hover over them and click on them?

---

### Post by oedipuss on 2008-06-05
> **Redrazor39 said:**
> When I change the color for selected items, it does not affect the scrollbars. How can I make the scrollbars the same shade of orange when I hover over them and click on them?

run the 'colorize' script in /.themes/softwhite like so :
./colorize AA BB CC 
where AA BB and CC are the red green and blue values of the color you want in hex. 

On that note, is there a simple/fast pixmap engine that would allow for simple color transformations ? Or should I just modify the theme to use the experience engine, which afaik can handle that kind of thing? The problem with that is it doesn't seem to be in the official repos ..

---

### Post by Redrazor39 on 2008-06-05
When I try to do that, it says emerald theme not found. I downloaded your emerald theme but when I go into emerald theme manager and click import, then your emerald theme, nothing happens.

Then I still get this error.

Help?

---

### Post by oedipuss on 2008-06-05
nah nevermind that unless you want to use the emerald theme (metacity is better, emerald was just easier to make :P)

It should say that it did convert the scrollbars though, before complaining about emerald. When you reload the theme, are the scrollbars ok?

---

### Post by Redrazor39 on 2008-06-05
Now my scrollbars are some sort of bluish-green teal color. Maybe I got the redbluegreen wrong... I could've sworn I just copied and pasted them from some orangy color. I'll try again.

Also, I'd like to report a small cosmetic bug. The workspace switcher applet is supposed to be rounded off like a capsule, correct? The desktops within that capsule are not. To fix this, you either have to make the rounded outline wider in order to accomodate all desktops and their corners or you have to round the corners of the mini desktops. I think the first solution is easiest.

Just make the rounded outline of the desktop-switcher-panel-applet a bit longer so the corners of the desktop previews are completely within the outline and are not sticking out at all.

Great theme! With a few tweaks and a professional-looking icon theme, this could be the next default Ubuntu theme (or one of the defaults available)!!!

---

### Post by oedipuss on 2008-06-06
Thanks, I noticed that little bug too.. I'll try to isolate the desktop switcher and make its frame rectangular. 
Or would it be better to apply that to everything on the panel, like the menus ?

Dont forget the spaces between Red Green and Blue, all in hex.

---

### Post by Redrazor39 on 2008-06-06
I navigated to the location you specified and typed in 

./colorize 255 184 78

I think those are the numbers, but I know I entered the right ones. Is that how I should enter it?

---

### Post by oedipuss on 2008-06-07
./colorize ff b8 4e

Looks nice btw, more 'ubuntu' like than my green.

---

### Post by Redrazor39 on 2008-06-07
thank you!

When I have a very good icon theme with it, then I'll send you the links and info so you can check it out. I'm trying to make this a professional yet fun looking ubuntu theme.

---

