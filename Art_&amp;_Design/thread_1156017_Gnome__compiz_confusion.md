---
title: "Gnome / compiz confusion"
date: 2009-05-11
forum: Art &amp; Design
---

### Post by skygazer on 2009-05-11
Hi.. i recently switched to ubuntu 8.04 hardy on my laptop.. need your help on few problems that i am facing

1.. whenever i change a theme in Appearances and Preferences, the icon theme also gets changed automatically. So every time i change theme, i have to install the icon theme again. Initially this was not a problem, but now its irritating me like anything. Pls suggest some trick for this

2. is there any way to know which window manager (gtk / emerald) and display manager (compiz / gnome) i am using currently

3. what is the difference between emerald themes and gnome themes. Also there are many customisations possible like icons, window borders, opacity, controls, colours, pointers etc. How are they related to each theme. I thought a theme will have all the above components which will be modified when a theme is applied. But it doesnt seem to be the case. 

4.. if i am using compiz and i change the theme under Appearances and Preferences, then will my display change accordgin to the theme. Similarly if i am using gnome and change the emerald theme, will it effect my display.

i am very much confused about all the customisations. pls help me understand this better.

---

### Post by Flimm on 2009-05-11
Hi!
1. You probably want to click customise and choose the icon set you want manually. You can also choose the control styles, window borders (metacity) and so on. If you don't click customise, GNOME has a list of predefined sets of themes you can choose from.
2. Open System Monitor (System, Administration, System Monitor). Click on the Processes tabs. If compiz.real is in the list, then you're probably running compiz. If not, you're running metacity as your window manager. (Remember that window manager and window decorator are not the same thing, although Metacity can do both).
I've written a guide about all the different themes you can install on Ubuntu, it'll probably help you: 
[Gnome-look.org guide](http://gnome-look.org/content/show.php/Gnome-look.org+guide?content=88873). (gnome-look.org is a site with a lot of GNOME themes)

---

### Post by skygazer on 2009-05-12
> **Flimm said:**
> Hi!
1. You probably want to click customise and choose the icon set you want manually. You can also choose the control styles, window borders (metacity) and so on. If you don't click customise, GNOME has a list of predefined sets of themes you can choose from.
2. Open System Monitor (System, Administration, System Monitor). Click on the Processes tabs. If compiz.real is in the list, then you're probably running compiz. If not, you're running metacity as your window manager. (Remember that window manager and window decorator are not the same thing, although Metacity can do both).
I've written a guide about all the different themes you can install on Ubuntu, it'll probably help you: 
[Gnome-look.org guide]("http://gnome-look.org/content/show.php/Gnome-look.org+guide?content=88873"). (gnome-look.org is a site with a lot of GNOME themes)
thanks for the answer.. but i want to control the icons, window borders , theme etc in a single click instead of changing eeverything manually.. its a big hassle if you are like trying out tens of themes to pick out one.. i hope you understand my question..
 
Also can anyone answer question 3,4?.. I request the linux gurus to help me out..!!

---

### Post by alex.rayu on 2009-05-12
> **skygazer said:**
> thanks for the answer.. but i want to control the icons, window borders , theme etc in a single click instead of changing eeverything manually.. its a big hassle if you are like trying out tens of themes to pick out one.. i hope you understand my question..
 
Also can anyone answer question 3,4?.. I request the linux gurus to help me out..!!

Hi if you want to control the theme with a single click then you should save your theme - in the theme manager, it has a "save as" option. THen it saves your theme up (all the parts of the themes it consists of need to stay in respective folders after you save a new theme. 

But whenever you apply one of the pre-set themes, you will have all parts of it (icons, themes, cursors) applies as well. Some of them even have own wallpaper. 

If you want to control the window decorator, install a fusion-icon package. After you run it (i have it in autorun) it displays in icon on the system tray that allows you to choose the decorator and choose between compiz/metacity.

---

### Post by mcduck on 2009-05-12
Also, just to clear a couple of things:

*Gnome* is the desktop environment. You are using it all the time, no matter if you use desktop effects or not. Gnome is the panels, the desktop, configuration tools, all the keyboard shortcuts you have, and interaction between applications (like drag & drop) etc.

*Metacity* and *Compiz* are window managers. They are responsible of putting running programs into windows that you can move around, minimize etc. Metacity is Gnome's default window manager, but when you enable the desktop Effects Ubuntu switches to using Compiz instead. In addition to normal window manager features Compiz adds compositing and a bunch of effect plugins.

Unlike other window managers, Compiz doesn't draw the window borders directly, instead it uses plugin programs called "window decorators" to do the job. By default the window decorator used in Ubuntu is *gtk-window-decoarator*, which allows using Metacity's themes with Compiz. *Emerald* is another popular window decorator for Compiz.

*GTK2* is the toolkit used to draw your programs on the screen. it's responsible of all the buttons, scrollbars etc. stuff your running apps use in their user interfaces.

(In other words, GTK and Emerald are not window managers, and compiz & gnome are not display managers. GTK is widget toolkit, Emerald is a window decorator, Compiz is a window manager and Gnome is a desktop environment.. ;) )

---

### Post by skygazer on 2009-05-12
> **alex.rayu said:**
> Hi if you want to control the theme with a single click then you should save your theme - in the theme manager, it has a "save as" option. THen it saves your theme up (all the parts of the themes it consists of need to stay in respective folders after you save a new theme. 

But whenever you apply one of the pre-set themes, you will have all parts of it (icons, themes, cursors) applies as well. Some of them even have own wallpaper. 

Thanks alex.. will definately try this out today..! I cant believe i overlooked this save as option in the theme manager..

> 
*GTK2* is the toolkit used to draw your programs on the screen. it's responsible of all the buttons, scrollbars etc. stuff your running apps use in their user interfaces.

Ohh.. do you mean GTK+2.x  themes can be used with both metacity and compiz and that they can set looks of the window controls only..

---

### Post by mcduck on 2009-05-12
> **skygazer said:**
> Thanks alex.. will definately try this out today..! I cant believe i overlooked this save as option in the theme manager..


Ohh.. do you mean GTK+2.x  themes can be used with both metacity and compiz and that they can set looks of the window controls only..

Exactly. GTK has absolutely nothing to do with window borders. (well, some Metacity themes can take colors from current GTK theme and use them, but that's all).

GTK themes change how apps that use GTK as toolkit for their widgets look like. No matter what window manager, desktop environment or operating system you use. (I even have some GTK apps on both Mac and Windows..)

---

### Post by alex.rayu on 2009-05-12
It's like this:

**Gnome** is a desktop environment. It uses **GTK** as a toolkit (to draw form elements), and **Metacity**, which is a window manager (to draw border around windows, resize, minimize/maximize, etc).

Gnome can work as it is, with Metacity and GTK.

Then, there comes **Compiz**. Compiz is, roughly speaking, a program, that hooks into Gnome and allows it to take the drawing of elements into the OpenGL, which allows to use the resources of video card accelerator. That also allows to *composite* the output (draw all things before actually showing them). Compositing allows to make different cool effects. 

Compiz still uses the GTK to display buttons and other form elements, but it also allows to replace Gnome's window decorator (Metacity) with it's own (Emerald). **Emerald** is a window manager, which can take over Gnome's Metacity and draw and control windows in it's own way. Emerald is installed separately and has it's own themes.

So, basically, it's a system op PLUGINS that plug into Gnome to make it cooler. When plugins plug in, they take over certain functionlaity, like drawing, looks, control, etc. This is something which Windows allows only to a very limited extent, which is why compiz-like projects for Windows are so lagging behind as compared to Linux. Microsoft won't let plug in into Explorer.

So, while it may look a bit complicated - co many plugins and flexibility, one soon gets used to it and becomes hugely irritated, when using Windows and seeing that Microsoft win't let you do this or wont let you do that, like you have to apply a hack to be able to use a theme other than default.

---

### Post by skygazer on 2009-05-12
> **mcduck said:**
> Exactly. GTK has absolutely nothing to do with window borders. (well, some Metacity themes can take colors from current GTK theme and use them, but that's all).

GTK themes change how apps that use GTK as toolkit for their widgets look like. No matter what window manager, desktop environment or operating system you use. (I even have some GTK apps on both Mac and Windows..)

Okay, so then what does "gnome themes" on gnome-look.org mean?.. is it a metacity theme/ emerald theme or a gtk theme?..

---

### Post by skygazer on 2009-05-12
> **alex.rayu said:**
> It's like this:
So, basically, it's a system op PLUGINS that plug into Gnome to make it cooler. When plugins plug in, they take over certain functionlaity, like drawing, looks, control, etc. This is something which Windows allows only to a very limited extent, which is why compiz-like projects for Windows are so lagging behind as compared to Linux. Microsoft won't let plug in into Explorer.

So, while it may look a bit complicated - co many plugins and flexibility, one soon gets used to it and becomes hugely irritated, when using Windows and seeing that Microsoft win't let you do this or wont let you do that, like you have to apply a hack to be able to use a theme other than default.

yes.. when i was using vista, i was a bit surprised to know that you can get so many cool 3d effects with such a minimalistic configuration with ubuntu and compiz. Back then my laptop had a windows score of 2.6. Basically windwos was telling me that my beloved computer was not worth running 3d effects!!
And yes, it is quite confusing for a new ubuntu user to have so many options available for customisation without the proper documentation of what is what. Untill today i was downloading random themes from gnome-looks.org and using the one which worked fine.. Now i can choose my themes better. Thank you guys for that..!

---

### Post by Flimm on 2009-05-12
> **skygazer said:**
> Okay, so then what does "gnome themes" on gnome-look.org mean?.. is it a metacity theme/ emerald theme or a gtk theme?..

The [Guide to Gnome-look.org](http://gnome-look.org/content/show.php/Gnome-look.org+guide?content=88873) answers those questions, with a particular emphasis on the way gnome-look.org categorises things.

> **skygazer said:**
> thanks for the answer.. but i want to control the icons, window borders , theme etc in a single click instead of changing eeverything manually.. its a big hassle if you are like trying out tens of themes to pick out one.. i hope you understand my question..
For single click goodness, you might be interested in [Epidermis](http://epidermis.tuxfamily.org). I didn't mention it at first because an unofficial way of customising your desktop, but it does what you ask for.

---

### Post by skygazer on 2009-05-12
gnome-art hangs my computer. Epidermis looks good.. will try it today.. Does it work with 8.04LTS?..

---

### Post by Flimm on 2009-05-14
It should work on 8.04, except perhaps for the USplash themes/pigments, which I've been finding many bugs with.

---

