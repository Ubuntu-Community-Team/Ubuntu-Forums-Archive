---
title: "Help me fix my desktop! PLEASE!"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by joshjani on 2007-04-30
OK- I've been messing around with my Ubuntu install, and I wanted to check out some other desktop looks. I installed uXbuntu desktop via synaptic, and was given a login window to choose between xfce or gnome.

I now just want to use gnome, and want to log in w/ the same look, logos etc as I was before I tried ubuntu's look. So that's problem 1.

I also changed my panels around to try to mimic windows a little more, placing them at the bottom of the screen and deleting one panel. But I lost my trash icon, and now my windows minimize off screen somewhere! I had 5 instances of firefox running, etc.

So, how do I rid myself of the xfce login screen? How do I just restore the defaults of the gnome desktop so I have the panels back where they belong? And how do I get a trash icon on the desktop? Thanks for any help!

JC

---

### Post by Billy McCann on 2007-04-30
To get rid of xfce --

sudo aptitude remove --purge xubuntu-desktop


Then log back into gnome, right-click on your existing panel and choose, create new panel.  Move that new panel wherever you want, right click on it, click add to panel, and add a Window List.  You'll also find a Trash button (and everything else you could ever want) that you can add to the panel in that "Add to Panel" dialog window.  

Hope that helps.

---

### Post by Sef on 2007-04-30
> To get rid of xfce --

```
sudo aptitude remove --purge xubuntu-desktop
```


First do ```
sudo aptitude update
```

then do ```
sudo aptitude remove --purge xubuntu-desktop
```

---

### Post by starcraft.man on 2007-04-30
> **joshjani said:**
> 
How do I just restore the defaults of the gnome desktop so I have the panels back where they belong? And how do I get a trash icon on the desktop? Thanks for any help!

JC

To get your trash back on the bottom panel, right click on it and select "add to panel", in the big window look at "Desktop and Panel" and trash is right there. :)

As for your panels, I'm not sure I understand. Do you mean to say that you deleted the bottom taskbar where your windows minimize to?

If you need to make it back again, right click on your remaining panel and click "New Panel", then add whatever you like to it (I assume if you deleted the bottom one you want the "show desktop" on the far left and "workspaces and trash" on the right.

Hope that helps :)

Edit: yar... was sitting on your post too long and got beat >.>

---

### Post by Billy McCann on 2007-04-30
Hi Sef.  

I think this is an opportunity for me to learn.  :)

Why is it necessary to `sudo synaptic update` before removing xubuntu-desktop?  

I've done it before without and would like to know why I should be doing this.  Thanks.  :KS 


Billy

---

### Post by joshjani on 2007-05-02
> **starcraft.man said:**
> As for your panels, I'm not sure I understand. Do you mean to say that you deleted the bottom taskbar where your windows minimize to?

If you need to make it back again, right click on your remaining panel and click "New Panel", then add whatever you like to it (I assume if you deleted the bottom one you want the "show desktop" on the far left and "workspaces and trash" on the right.

Hope that helps :)

Yes, that's the one I was talking about. My windows now minimize offscreen somewhere.

I'll try all this good stuff out and let y'all know.

JC

---

### Post by joshjani on 2007-05-02
OK- I got my desktop OK for me when I get logged in- I have a single panel at the bottom, with just about everything I want on it. BUT when I first boot up, I still get the Xubuntu login- blue with the mouse logo.

I have nothing against xubuntu, but it just doesn't match the rest of my ubuntu install- in the brown-ish tones I like. How do I get back to the regular old login screen? I have already tried the 2 sudo commands listed above. Thanks for the help!
JC

---

### Post by joshjani on 2007-05-02
Found my answer- system->administration->login window->local

So thanks for nothin'! :-P (just joking)

JC

---

