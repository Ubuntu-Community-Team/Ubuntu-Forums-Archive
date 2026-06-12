---
title: "Flux killed Dapper"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Drillbit on 2007-02-16
Hello all.

I installed Flux Box last night, couldn't find it, and switched my computer off. Now, today, when I logged on all I get in a white screen with a toolbar down the end. 

That's it though.

No desktop, no icons, no wallpaper, no nothing. Flux killed Dapper. Even if I right click, I just get "Flux Box" in a non clickable icon. 

Please help.

Thank you.

---

### Post by bodhi.zazen on 2007-02-16
That sounds like fluxbox, but it sounds as if the configuration is not complete.

First how did you install Fluxbox ?

Second what happens when you Ctrl-Alt-Backspace ?

This hopefully will get you to a terminal.

Type in ```
sudo gdm
```

to re-start GDM.

Also if you are booting directly to fluxbox, did you disable gdm or do yo have some type of auto log-in ??

After all that, we can help configure fluxbox.

---

### Post by Drillbit on 2007-02-16
Just to clarify; how can I delete Flux Box without having access to any terminals?

---

### Post by kerry_s on 2007-02-16
logout(ctrl+alt+backspace) select fail safe terminal and type> 
sudo update-menus

then type> exit

and the log back in to fluxbox.

---

### Post by Xappe on 2007-02-16
if you log in with GDM (gnome desktop manager, the thing where you put your login and password), try to choose sessions and then gnome...

That *should* get you back into gnome.

if that fails, another thing you could try is to press ctrl+alt+f1 while in fluxbox, and then install the package "menu" with apt-get:

That should give you a fluxbox right click menu I guess...

---

### Post by Drillbit on 2007-02-16
> **bodhi.zazen said:**
> That sounds like fluxbox, but it sounds as if the configuration is not complete.

First how did you install Fluxbox ?

Second what happens when you Ctrl-Alt-Backspace ?

This hopefully will get you to a terminal.

Type in ```
sudo gdm
```

to re-start GDM.

Also if you are booting directly to fluxbox, did you disable gdm or do yo have some type of auto log-in ??

After all that, we can help configure fluxbox.


Thanks for the reply.

I first installed it by clicking your link.:lolflag: 

I will try your suggestions and log back on. (I'm on live CD at the moment.)

---

### Post by Drillbit on 2007-02-16
OK, I'm on now in fail safe. (Thanks Xappe.)

---

