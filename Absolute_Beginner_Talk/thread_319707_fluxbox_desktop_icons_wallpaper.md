---
title: "fluxbox desktop icons wallpaper"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-12-16
i have just instaled fluxbox on my ubuntu and i want to put wallpaper and icons on the desktop how can i do that ?

---

### Post by bodhi.zazen on 2006-12-16
You have several options.

IMO rox is easiest.

See here: [How to ROX](http://community.fluxbuntu.org/index.php?topic=78.0)

There are other fluxbox how-to's on that site that cover how to set your background image.

---

### Post by fasoulas on 2006-12-16
> **bodhi.zazen said:**
> You have several options.

IMO rox is easiest.

See here: [How to ROX](http://community.fluxbuntu.org/index.php?topic=78.0)

There are other fluxbox how-to's on that site that cover how to set your background image.

How can i get **rox**???

i have the ubuntu and after i installed fluxbox i don't  have fluxbuntu

---

### Post by bodhi.zazen on 2006-12-16
```
sudo aptitude install rox-filer
```

---

### Post by fasoulas on 2006-12-16
> **bodhi.zazen said:**
> ```
sudo aptitude install rox-filer
```

that isn't gonna affect my gnome or nautilus right??

---

### Post by bodhi.zazen on 2006-12-16
No it will not affect gnome or nautilus.

---

### Post by fasoulas on 2006-12-16
i installed it now what?

---

### Post by bodhi.zazen on 2006-12-16
See my previous link for a detailed how-to

---

### Post by fasoulas on 2006-12-16
> **bodhi.zazen said:**
> See my previous link for a detailed how-to

ok thnx a lot for the info i will try it

---

### Post by bodhi.zazen on 2006-12-16
FYI I call it "FluxRox"

---

### Post by fasoulas on 2006-12-16
> **bodhi.zazen said:**
> FYI I call it "FluxRox"

Now again make this script executable:
Code:
chmod u+x ~/.fluxbox/startup

You will now start fluxbox with:
Code:
~./fluxbox/startup
Or with the alias (if you set one)
Code:
flux

**i can't understand what it says here**


3. Now (re)start Fluxbox. Kill gdm and start from the cli
Code:
sudo /etc/init.d/gdm stop
log out and back in to tty1 (to activate your alias)
Code:
~.fluxbox/startup
OR 
Code:
flux
If you have set an alias in .bashrc.

and what does it means set an alias in .bashrc???

i tryied it as it is in that how to amd it didn't loaded

---

### Post by kerry_s on 2006-12-16
> **fasoulas said:**
> Now again make this script executable:
Code:
chmod u+x ~/.fluxbox/startup

You will now start fluxbox with:
Code:
~./fluxbox/startup
Or with the alias (if you set one)
Code:
flux

**i can't understand what it says here**


3. Now (re)start Fluxbox. Kill gdm and start from the cli
Code:
sudo /etc/init.d/gdm stop
log out and back in to tty1 (to activate your alias)
Code:
~.fluxbox/startup
OR 
Code:
flux
If you have set an alias in .bashrc.

and what does it means set an alias in .bashrc???

i tryied it as it is in that how to amd it didn't loaded

 I'm assuming you installed fluxbox from the repo, then just add rox to the startup script it should be there already.
in terminal->
gedit ~/.fluxbox/startup

look for this section->
# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

and ad your line

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &
rox --pinboard=Default &

That's it done, log out and back in. When you use fluxbox you have to turn on compatibility with rox, so right click options> compatibility, check the top 4 boxs. then you should have fluxbox right click back.

---

