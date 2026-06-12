---
title: "GNOME Panel, NOT always on top?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by Sklasko on 2007-01-18
Hello there, I was just wondering if it was possible to set a specific panel to NOT always be on top of other windows? I want to have a small non-expanded panel at the top right with nothing but the system monitor in it, but I don't want it to hog space that my Firefox window could be using while maximized. 

This, in my view, is a very basic configuration option and I can't seem to understand why it's missing. :-k  However, forgive me if I'm overlooking something here.

Thanks in advance for any help.

---

### Post by Sklasko on 2007-01-18
I was Google'ing and read somewhere that this can be dependent on the window managers own settings. Perhaps this is the solution? I've been looking around but nothing so far. Maybe what a lot of people say *is* true: "GNOME is too simple"

---

### Post by RomeReactor on 2007-01-18
Well, one way to do it is to right-click on the panel, select "Properties" and check "Autohide". Hope this helps you.

---

### Post by supersonicdarky on 2007-06-22
i know that i'm bumping a partially old thread, but i would like to know if there is away to not have a specific panel on top. also, autohide doesnt completely hide it, and i dont want it to pop up when i move my mouse to the side.

---

### Post by technx on 2007-08-25
I was having an issue with auto-hiding my side panel, fortunately there is a way to hide the side panel by running gconf-editor, which can be accessed by pressing the run short-cut of ALT + F2 and typing gconf-editor.

Once the editor is open, navigate to apps -> panel -> toplevels ->(panel # (could be panel 0, 1, 2, etc..), look at the orientation value to find the panel you want to hide)  and edit the auto_hide_size value to whatever you like. Setting this to 0 completely hides the icons, except for about a pixel or two from the borders of the panel itself which is only a few pixels wide, you probably won't even notice it.  

The down side to the operation above means that since the icons are completely hidden, you won't be able to mouse over them to bring out, at least that is how it is from what I tried. 

I came up with a compromise. My panel that I want to auto hide is on the left side and I set the auto_hide_size value to 8 - that way the panel sticks out a little bit when its hidden so when I mouse over it, it brings out the whole panel.

Hope this helps

---

### Post by mike555 on 2007-08-25
=== of course you could put everything that is on the top bar onto the bottom bar , then delete the top bar ......... I do that for my Windows converts .========

---

