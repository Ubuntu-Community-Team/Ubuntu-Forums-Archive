---
title: "Nimbus Panels"
date: 2007-05-05
forum: Art &amp; Design
---

### Post by Churnd on 2007-05-05
I love the [Nimbus Theme]("http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755"), but I'd like to try to get the top taskbar back down to the same size as the bottom.  Anybody know how to do this?

---

### Post by ComplexNumber on 2007-05-05
> **Churnd said:**
> I love the [Nimbus Theme]("http://gnome-look.org/content/show.php/Nimbus+%28Ubuntu+and+Debian%29?content=54755"), but I'd like to try to get the top taskbar back down to the same size as the bottom.  Anybody know how to do this?
if i understand you correctly, just right click on panel, select 'properties', then reduce the size.

---

### Post by Churnd on 2007-05-05
> **ComplexNumber said:**
> if i understand you correctly, just right click on panel, select 'properties', then reduce the size.

The thing is, both panels say they're the same size.  I can't decrease the top size any lower than 23, and it doesn't change.  Here's a screenshot to show you what I mean:

---

### Post by ComplexNumber on 2007-05-05
> **Churnd said:**
> The thing is, both panels say they're the same size.  I can't decrease the top size any lower than 23, and it doesn't change.  Here's a screenshot to show you what I mean:
it seems that the lowest size a panel will go is 21.
go to the commandline and type in:
 killall gnome-panel

maybe something got stuck. i've just this minute installed the nimbus package so that i can help you, but i can't replicate what you have. here is my screenshot with a panel thats size 21. i made a new panel so i wouldn't mess up my setup (just in case).

---

### Post by Churnd on 2007-05-05
> **ComplexNumber said:**
> it seems that the lowest size a panel will go is 21.
go to the commandline and type in:
 killall gnome-panel

maybe something got stuck. i've just this minute installed the nimbus package so that i can help you, but i can't replicate what you have. here is my screenshot with a panel thats size 21. i made a new panel so i wouldn't mess up my setup (just in case).

That's strange.  I can't resize it that low.  I tried creating a new panel like you, but that didn't work.  I'm also using Beryl, so I switched back to Metacity... that didn't work either.  Whenever I select the nimbus icons for any theme, it increases the taskbar size.

I also tried killall gnome-panel, which didn't work either.

---

### Post by kpolice on 2007-05-05
Probably the problem is your big button on the corner, remove it and try again.

Other things that can limit how small your panel can be is the applets. Try removing them to find which one.

---

### Post by ComplexNumber on 2007-05-05
the menu bar is not available in the smaller sizes. thats the problem.

EDIT: the distributor-logo is found ONLY in the 32x32/places directory. so thats why the minimum size of the panel is going to be 32.


** Churnd**
downoad the attached icon and (assuming that you have your icons in /usr/share/icons), place it the following directory:
**/usr/share/icons/nimbus/24x24/places **(NOTE: you will need root access to place it there)if you have your theme stored in your home directory, then place the file in:[B]
~/.icons/[/B]**/nimbus/24x24/places**
then restart the theme by going to gnome-theme-manager, selecting another theme, then selecting nimbus icon theme again.

---

### Post by Churnd on 2007-05-05
> **ComplexNumber said:**
> the menu bar is not available in the smaller sizes. thats the problem.

EDIT: the distributor-logo is found ONLY in the 32x32/places directory. so thats why the minimum size of the panel is going to be 32.


** Churnd**
downoad the attached icon and (assuming that you have your icons in /usr/share/icons), place it the following directory:
**/usr/share/icons/nimbus/24x24/places **(NOTE: you will need root access to place it there)if you have your theme stored in your home directory, then place the file in:[B]
~/.icons/[/B]**/nimbus/24x24/places**
then restart the theme by going to gnome-theme-manager, selecting another theme, then selecting nimbus icon theme again.

That worked!  Nice!  Where did you get the smaller icon from?

---

### Post by ComplexNumber on 2007-05-05
> **Churnd said:**
> That worked!  Nice!  Where did you get the smaller icon from?
i made it myself. i just took the 32x64 icon and reduced it in size. the distributor-logo icon is the icon that a theme uses for the main menu. if the theme hasn't got one, it will use the distributor-logo of one of the themes that it 'inherits'(if you have a look in the index.theme file, you may see a line that says "Inherits=......". if the line isn't there, it will inherit the icon found in the gnome, Tango, or hicolor theme instead). HOWEVER, because the icon theme does have a distributor-logo icon, it used the only one that it has. and because it only has the distributor-logo in the 32x64 size, it uses that. therefore, the panel will always be at least 32 pixels high. if there is a smaller distributor-logo within the theme, it will use the one that closest to the size of the panel. therefore, because the icon that i gave you is a  better fit for your chosen panel size, it used that instead.
hope that makes sense.

---

### Post by Churnd on 2007-05-05
> **ComplexNumber said:**
> i made it myself. i just took the 32x64 icon and reduced it in size. the distributor-logo icon is the icon that a theme uses for the main menu. if the theme hasn't got one, it will use the distributor-logo of one of the themes that it 'inherits'(if you have a look in the index.theme file, you may see a line that says "Inherits=......". if the line isn't there, it will inherit the icon found in the gnome, Tango, or hicolor theme instead). HOWEVER, because the icon theme does have a distributor-logo icon, it used the only one that it has. and because it only has the distributor-logo in the 32x64 size, it uses that. therefore, the panel will always be at least 32 pixels high. if there is a smaller distributor-logo within the theme, it will use the one that closest to the size of the panel. therefore, because the icon that i gave you is a  better fit for your chosen panel size, it used that instead.
hope that makes sense.

Perfect sense.  I don't have experience designing themes, so I'm not sure how they integrate themselves into the OS yet.  Thanks for the explanation though, cleared up a lot!

---

