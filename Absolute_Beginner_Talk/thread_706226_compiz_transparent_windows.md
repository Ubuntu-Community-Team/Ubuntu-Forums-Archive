---
title: "compiz transparent windows"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by baysl on 2008-02-24
I know how to make Terminal window transperent, but I dont know how to make all other windows to be transparent?

Can you help?

I have CompizConfig setting manager, what do I change to make all windows transparent?

---

### Post by Mad_Gouki on 2008-02-24
well, you can change the transparency of any window at any time by holding alt+scroll up or down on the mouse to change transparency of the current window up or down, but when you close the window, it will reset to default.
if you want to change the transparency of EVERY window, you can go into compiz config settings manager, click general options (its in the same window pane as all the other options, its just at the very top), click the opacity settings tab, click add, type this into the box:
type=normal
set the opacity between 30 and 99 if you want transparent windows that you can still see, set it above 100 and it will be greater than opaque (it will be SUPEROPAQUE!), set it under 20 or 30 or so, and you won't really be able to see the windows too well, not even the one to change the setting back! :shock:

if you do set it too low, or into the negatives, you can always go to system>prefrences>appearance and turn compiz off so you can delete that setting, or change the value, then turn compiz back on.

as far as a specific window, I'll have to get back to you on that one, expect the answer soon!

---

### Post by Mad_Gouki on 2008-02-24
ok i found it
for the terminal opacity, you do this:
title=yourname@yourname.whatever
the part after the = is what the terminal says when it is open, mine says
_[EMAIL="alex@alex.lapt"]alex@alex.lapt[/EMAIL]_op
then set the opacity to something you like, and it is done
the other options are:
name
type
title
class

there may be a few others i'm forgetting, but this thread should prove useful
[http://forum.compiz-fusion.org/archive/index.php/t-1768.html](http://forum.compiz-fusion.org/archive/index.php/t-1768.html)
basically, you can type xprop into a terminal, click on a window, and it will spit out a bunch of info that you can use in the transparency options.

edit:
also, a better string to use, instead of [email]name@name.comp[/email]
is class=Gnome-terminal

---

### Post by thirdy on 2008-07-16
value of 85-90 will do :D, is there a way to do this but not affecting the text inside the windows?

---

