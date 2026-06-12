---
title: "Just got beryl working but..."
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by faylix on 2007-04-10
Well, the resolution looks a little crappier than the normal gnome window manager... it says its running at 1680x1050 but everything looks bigger under system ->  pref ->screen size? 

Also, the desktop flipping is cool, the fact that the icons come up when  I roll over the things on the bottom is cool - but um, what are the other hot keys that i should play with, how do i make it scale back and show that cool 4 desktop look?  In the settings manager it says ctrl +alt + next - what is next? 

ohh third mouse button + dragging does some cool ish (sorry i'm playing with it as i do) 

okay next, the folder icons and window shading just doesn't look as nice (maybe having to do with the magnification/lower resolution) also, the colors are more grey now... def not as nice as the human theme under regular gnome. 

Can someone give me some tips? I like beryl but it color matching, shading and looks are just as important as cool 3d flipping!:guitar: 

-J

---

### Post by freebird54 on 2007-04-10
Here are some commands/capabilities:

[http://wiki.beryl-project.org/wiki/Tips/Default_Commands](http://wiki.beryl-project.org/wiki/Tips/Default_Commands)

And the themes are in Emerald Theme manager.  A little tweaking goes a long way with Emerald.  There is a clearlook Human I think - if that is what you're looking for.  Never noticed a difference in fonts/Resolution though...

---

### Post by faylix on 2007-04-10
My resolution is def lower, the icons for things like folders are just flat grey now, instead of being colorized like under gnome. 

The gradients on applications seem to be lower quality. Am i missing something?

-J

---

### Post by freebird54 on 2007-04-10
Change the theme!  Yolu *DID* load on the Emerald Theme manager - and the emerald-themes package?  Should be in the right-click from the Red Diamond on your top panel...

---

### Post by faylix on 2007-04-10
Swapped the theme to the Ubuntu one, folders still grey, gradients still messy. Should i post screen shots? 

-J

---

### Post by freebird54 on 2007-04-10
Sounds very strange to me.  Things are still fine when you don't load beryl?  I wonder if one of the render options would change things (use COW - use Copy etc etc).  I almost can't tell when Beryl is there - until I move a window or stick the mouse in the top right corner...

---

### Post by faylix on 2007-04-11
Everything works fine when beryl is not running. What is Cow? is that through the beryl manager? 

I just fixed that crappy shift delete log out 'feature' - but in doing so crashed the beryl server. I'll be rebooting and going back to messing with it soon. 

Everything looks perfect under gnome's window manager, gradients on windows look nice and smooth, icons are colored, text is the right size. Everything in beryl looks pretty awkward. I hope i can get beryl to run at this display and look like this because its got some sexy features. 

-J

---

### Post by faylix on 2007-04-11
Here is a side by side example with the same window's open - its like the gradients are messed up, the color has been bled out and the resolution isnt the same. 

:-(

-J

---

### Post by freebird54 on 2007-04-11
VERU odd! I almost looks as though some other desktop manager has taken over (the desktop manager is Nautilus, Window manager is Metacity or Beryl).  In fact the desktop theme almost looks more like Motif (or lesstif, in today's terms).

What does the startup.sh look like?  Which video setup are you using?  I have NOT seen that before!

---

### Post by faylix on 2007-04-11
this is my /usr/local/bin/start_beryl.sh

> #!/bin/bash
#
# Start beryl-manager within gnome-session
#
if [ `ps -A -o comm | grep -c '^Xgl$'` == "1" ]; then
       DISPLAY=:1 beryl-manager
       DISPLAY=:1 beryl-xgl
else echo "${0}: Error: beryl-manager not launched. Xgl not running?"
fi

This is run from sessions  -> start up programs

I'm on a thinkpad t60 with a ATI mobility radeon with fglrx

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)

(command above run under gnome) 

This is starting to feel silly. 

-J

---

### Post by faylix on 2007-04-11
under beryl, the fglrxinfo changes: 

> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)


could this be the source of my woe?

---

### Post by freebird54 on 2007-04-11
Well - here is note from the install guide that I followed:  It refers to how xgl is started up.

```
Alternative

For me, above script did load XGL properly, and Beryl could be run too. However, my 
theme wasn't loaded, everything looked incredibly ugly. Folders, files, everything had
no theme. After some searching I found the following startxgl.sh script, which loads 
gdm as well, so gives me back my theme:

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

Note: You may also need to install beryl-dbus as it wasn't installed on my system by default.

```

and here is the version I use - with 'protection' from potentially losing the shutdown and reboot options as well...

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
#exec /etc/X11/Xsession gnome-session
```

Maybe this will cure the problem :)

BTW - the full guide was here:  [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL)

in case I didn't post it before (can't remember!)

Good luck!

---

### Post by freebird54 on 2007-04-11
The change I haven't figured out - but I don't think it matters - it runs fine.  Ubuntu doesn't use XFree86 anyway - it uses xorg - so I don't know that the complaint might be.

---

### Post by faylix on 2007-04-11
I switched to your script, but on further reading in that FAQ you posted i tried the gnome-setttings-daemon fix and thats what finally did it. woot! 

Everything looks sexy under beryl. 

Now um... How do i fade/darken the windows under my terminals? so i can actually see what i'm type? Someone mentioned beryl can do this but when i right click on the window all i get is the option to fade the whole thing... 

thanks guys! Sorry for my noobishness!

-J

---

### Post by faylix on 2007-04-11
Whoops. got that too. its just a setting i missed in the beryl manager... 


Okay this is all pretty cool - anyone have some extra tips they'd like to share for last things i should do? 

-J

---

### Post by freebird54 on 2007-04-11
Not sure about fading - but blur effects will 'clean up' the view underneath if need be.

---

### Post by freebird54 on 2007-04-11
Have you enabled the rain to fall?  <shift><F9> ?  Set the Skydome yet?  Changed the scaling of the cube?  Tried it from the inside?  Unravelled it?  Beryl can the most productive addition to your system - OR the biggest time sink in comuting history!!  :D

---

