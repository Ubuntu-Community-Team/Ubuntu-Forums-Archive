---
title: "Window Padding"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by dannymichel on 2007-06-08
I'm a webdesigner so the term I use  for it is cellpadding.
I don't know if you guys know what I'm talking about, but the [cellpadding]("http://www.htmlcodetutorial.com/tables/index_famsupp_29.html") for Ubuntu seems a bit more than the cellpadding on my Windows desktop.
I mean the space between the text and what not on all the Windows.

Please say someone knows what I mean.
I was wondering how to decrease the cellpadding thus giving me a bit more space.

---

### Post by dannymichel on 2007-06-08
Another example:
You click on applications and see the spacing between each application mae? I want to control THAT.

---

### Post by arijarot on 2007-06-09
> **dannymichel said:**
> Another example:
You click on applications and see the spacing between each application mae? I want to control THAT.

I'm not entirely sure that what I'm going to suggest is relevant to your question, but... in theme preferences (sys>prefs>theme), under  customize> controls, I installed and use xfce-winter (for instance), which when I click on applications, there is no (/little) space between the sub-menus... maybe you can customize your theme (i.e., spacing) here, to suit yourself...

see png attachment

---

### Post by dannymichel on 2007-06-10
Still can't find it.

---

### Post by arijarot on 2007-06-10
still can't find what? if you're looking for specific settings to change, I don't know how to do this, but if you want to change the settings via themes, then this is my suggestion to accomplish the same end.

---

### Post by dannymichel on 2007-06-15
I'm just looking to change the spacing in the windows controls.
With the high customization capabilities on Linux desktops this has GOT to be possible>
Does anyone know what I mean?

---

### Post by jordanmthomas on 2007-06-15
Are you talking about the sections I have highlighted in red here?
If so, then you just need to find / make a metacity theme with smaller padding.

...or are you talking about the distance between the buttons in the titlebar...(solved by metacity theme also)
...or are you talking about the widgets (like the OK / Cancel buttons in your windows)....(solved by a new GTK theme)

You may want to check this out as it's an easy to use GUI app that will allow you to override the pre-defined "padding" in GTK themes:
[http://www.gnome-look.org/content/show.php?content=47349](http://www.gnome-look.org/content/show.php?content=47349)

?

---

### Post by dannymichel on 2007-06-15
I highlighted what I am talking about.

---

### Post by dannymichel on 2007-06-15
Are there like theme engines that will allow me to do this?
What's XFCE about anyways?
I heard about theme engines, but I really cant tell the difference between any of them.
What are the other ones other than Murrine?

---

### Post by jordanmthomas on 2007-06-15
Well, on the plus side I know what you're talking about now.
On the down side, I have actually wondered how to fix this myself (at least in nautilus)  
I've looked around but can't really come up with anything.  I guess someone else will have to hop in here and offer some sort of suggestion.

XFCE is kind of like gnome-light (or so they say) and it uses gtk themes just like Gnome.  In my experience it's becoming about as heavy on resources as Gnome is.  

Engines that aren't Murrina:  Pixmap, Clearlooks, Candido, Rezlooks, etc.
Changing engines won't let you fix the buttons in nautilus.  A theme for Firefox *might* work though.

---

### Post by mcduck on 2007-06-15
That padding is defined in themes, to change it you need to edit the themes gtkrc file. Or try to find another theme with less padding..

---

### Post by dannymichel on 2007-06-15
> **jordanmthomas said:**
> Well, on the plus side I know what you're talking about now.
On the down side, I have actually wondered how to fix this myself (at least in nautilus)  
I've looked around but can't really come up with anything.  I guess someone else will have to hop in here and offer some sort of suggestion.

XFCE is kind of like gnome-light (or so they say) and it uses gtk themes just like Gnome.  In my experience it's becoming about as heavy on resources as Gnome is.  

Engines that aren't Murrina:  Pixmap, Clearlooks, Candido, Rezlooks, etc.
Changing engines won't let you fix the buttons in nautilus.  A theme for Firefox *might* work though.
I don't JUST want to change it on Firefox though.
I want to chage it for every window on my desktop.
What's this?
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-71-1.png[/IMG]
> **mcduck said:**
> That padding is defined in themes, to change it you need to edit the themes gtkrc file. Or try to find another theme with less padding..
How do I edit my themes gtkrc file?

> **jordanmthomas said:**
> 
XFCE is kind of like gnome-light (or so they say) 
My desktop is a LOT slower when I use XFCE  session.
Is that the only difference for XFCE? Because if the supposed speed is suppose to be the only difference I have no reason to use it.

[[IMG]http://www.geekdum.com/forums/gallery/data/501/medium/XFCE_Panel.png[/IMG]]("http://www.geekdum.com/forums/gallery/data/501/XFCE_Panel.png")
You see the size of that icon?
Why is it so tiny when I shrink my panel size?
I mean, I set my panel size to 24 on my REGULAR Ubuntu desktop and it's the equivalent of when I set my panel size(height) to 16 on XFCE(why is that?)
Why is the icon so small when I set it to 16?
This is a bug?

---

### Post by mcduck on 2007-06-15
> **dannymichel said:**
> 
What's this?

That's Widget Factory. It's a samll app that displays some buttons and other widgets in one window, making it easier to write GTK themes as you don't have to actually reload the GTK theme you are using all the time to see how changes you make change the theme. (So, it's just a window with buch of buttons that don't actually do anything).
> **dannymichel said:**
> 
How do I edit my themes gtkrc file?

Browse into the theme's directory and open the gtkrc file in any text editor ;) You'll find your theme from either ~/.themes or /usr/share/themes. Try searching forums for more help about making gtk themes, it's been a long time since I've made any and I don't have access to any Linux machine ATM so I can't really help in that.

---

