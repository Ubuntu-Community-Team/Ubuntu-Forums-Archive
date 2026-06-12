---
title: "Can I change the colour of the Menu font?"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-07-15
I'm in the process of tailoring my desktop scheme.  I only have one panel (placed at the bottom of the desktop) and I have changed its background
 to be blue.  However, the default black text of the menus is difficult to read.  I would like to change this to white, ie. white text on a blue background.  Can I do this?

---

### Post by adam.tropics on 2006-07-15
To change panel font colour, in ~/.gtkrc-2.0 insert this line

include "/home/<user_name>/.gnome2/panel-fontrc"

then create the file panel-fontrc in .gnome2, which consists of the following lines:

style "my_color"
{
fg[NORMAL] = "#4353b6"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"

and that's it. All you have to do is choose the color (and replace the colour code above) and do a killall gnome-panel. The second "widget" line affects only the applets and the first one does the rest.

---

### Post by n00b@linux on 2006-07-15
Thanks adam.tropic but I'm quite new to linux and I'm not sure what you mean by the line:
> in ~/.gtkrc-2.0 
When I 'ls -a' I can see a '.gtkrc-1.2-gnome2' file.  Should I be substituting this file for '.gtkrc-2.0' or will it basically shag my desktop?

Also, I've never 'kill'ed anything before, so when you say:
> do a killall gnome-panel 
Can you give me a bit more explanation please?

I think I know enough linux to implement the rest of your thread.

Thanks for your help.

---

### Post by adam.tropics on 2006-07-15
My fault...better explanations, sorry! Ok, ~/.gtkrc-2.0 is a hidden file in your home directory. If it's not there, create it. (sudo gedit ~/.gtkrc-2.0)

panel-fontrc is not a hidden file, but is in a hidden directory .gnome2 (thats what the . means). Again if not there create it. Also, above where you see <user_name> replace all of that including <> with your username.

killall is not as bad as all that, in this case it just restarts the panel with your new settings.

---

### Post by n00b@linux on 2006-07-15
> **adam.tropics said:**
> My fault...better explanations, sorry! Ok, ~/.gtkrc-2.0 is a hidden file in your home directory. If it's not there, create it. (sudo gedit ~/.gtkrc-2.0)

panel-fontrc is not a hidden file, but is in a hidden directory .gnome2 (thats what the . means). Again if not there create it. Also, above where you see <user_name> replace all of that including <> with your username.

killall is not as bad as all that, in this case it just restarts the panel with your new settings.

Thanks adam.tropic!  I did as you said and it's worked.  Man this linux thing really is the cat's ***!  :mrgreen:

Just check out my screenshot.  Soon I'll have everyone over at my other forums thinking I'm running XP, LOL!

Is there any way I can change the font style, size, etc?

---

### Post by StoneMan353 on 2006-07-15
LOL noob@linux,

That's just disturbing.

Soon your windows buddies will be asking how to have 4 virtual desktops.

---

### Post by adam.tropics on 2006-07-15
> **n00b@linux said:**
> Thanks adam.tropic!  I did as you said and it's worked.  Man this linux thing really is the cat's ***!  :mrgreen:

Just check out my screenshot.  Soon I'll have everyone over at my other forums thinking I'm running XP, LOL!

Is there any way I can change the font style, size, etc?


Saw the screenie, and no! That's it, no more!!

Oh ok, System>>Preferences>>fonts

---

### Post by autocrosser on 2006-07-15
Also--take a look at [http://www.gnome-look.org/](http://www.gnome-look.org/)  --you can find icons-themes & wallpaper there to finish your XPfication;)

Try the Vista-inspirate or Aero icons--also, there is a running thread to OSXify Gnome---

Also--if you use Easy Ubuntu, you can get the MS_core fonts.

---

