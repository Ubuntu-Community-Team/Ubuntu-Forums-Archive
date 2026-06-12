---
title: "Are transparent backgrounds only for Terminal programs?"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by imnotryan on 2007-08-13
I want to have all of my windows from all or nearly all of my programs to show my desktop-background through - with the text, or icons within a folder (the pertinent info in the window) still being opaque and 100% visible.

I see the effect mostly on terminal programs and various widget-like app's.... but I don't often see it on all windows. When browsing my files, or reading an instant message - id like to do it over my desktop's colors.  (no not just the colors, the desktop itself.)

Do only certain applications have the ability?
Is this simply not going to happen?
I have feisty/beryl.

This is the effect I'm referring to - Sorry to the man who's desktop I am stealing to demonstrate my point.
[http://i103.photobucket.com/albums/m128/envyouraudience/obkanji.jpg](http://i103.photobucket.com/albums/m128/envyouraudience/obkanji.jpg)

---

### Post by Xenthan on 2007-08-13
Sorry for the slight thread-hijack here, but I was simply curious as to how the man from the link got his desktop to look like that (with the running processes, CPU usage, kernel info, etc.) being displayed?  Is it through vast programming knowledge, or is it a simple program download?

---

### Post by ThrobbingBrain66 on 2007-08-13
> **imnotryan said:**
> I want to have all of my windows from all or nearly all of my programs to show my desktop-background through - with the text, or icons within a folder (the pertinent info in the window) still being opaque and 100% visible.

I see the effect mostly on terminal programs and various widget-like app's.... but I don't often see it on all windows. When browsing my files, or reading an instant message - id like to do it over my desktop's colors.  (no not just the colors, the desktop itself.)

Do only certain applications have the ability?
Is this simply not going to happen?
I have feisty/beryl.

This is the effect I'm referring to - Sorry to the man who's desktop I am stealing to demonstrate my point.
[http://i103.photobucket.com/albums/m128/envyouraudience/obkanji.jpg](http://i103.photobucket.com/albums/m128/envyouraudience/obkanji.jpg)

I think it's a per-application thing.  gnome-terminal has it and so does x-chat but I don't believe it's possible with nautilus, for example.

---

### Post by ThrobbingBrain66 on 2007-08-13
> **Xenthan said:**
> Sorry for the slight thread-hijack here, but I was simply curious as to how the man from the link got his desktop to look like that (with the running processes, CPU usage, kernel info, etc.) being displayed?  Is it through vast programming knowledge, or is it a simple program download?

Probably Conky

```
sudo apt-get install conky
```
then add it to your startup programs

Check this thread for 'themes'
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by Seisen on 2007-08-13
That is conky in the left-hand corner.

---

### Post by Steveway on 2007-08-13
The apps need to be rewritten for that.
For GTK there is a new library in development called libsexier wich will offer widgets wich use compositing.

---

### Post by bodhi.zazen on 2007-08-13
If you want true transparency your options are beryl, compiz, or xcompmgr

You can check this out :

[http://kmandla.wordpress.com/2007/02/14/transparencies-in-openbox-with-xcompmgr/](http://kmandla.wordpress.com/2007/02/14/transparencies-in-openbox-with-xcompmgr/)

The screen shot looks like openbox (as a window manager) with conky in the upper left corner.

I can not tell if the terminal is true transparency or not (pseudo transparency shows your desktop background image, ie windows underneath will not be shown).

To configure conky this link is also helpful :

[http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)

---

### Post by Seisen on 2007-08-13
Its one of the box variety, flux, open or black I wasn't sure either. :lolflag:

---

### Post by bodhi.zazen on 2007-08-13
he he he... it's openbox for sure (look at the information on conky, easy to miss)

---

### Post by imnotryan on 2007-08-13
OK.....

I'd be happy with psuedo-transparency.... that is showing my desktop image (or in my case gradient colors) thru the window contents - however not showing windows that may be underneath it.

Infact - that would be preferable to me because its just the color matching I'm after, not seeing a dizzying array of windows beneath one.

Any tips on achieving that?

EDIT: for clarity:  I don't mean making an entire window transparent the way beryl so easily can do.  I want for instance an IM window's text and border/frame to be opaque over the desktop's background,

Thank you.

---

### Post by diatribe on 2007-08-13
I believe what you are looking for is not possible, like having just the menubar and title bar be transparent, but having the rest of the controls opaque?  or like in nautilus having the background be transparent put having the icons and text opaque?  if so this isnt possible

---

### Post by imnotryan on 2007-08-13
> **diatribe said:**
> I believe what you are looking for is not possible, like having just the menubar and title bar be transparent, but having the rest of the controls opaque?  or like in nautilus having the background be transparent put having the icons and text opaque?  if so this isnt possible

This is what I was afraid of.  Thank you.

At the very least can anyone tell me if I can change the window's background color?  I see it all over other themes.... However I can't find the option in Beryl or Ubuntu to do it.  Right now it's off-white which stands out horribly.

Under preferences there is "windows" but it says I can't open it because "Beryl has not registered a configuration tool."

---

### Post by Krydahl on 2007-08-15
Shame - I'd love this too. 

Re getting the background colour set, what I found was Beryl themes only seemed to set up the borders round windows and the controls. If you want to set the insides of the windows (including background colour) I did it by changing my metacity theme. Now at first I assumed that metacity wasn't running when beryl was (and maybe it isn't) but if you start the default theme manager (not emerald, the thing near the bottom of your preferences menu) and tinker with the themes there, you can change background, text colour and things like that for most windows.

Haven't managed to make anything transparent using it though.

---

