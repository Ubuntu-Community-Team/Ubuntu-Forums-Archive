---
title: "Please help..."
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-26
[IMG]http://i109.photobucket.com/albums/n75/03davist/Untitled-7.png[/IMG]

it was easier to make a picture :)

Is it even possible without changing the windows colour?

---

### Post by nitro_n2o on 2008-03-26
right click on the panel and you can specify any color you want. 
I think that the glossy green effect is done using an image as the background. 
have a look at [www.gnome-look.org/](www.gnome-look.org/) and art.gnome.org/ you'll find lots of themes

---

### Post by YotoshiWii on 2008-03-26
Right Click (On the panel)--->Properties--->Background

---

### Post by Tom--d on 2008-03-26
Yeah I know that but look what happenes when I do..

---

### Post by Tom--d on 2008-03-26
> **YotoshiWii said:**
> Right Click (On the panel)--->Properties--->Background

I have already used that with the green panel background. Im talking about when opened a window. The colour goes gray.

---

### Post by SunnyRabbiera on 2008-03-26
that goes on how the theme is configured.
I know when I minimize my apps my tasks turn transparent and when I maximize them they turn blue.

---

### Post by Tom--d on 2008-03-26
> **SunnyRabbiera said:**
> that goes on how the theme is configured.
I know when I minimize my apps my tasks turn transparent and when I maximize them they turn blue.

How did you get them to turn blue when maximized?

---

### Post by SunnyRabbiera on 2008-03-26
I customized my themes.
you had another topic on this matter, and I asked you if you used themes from gnome look or if you use the themes pre provided by the OS.
It goes back to the same thing, editing the gconf theme.

---

### Post by waspbr on 2008-03-26
I have a similar issue with dark themes, specially with firefox and OOo  since their colour seems  to be changed together with the colour scheme

---

### Post by Tom--d on 2008-03-26
ah... I see..
But I dont know what to do? At all with editing it.

---

### Post by SunnyRabbiera on 2008-03-26
well its now up to you really, if you want some variety go to [gnomelook]("http://www.gnome-look.org/") that way you can get more themes to play around with and even edit.
Your main themes on your system are located in usr/share/themes, and the extra themes you can install on gnome look will install in home/yournamehere/.themes a hidden directory.
by default you cannot edit the themes in usr/share/themes as they require root privelages, but you really dont need to go under root to use or edit them, you can just copy the themes you like over to your home/yournamehere/.themes directory and then edit them.
to unhide these directories when you open up your home folder go to "view" and then select "show hidden files"
then open up your .themes folder in a seperate window, from there you can go into the theme you want and look around for the gconf file and edit it.

---

### Post by Tom--d on 2008-03-26
Thanks, but What do I need to change in the gconf file?

---

### Post by SunnyRabbiera on 2008-03-26
nothing, you just open it with a text editor thats all.
basically the gconf file is a gussied up text file, with a lot of technobabble for the code geeks.
But its relatively easy to figure out.

---

