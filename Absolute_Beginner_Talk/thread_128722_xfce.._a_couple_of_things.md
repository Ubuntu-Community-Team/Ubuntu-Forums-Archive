---
title: "xfce.. a couple of things"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by wishyjr on 2006-02-12
hiya guys! havent started a thread in a while now but here goes...

just installed xfce last night and played about with it. love it. i've got it running over kde and it works sweet apart from a few minor things:

mouse right clicking. it worked fine when i first installed it but after a bit of playing with the desktop settings (and stuff in general) it now doesn't bring up the menu it should. any ideas?

desktop icons. i like them. does xfce allow me in any way to create links/shortcuts to stuff by putting icons on the desktop? not quite sure where to put my trash just yet :)

oh and whats this 'lil star'? is that what the little mini menu thing is?

thanks chaps!

---

### Post by alfonz on 2006-02-12
xfce doesn't support desktop icons unfortunately, not sure how you lost the right click menu, I don't run KDE but did you launch konquer by any chance?

If you did that might have taken over your desktop and in that case open terminal

```
sudo killall konquer
sudo xffm or xmmf (not sure which it is)
```

the little x button is a menu applet that does launch your xfce applications menu.

Hope this helps.

---

### Post by Jimmey on 2006-02-12
HIJACK!

Just kidding, I'm genuinely apologetic but;

How did you install xcfe? Can it be "got" through apt-get? Or, if I install it through a .bin, and don't like it, can it be easily removed?

---

### Post by alfonz on 2006-02-12
best way to install it is through apt-get

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

5-1-min later you have xfce to choose from in session in log-in

remember to log off ;)

---

### Post by wishyjr on 2006-02-12
cheers guys,

alfonz, i'm quickly learning to live without icons so thats cool :)

i didnt open konqeurer so i dont think thats it. i ran the commands you suggested but it didnt kill anything. thanks anyway dude. i know i can run stuff with the xfce menu button, i just like using my right click menu better :)

to jimmey: mate, all i did was use adept (if your using gnome - synaptic) and did a search. i think you may have a repository problem if you can find it there. mark it for install and away you go!

oh, and i have another question: can i intergrate the main menu bar and the task bar together? thanks.

---

### Post by alfonz on 2006-02-12
[QUOTE=wishyjr]cheers guys,

alfonz, i'm quickly learning to live without icons so thats cool :)

i didnt open konqeurer so i dont think thats it. i ran the commands you suggested but it didnt kill anything. thanks anyway dude. i know i can run stuff with the xfce menu button, i just like using my right click menu better :)

to jimmey: mate, all i did was use adept (if your using gnome - synaptic) and did a search. i think you may have a repository problem if you can find it there. mark it for install and away you go!

oh, and i have another question: can i intergrate the main menu bar and the task bar together? thanks.[/QUOTE]


My fault, as I said I don't use KDE but if nothing got killed then either the command is wrong or konqer isn't running at all.

as for the taskbar, yes you can. Right click on the xfce panel and add new item, look through the list and you will see taskbar or something like that. ;)

If you want system tray you can add it as well but you first have to dissable it from the taskbar in settings. xfce wont let you run two instances of the same thing.

oh and now that you have 2 taskbars open terminal and type

sudo killall xftaskbar4 - this should get rid of the top taskbar.

---

### Post by Jimmey on 2006-02-12
Just got XFCE. I love it to peices.

---

### Post by wishyjr on 2006-02-12
yeah, been playing with mine, ive set it up like kde but its better!! goddammit i love linux! yippee!! :)

---

### Post by alfonz on 2006-02-12
well you guys if you like the desktop icons you can run nautilus (konquer for KDE). However be WARNED if you do like the right click menu of xFce this will disable that feature.

---

### Post by Peter76 on 2006-02-12
To get desktop icons, you can use rox-filer, which is the filemanager in xfce if i'm right; don't know exactly how in xfce ( using it with icwm ) but here's the general steps:
make a script that starts up when xfce starts up ( look up in xfce manual where to put it); you probably have to make it executable as well ( chmod 744 nameofscript )
put this int the script:
rox --pinboard=whatevername youlike (or maybe rox-filer; can't remember command now)
The pinboard option takes over your root window and now you can drag icons to it from the filemanager. Now if you right click you get the rox menu. If you want the xfce menu, in the rox menu go to option and somewhere you can change th right click behaviour to get the xfce menu.
If this is all a bit to vague, tell me and i'll lokk it up properly later.... ( now in bed with laptop being lazy;-)

Good luck

---

