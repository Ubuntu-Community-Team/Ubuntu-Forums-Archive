---
title: "Resizing icons through terminal"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by yamel on 2007-02-23
Good afternoon.

I think I've searched well for this on the forum and haven't found anyone else with the problem.

I need newbie instructions on opening a terminal from the login screen and the commands needed to change the icon size on the top desktop panel.  

I don't know how much you need to know, but I'm working on a Gateway MX3414 laptop (with plenty of other issues: sound, graphics, etc.).  I was playing with increasing the size of the icons from the properties menu of the top panel and when it got as large as ~50 pixels the screen went a little wild and bumped me back out to the login screen.  Each attempt to log back in results in being bumped back out again after the second or third icon begins to load, so that I don't have time to right click for the panel properties and decrease the size.

I've tried to log in in recovery mode from the GRUB menu and to enter different types of sessions from the login screen, but each crash as the icons begin to load.  I expect this is indicative of a larger problem, but if I could just get back into the desktop, I could begin to focus on those issues.

Thanks so much for any help you can provide.

---

### Post by solar george on 2007-02-24
What commands did you use to alter the icon size?

---

### Post by yamel on 2007-02-24
I didn't use any commands.  I right-clicked on the panel, selected Properties, then used the arrows in the resulting menu to increase the size of the icon.  At ~50 pixels the screen shut down.  I haven't been able to access the desktop since.

Thanks much for any help you can offer.

---

### Post by kevinlyfellow on 2007-02-24
when you get to the login screen, hit ctrl-alt-f1 Login through here.  then 
```

mv .gnome2 .gnome2_bak

``` 

then press ctrl-alt-f7 and log in.  this will reset your gnome settings

Edit:  Sorry, I didn't try my solution before I posted.
this works
ctrl-alt-f7, log in
```
rm -r .gconf/apps/panel
startx
```

---

### Post by yamel on 2007-02-24
Thanks so much for your prompt reply.  Unfortunately, upon logging in, it still tries to load these massive icons in the panel; freezes up after the second icon and bumps me out to login again.

Any alternatives?

Thanks again!

---

### Post by yamel on 2007-02-24
A last desperate attempt to login, right click the panel, select properties, and maneuver the mouse to the pixel size before the icons were loading finally met with some success.  After a week of trying!

So, I have puny icons again and no crashing.  Should I look very deeply into how a change in font size could so destabilize this access to my OS, or should I just be happy with smaller graphics?

Thanks again for your help.

---

### Post by randiroo76073 on 2007-02-24
I don't know if this will help, but common icon sizes are: 16, 24. 32. 48.  After 48 it usually jumps to 96. One thing you forgot to mention is your screen resolution, that has to be factored in also.  I wouldn't try to take it beyond 48 unless running high resolutions, ie: above 1280x1024.

---

### Post by yamel on 2007-02-24
My resolution is 1280 x 800.  Jumped through a lot of hoops just to get the resolution to read right; messing with xorg.conf under the advice of friends and the forum.  I still don't have the NVidia driver properly configured and I'm wondering if that contributed to the problem.

---

### Post by randiroo76073 on 2007-02-25
I'd forgotten about that, I went to my monitor mfg's site & got specs, then, also, video card specs/drivers and jumped thru some hoops too, so that could be part of it.  Good luck & hope it comes thru for you :)

PS: it helps to have your monitors vert & horiz freq specs.  Refresh rate will auto-set off those.

---

### Post by yamel on 2007-02-27
Everything is functioning pretty well, now, thanks.  I even got the Nvidia driver properly configured using envy.  Now to figure out the sound.  Thanks again to all who replied.

---

