---
title: "advance desktop effects"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by dankdank on 2008-03-21
I am using advance desktop effects and I don't know if this is intended but I don't have my close, minimize and maximize buttons on any of my windows and ever time I want to move a window I have to press alt and then drag the window. is there a way around this or is it intended? please help :confused: I'm using ubuntu 7.10

---

### Post by billgoldberg on 2008-03-21
Open up the advanced desktop effects settings:

Make sure the the "resize window" is on (it's under the uncategorized section, aka the last section)

About the close keys, I don't really know. Maybe it's the emerald theme you are using?

(it's not intended to be like this).

Did this help?

---

### Post by dankdank on 2008-03-21
yes resize window is check but I still cant drag a window without holding alt and there are still no close minimize and maximize buttons :(

---

### Post by bumanie on 2008-03-21
Do you have an nvidia card. Open terminal, is it a blank white square?

---

### Post by dankdank on 2008-03-21
no i have ATI but everthing works fine besides dragging the window and the min max and close buttons

Edit: terminal is has the promt with my computer name

---

### Post by bumanie on 2008-03-21
Read this blog, it may help
[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by eragon100 on 2008-03-21
system -> preferences -> Advanced desktop effects settings Now go to "effects" (third section from the top) and put a mark in front of "window decoration". click on close in the lower left corner of the window. That should fix your problem :)

---

### Post by dankdank on 2008-03-21
window decorations is already checked : \

---

### Post by forrestcupp on 2008-03-21
Here's the applicable quote from the blog given above:
> Troubleshooting

No window boarders (titlebars)

Insert the window decorator of your choice (gtk-window-decorator, kde-window-decorator or emerald) in CompizConfig Settings Manager &#8594; Window Decoration &#8594; Command

Additionally for Nvidia users:
Make sure you have a nvidia-glx driver installed and use the following command to configure your xorg.conf:

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

(you have to restart X to make it work) 
If you have ATI, don't mess with the part about Nvidia.  But in the 'Command' line in those settings, type whichever of the 3 choices listed above is the right one.  If you are trying to use Emerald, enter emerald.  If you are using Gnome, type gtk-window-decorator in there.

---

### Post by dankdank on 2008-03-21
err... how do i tell what im using (i.e emerald gtk kde

---

### Post by billgoldberg on 2008-03-21
You have to install emerald yourself.

It gives you those transparent windows.

The default emerald theme is a red themed windows border (it's been ages since I used the default one).

---

### Post by dankdank on 2008-03-21
Um,,, okay let me start over sorry for wasting your guys/girls time :( but im completely new to ubuntu and i have compiz working but when I turn on the custom effects for compiz in the system->preferences->appearance Lose the ability to drag my windows without holding down the alt button and I have lost my minimize maximize and close buttons when I have compiz advance desktop effects enable and only when its enabled this is a fresh install I have resize movable windows and window decorations enabled I just have no idea why this is happening please all help is appreciated!

---

### Post by billgoldberg on 2008-03-21
> **dankdank said:**
> Um,,, okay let me start over sorry for wasting your guys/girls time :( but im completely new to ubuntu and i have compiz working but when I turn on the custom effects for compiz in the system->preferences->appearance Lose the ability to drag my windows without holding down the alt button and I have lost my minimize maximize and close buttons when I have compiz advance desktop effects enable and only when its enabled this is a fresh install I have resize movable windows and window decorations enabled I just have no idea why this is happening please all help is appreciated!

Do you have the "move window" plugin enabled in "advanced desktop effect settings".

If that won't fix it, I'm out of ideas.

I never had a problem like this.

---

### Post by dankdank on 2008-03-21
Yes i do have it enabled

---

### Post by billgoldberg on 2008-03-21
It might be a long shot,; but try turning either "snapping windows" or "wobbly windows" on.

And check with each if you can drag windows.

---

### Post by Therion on 2008-03-21
Okay, most likely the problem is Emerald.  Compiz looks to see if Emerald is installed (which it is) every time you boot up since it's the default Windows Decorator for Compiz.  How to solve your problem then?  You need to STOP Emerald from loading at startup along with Compiz.  Compiz yes, Emerald no.  This means you will be using Compiz as your Windows *Manager*, and Metacity as your *Windows Decorator*.  

Fire up your Terminal and get with the copy and paste, Hoss:```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```

---

### Post by dankdank on 2008-03-21
nope i still have to hold down alt when i drag the window :(

---

### Post by dankdank on 2008-03-21
okay i entered that into the terminal... now what? do i restart?

---

### Post by Therion on 2008-03-21
Restarting X should do it:  Ctrl+Alt+Backspace

EDIT:  Almost didn't notice it, but if you have the Windows Decoration plugin ENABLED in the Compiz Config Settings Manager, most likely you'll want to DISABLE it.

---

### Post by dankdank on 2008-03-21
none of that worked :( I so confused :confused:

---

### Post by Triggerhapp on 2008-03-21
```
gtk-window-decorator --replace &
```
Tell us if that works/complains.

---

### Post by dankdank on 2008-03-21
this is what i get 

The program 'gtk-window-decorator' is currently not installed.  You can install it by typing:
sudo apt-get install compiz-gnome
bash: gtk-window-decorator: command not found

---

### Post by Therion on 2008-03-21
> **dankdank said:**
> The program 'gtk-window-decorator' is currently not installed. 
Well that certainly would explain it.

---

### Post by dankdank on 2008-03-21
so what do I do?:confused:

---

### Post by Therion on 2008-03-21
Open a Terminal and paste in the following:```
sudo apt-get install compiz-gnome
```

---

### Post by dankdank on 2008-03-21
okay well I fixed it this is what I did 

sudo apt-get install emerald

then I went to system -> preferences -> sessions and the entered the command

emerald --replace

now it works like a charm! (googled my problem and read a forum post to solve it)

well sorry your guys attempts to help me didnt work :( I really do thank you guys for your time though! im loving ubuntu and very happy switching from windows to linux on my laptop

---

### Post by forrestcupp on 2008-03-22
Good job.  You solved it by installing Emerald, which is a program that gives you customizable title bars and window borders.  You also could have solved your problem by doing what your terminal output says below to install the gtk-window-decorator.

> **dankdank said:**
> this is what i get 

The program 'gtk-window-decorator' is currently not installed.  [b]You can install it by typing:
sudo apt-get install compiz-gnome[/b]
bash: gtk-window-decorator: command not found
When it gets back to your prompt, you just type exactly what it says:
```
sudo apt-get install compiz-gnome
```
The terminal outputs are very helpful, and they're not always cryptic.  If it gives a simple answer, it's worth it to do what it says.

But you may be happier with Emerald anyway.  It's pretty cool.

---

