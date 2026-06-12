---
title: "Problems Shutting down Edgy"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-10
It doesn't look like Edgy likes me shutting it down.

When I click the red power button on the top-right corner and the window pops up with the log off, hibernate, etc options, the 'Shutdown' is conspicuously absent.  For a couple weeks i'd been getting by with logging off and then choosing shutdown from the login screen, but recently even that stopped working.  When I click log off it first just shows the default ubuntu background (with nothing else on the screen) and when I push the power button on my computer the screen turns orange with a white rectangle where the text box is supposed to be on the log in screen, and I have to force a shutdown on my pc.

Any help?

---

### Post by tophatandy on 2007-05-10
odd. 

First did you change the theme?
Did you change the splash or the Usplash?

Try this to start off with:

1.right click the red power button and remove it from panel

2.right click the panel and click add to panel

3. select "Quit..."

then try that out..

---

### Post by gustavocm on 2007-05-10
i have the same problem.

i changed the splash using gconf-editor, because the gnome splash screen manager was not working.
when i type **gnome-splashscreen-manager** in terminal i get:
/usr/bin/gnome-splashscreen-manager:22:in `require': no such file to load -- gnome_splashscreen_manager (LoadError)
        from /usr/bin/gnome-splashscreen-manager:22


but now when i click the "Quit" button in panel, it doesn't ask me what i want to do: shuting down, hibernate, etc. It just turn to a black screen and stays in it until i cut down the power.

removing the Quit button and adding it again didn't work for me.
what i have to do?

---

### Post by mikewhatever on 2007-05-10
Hi, 
I remember having that problem after installing Kubuntu desktop along Ubuntu. It got solved once I removed Kubuntu, but until you figure out your solution, try this from the terminal for shutdown and reboot:
> sudo shutdown -h now
> sudo shutdown -r now

---

### Post by gustavocm on 2007-05-10
yes, that **shutdown -r now** works (well, more or less, i got an strange and annoying blinking screen, that goes black screen to blue striped screen, but in few seconds the computer turns down).

but i want my "Quit"button working again, there's no way to get it back?

oh, i forgot to tell that i'm not with a splash screen anymore. I lost it with the gconf-editor stuff.

thank you

---

### Post by gustavocm on 2007-05-10
oh god....
maybe i changed two things  accidentaly in gconf-editor:
the logout-prompt checkbox  and the show_splash_screen checkbox must marke, of course...

but i don't remember changing this.... anyway, sorry and thank you very much, now everything is working fine....

---

### Post by spur on 2007-05-10
I had this problem and solved it by choosing KDE at login. Instead of loging into ubuntu straight away (auto) I chose session KDE. After that no probs. It seems that I was running nautilus in a KDE session! I did not think that was possable.

---

### Post by zhinker on 2007-05-12
> **tophatandy said:**
> odd. 

First did you change the theme?
Did you change the splash or the Usplash?

Try this to start off with:

1.right click the red power button and remove it from panel

2.right click the panel and click add to panel

3. select "Quit..."

then try that out..

I don't think I changed the splash stuff but I did change the theme, think that's what's causing this (I think the problem did start happening around the time I changed my theme)?  If so is there any way to fix it without reverting back to the original theme?  I don't even remember what it was called

---

