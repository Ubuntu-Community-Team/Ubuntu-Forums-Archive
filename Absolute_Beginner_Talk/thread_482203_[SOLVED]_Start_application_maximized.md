---
title: "[SOLVED] Start application maximized"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by purdticker on 2007-06-23
How do I make an application start maximized?  I want the terminal to be maximized when I open it.

---

### Post by Pragmatist on 2007-06-23
Here is an explanation from this thread: [http://ubuntuforums.org/archive/index.php/t-107000.html](http://ubuntuforums.org/archive/index.php/t-107000.html)

> 
GOTO: APPLICATIONS -> SYSTEM TOOLS -> APPLICATIONS MENU EDITOR
 Inside the editor goto: Accessories
find Terminal in the list, right click on it and click on preferences.

If you have put the terminal link the Gnome Panel you can just right click on the icon in the panel and go to preferences.

This brings up the entry Editor for gnome-terminal, in which you will find the Command box, that probably says something like this:

 gnome-terminal --working-directory=%f

you want to add a switch for geometry here ( --geometry WIDTHxHEIGHT+XOFF+YOFF)

Where:
  WIDTHxHEIGHT = the size of the window, you'll just have to play with it to get it right
  +XOFF = offset from the left edge of the screen
  -XOFF = offset from the right edge of the screen
  +YOFF = offset from the top edge of the screen
  -YOFF = offset from the bottom edge of the screen

resulting in something like this:
gnome-terminal --working-directory=%f --geometry=150x40+0+0

it appears, now that I actually try this, that gnome or ubuntu's implementation of gnome uses Chars instead of pixels for the geometry settings, so start small and work up, lik 60x60 and adjust from there

I'me running 1400x1050 resolution and to get full screen with the gnome panels visible I set mine to 172x55+0+0, this gave me full width and just a sliver of desktop at the bottom

see man gnome-terminal and man X (scroll down to the geometry section) for more info


---

### Post by thelinuxguy on 2007-06-23
> **purdticker said:**
> How do I make an application start maximized?  I want the terminal to be maximized when I open it.

If you want  a "Fullscreen" terminal (The one that you get on selecting View >> Fullscreen in gnome-terminal as opposed to one that is maximized) then this (complicated) solution works:

1) Install wmctrl
```

sudo apt-get install wmctrl

```

2) Create a launcher and use this as the command
```

bash -c "gnome-terminal && wmctrl -r :ACTIVE: -b toggle,fullscreen"

```


[COLOR="Blue"]@Pragmatist:[/COLOR]
Is there anything like --geometry=maximized? That is, no hardcoded width and height values so that the application still opens maximized when I change the resolution?

---

### Post by Pragmatist on 2007-06-23
> **thelinuxguy said:**
> 
[COLOR=Blue]@Pragmatist:[/COLOR]
Is there anything like --geometry=maximized? That is, no hardcoded width and height values so that the application still opens maximized when I change the resolution?

I don't know.  Why not google it and let us know what you find?

---

### Post by thelinuxguy on 2007-06-23
> **Pragmatist said:**
> I don't know.  Why not google it and let us know what you find?

I had tried that. Didn't find anything. Thought there could be some other way (some other switch or something) to achieve the same.

---

### Post by haganerei on 2008-07-17
In GNOME/Ubuntu:
gnome-terminal --full-screen

---

