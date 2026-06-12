---
title: "theme manager wont change themes"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2007-01-15
i just installed edgy (along with beryl) but now my theme manager wont change themes. i click on a new theme but the colors in the application stay the same. the beryl themes work fine, but i want to change more than just the window border.

thanks!

---

### Post by ComplexNumber on 2007-01-15
i'm not too sure how you have it it set up. but it could for a number of reasons. do you have gtk2-engines(although i suspect that this can't be the reason because they have to be installed for you to run gnome properly) and gtk2-engines-pixbuf installed? 
to check to see of you have them installed, fire up synaptic(you will fin it in menu -> system -> administration) and do a search.


can you give us a screenshot to show us all what it looks like when you select the new theme? please also include a shot of the theme manager showing the themes that you have installed in the screenshot. to make a screenshot, go to your menu and select accessories.

is it the same for all themes that you try to select?

---

### Post by jinxjinx on 2007-01-15
yup those packs are installed. 
ya its like when i double click on clearlooks nothing happens...

---

### Post by ComplexNumber on 2007-01-15
> **jinxjinx said:**
> yup those packs are installed. 
ya its like when i double click on clearlooks nothing happens...
is it the same for all themes that you try to select?

sometimes it takes a moment or 2 to change. also, you only need to click it once to change it.
from your screenshot, it appears that the theme isn't using the right theming engine, even though you say that you have the engines installed. 
my screenshot shows what clearlooks should look like.


btw go to /usr/lib/gtk-2.0/2.10.0/engines and tell me if you have the clearlooks engine installed (its called libclearlooks.so).

---

### Post by jinxjinx on 2007-01-15
that file is there. and yes its the same for all themes i try. thats why it looks like nothing happens when i click on a theme...

i really appreciate your help...

---

### Post by ComplexNumber on 2007-01-15
i'm sure the problem is to do with the engine. a theme always looks like it does in your screenshot when there is something wrong with the engine. but what could it be :-k. 
does the default human theme look 'normal'?

earlier, i thought that beryl was somehow affecting the gtk themes, but it can't do because beryl is just a window manager like metacity. just to clutch at straws, i even tried to replicate your situation by selecting the beryl manager, then firing up the theme manager and selecting a random theme. the colours and theme loaded up fine when i selected a theme (except for metacity, but thats understandable when beryl is active).

---

### Post by jinxjinx on 2007-01-15
maybe i could try un-installing and reinstalling something?? im just not sure what could be broken...

---

### Post by ComplexNumber on 2007-01-15
> **jinxjinx said:**
> maybe i could try un-installing and reinstalling something?? im just not sure what could be broken...
it maybe a long shot, but reinstall gtk2-engines (DON'T uninstall then reinstall).

---

### Post by jinxjinx on 2007-01-15
tried that, didnt work
even tried using the file browser to go to location themes:/// URI and double clicking the themes that way and nothing happened. some themes asked if i wanted to change font, but thats about it. 

so i think its getting the command to change. its just not drawing it...

---

### Post by jinxjinx on 2007-01-15
well i dont know wtf is wrong but i dled gtk-theme-switch and ran gtk-theme-switch2 fm the command line and that worked

---

### Post by theh0g on 2007-01-17
Bump, same problem on my machine. I also run Beryl, but I don't see how that can be connected, did you figure anything out?

---

### Post by mcduck on 2007-01-17
Try running 'gnome-settings-daemon &' and if that helps add 'gnome-settings-daemon' to your session startup programs (in System/Preferences/session).

That should fix it. :)

---

### Post by Buck2348 on 2007-01-17
Were you trying to change metacity themes when Beryl was the active window manager?  I've tried something similar a few times and it doesn't work.  :-?

---

