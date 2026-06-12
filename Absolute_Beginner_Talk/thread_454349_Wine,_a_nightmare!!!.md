---
title: "Wine, a nightmare!!!"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by naknak987 on 2007-05-25
I got myself into a real pickle this time. I installed wine using the this code...   ```
sudo apt-get wine
``` I couldn't find were it was at to start it up, so I restarted my computer. When the desktop started back up I have absolutely no panels, and I cant get to the terminal to pkill them to see if they would comeback if I did. I think if I reinstall the panels with synaptic it would fix this, but i don't know how to start synaptic up without the panels. Please help, this is turning into a nightmare. It took me about a half-hour to figure out how to start firefox without the panels. :( I know, I'm such a noob.

---

### Post by Outrunner on 2007-05-25
If you press alt+f2 does a "run application" prompt come up? If it does, try typing ```
gnome-panel
``` in it and see what happens.

---

### Post by naknak987 on 2007-05-25
When I do that, it tells me that there is already a panel runing and the it won't start a new one. I think if I could get a terminal up i could pkill to get them back.

edit: I used what you just told be to use to run a terminal, then i pkilled the panels, now i have panels. thanks for the help. I think i can use synaptic to reinstall the panels now to fix the problem. thanks.

---

### Post by Outrunner on 2007-05-25
Anytime. Are you sure you installed wine though? just

```
sudo apt-get wine
``` doesn't seem to do anything except give an error.Of course maybe you typed it right in the terminal but wrongly here, just thought I'd make sure

---

### Post by naknak987 on 2007-05-25
I was wrong, using synaptic to reinstall the panels didn't fix the problem. I also gave you the rong code,  what I used was... ```
sudo apt-get install wine
```

---

### Post by Hobo Joe on 2007-05-25
un-install it using:
```

sudo aptitude purge wine

```
Then install it using this:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by naknak987 on 2007-05-25
Thats what I used to install in the first place, I will try it again tho.

---

### Post by Hobo Joe on 2007-05-25
> **naknak987 said:**
> Thats what I used to install in the first place, I will try it again tho.

Oh, I didn't realize that's what you used....

But you have a very weird problem, as far as I know, wine doesn't run on startup, unless you added a session for it.

When you start up the computer, before you log in, set the session to 'failsafe GNOME' and see what happens. 

If it works, check your sessions to make sure that Wine doesn't have a startup in there.

---

### Post by feest on 2007-05-25
okay maybe this might be usefull, 

hit crtl-alt-f1 to switch to a terminal
use sudo killall gnome-panel
and then gnome panel (maybe using the command earlier posted)

does this help?

---

### Post by naknak987 on 2007-05-25
I don't want wine to run on startup, I want my panels to be visible when the desktop is done loading. See, after I first installed wine, the panels weren't visible, but they were still runing. Inorder to get them to be visible again, I had to pkill them to make them reload, then they would be visible. Thats what I'm trying to fix. Reinstalling wine didn't do anything tho.

Edit: I'm not sure what you are telling me to do feest.

---

### Post by Hobo Joe on 2007-05-25
> **naknak987 said:**
> I don't want wine to run on startup, I want my panels to be visible when the desktop is done loading. See, after I first installed wine, the panels weren't visible, but they were still runing. Inorder to get them to be visible again, I had to pkill them to make them reload, then they would be visible. Thats what I'm trying to fix. Reinstalling wine didn't do anything tho.

Edit: I'm not sure what you are telling me to do feest.

Ok, I'm not sure if this will work, but try booting into recovery mode and re-installing the panels. This is kindof risky, so I'd suggest waiting for a second opinion before trying it. First type:
```

sudo aptitude purge gnome-panel

```
Then install it again by:
```

sudo aptitude install gnome-panel

```

Then restart the X server by:
```

startx

```

Like I said, a second opinion would be a good idea, because I'm still a novice at this stuff.

---

### Post by Enverex on 2007-05-25
Wine doesn't run on startup, nor does it run after installing it unless you specifically run it. Your issues aren't related so Wine, it's just a coincidental timeframe.

I remember I had the panel issue ones. I got around it by killing X then doing "sudo rm -rf /tmp/*".

---

### Post by l3f3vr3 on 2007-05-25
try ctl-alt-(plus) or ctrl-alt-(minus) to get your resolution back where it should be.

Then make sure your computer is starting in the right resolution.

---

### Post by naknak987 on 2007-05-25
My computer is starting in the right resolution. 

I don't know what you mean by "killing x then doing "sudo rm -rf /tmp/*"

I just want my beautiful panels back.

Edit: what exactly does ```
sudo rm -rf /temp/*
``` actually do. Because that fixed the problem.

---

### Post by Enverex on 2007-05-25
It removes temp files on your PC. I remember after killing the X server once to update my graphics drivers that it wouldn't load Gnome again, so I did that (which removes my users temp files for Gnome too) and it fixed it.

---

