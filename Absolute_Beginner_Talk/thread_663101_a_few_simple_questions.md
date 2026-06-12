---
title: "a few simple questions"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Sugz on 2008-01-09
I have had Ubuntu for a while now but or some reason i cant get my head around the following. 
Im very familiar with themes. 
But recently i this downloading this theme.
The install went fine, with no problems. But, the result look of this theme is this... 

[[IMG]http://img526.imageshack.us/img526/4921/screenshot1qg7.th.png[/IMG]](http://img526.imageshack.us/my.php?image=screenshot1qg7.png)


Not Quite what i was looking for. 
But then it struck me, I need GTK 2.x I check my current version. And apparently it is not installed? So what exactly is GTK? and why is it so vital to theming from a Non-developers point of view?
And second apparently i need Pixbuf, Pixmap and all sorts of Plugins for GTK. But i have no clue what they are.
I understand them as a fundermental part of the Beryl Engine but ..... Well, what am i using to theme my Desktop components?

I know this is basic but im just a bit confused, purely because this theme is not working correctly.

---

### Post by -grubby on 2008-01-09
well I'm pretty sure if you're using gutsy  (and almost sure fiesty, I'm pretty sure that GTK 1.2 is old) that you have GTK2. You'll have to wait for someone else to post about the plugins. And GTK is the thing that manages the window decorations for GTK apps

---

### Post by RomeReactor on 2008-01-09
Hi. GTK (The GIMP Toolkit) is used to create graphical user interfaces. To install pixpuf and pixmap, open a terminal (Applications->Accessories->Terminal) and write or paste:
```
sudo apt-get install gtk2-engines gtk2-engines-pixbuf gtk-engines-pixmap gtk-engines-qtpixmap gtk2-engines-qtpixmap
```

---

### Post by stump138 on 2008-01-09
GTK is the gimp toolkit, and a large portion of gnome is built on it.  It is actually installed b y default.  What I would do is start in synaptic, searching for "gtk2-engines" and install those packages.  That should go a way toward getting you started

---

### Post by Sugz on 2008-01-10
Thanks!
So GTK is like a development kit for GUI's?
By the way, that you for that Engine Download Syntax :popcorn:

I installed the engines, and the theme still looks horrible. :(
Other themes that look equally as horrible are the following.

Redmond
Mist
Raleigh
Thinice

They look just like the the screenshot posted above, boxy and unpolished. I hardly think that all they are is a different colour scheme?

---

### Post by thelatinist on 2008-01-10
> **Sugz said:**
> They look just like the the screenshot posted above, boxy and unpolished. I hardly think that all they are is a different colour scheme?

Assuming you got the themes from Gnome-Look or someplace similar, there should be a preview...

---

### Post by sailor2001 on 2008-01-10
themes are what you make them

---

### Post by Sugz on 2008-01-10
no, no im not making them. im merely applying them (or trying to ;) )
Ok, here is the example screenshot of the Aurora Engine Theme. and the next screenshot shows my result. 

What it should resemble
[IMG]http://www.gnome-look.org/CONTENT/content-pre1/56438-1.png[/IMG]

My result
[IMG]http://img526.imageshack.us/img526/4921/screenshot1qg7.png[/IMG]

---

### Post by mcduck on 2008-01-10
> **Sugz said:**
> Thanks!
So GTK is like a development kit for GUI's?


Yes, and also the program that actually draws the user interfaces for programs that use it.

Anyway, have you actually installed the Aurora engine? The theme is not going to work without the engine.. (it's not in Ubuntu repositories, but I believe there was a package for it in Gnome-look.org)

[http://gnome-look.org/content/show.php/gtk2-engines-aurora+%5BRPMs%2BDebs%5D?content=64607]("http://gnome-look.org/content/show.php/gtk2-engines-aurora+%5BRPMs%2BDebs%5D?content=64607")

---

### Post by 3rdalbum on 2008-01-10
If you've installed a package for the Aurora theme engine, it might be older than what the themes require.

Try compiling Aurora from source code; believe me it's not a difficult compile. Run ./configure --help to start with in the Aurora source code directory to see what options you can enable - there's an option for animated widgets that is very cool; you'll want to enable it.

---

