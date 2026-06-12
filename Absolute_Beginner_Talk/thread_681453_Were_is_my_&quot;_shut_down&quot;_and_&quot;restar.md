---
title: "Were is my &quot; shut down&quot; and &quot;restart&quot;"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Bluestick on 2008-01-29
i don't know what happened... but i don't have "shut down" or "restart" buttons in my menu.. 
Plz help thx ahead

---

### Post by randy78 on 2008-01-29
Did you recently update? Explain what you were doing before the buttons disappeared and that will give us some insight as to what might have happened.

---

### Post by Bluestick on 2008-01-29
screenshot

---

### Post by Amstell on 2008-01-29
thanks funny.....sorry never had that happened.  it almost looks like something graphically is f'ed up

---

### Post by Bluestick on 2008-01-29
the only thing i can remember is i was messing with my avant bar in the terminal... nothing really major :( 
 i cant think of anything im sorry....

---

### Post by Bluestick on 2008-01-29
oh wait... i know i have installed a bunch of themes and stuff like for emarald and such....

---

### Post by randy78 on 2008-01-29
Try restarting X by hitting CTRL ALT BACKSPACE and re-logging in..., you can also shut down from that menu as well. It may just be a glitch in X...

---

### Post by Amstell on 2008-01-29
> **randy78 said:**
> Try restarting X by hitting CTRL ALT BACKSPACE and re-logging in..., you can also shut down from that menu as well. It may just be a glitch in X...

I second that!

---

### Post by Bluestick on 2008-01-29
Ive tried that guys... and nope that's a no go....
 this is weird its like GONE i cant think of anything

---

### Post by jordanmthomas on 2008-01-29
These will also go away if you use kdm to run gnome instead of gdm or if you don't run an *dm and just use startx.

---

### Post by Bluestick on 2008-01-29
> **jordanmthomas said:**
> These will also go away if you use kdm to run gnome instead of gdm or if you don't run an *dm and just use startx.
 sorry can u put that in N00b terms?
 i am using gnome art work themes.. is there a way i can remove that?

---

### Post by zabien1970 on 2008-01-29
If you open the terminal (just the alt f2 one) and put in  metacity --replace  that should replace emerald, then you would know if its in that or not

---

### Post by randy78 on 2008-01-29
Hmmm... well, try switching to one of the out-of-the box themes, like Human or Clearlooks, to see if that straightens it out...

If nothing else, for now you can open a terminal and type: sudo reboot and sudo poweroff

I'll dig around and see what I can find, but it's starting to sound like the glitch might be within the Emerald theme that you're using.

Let us know and if you fix it, be sure to mark your post as SOLVED ;)

---

### Post by jordanmthomas on 2008-01-29
> **Bluestick said:**
> sorry can u put that in N00b terms?

gdm is the gnome desktop manager.  It's what you log on to by default (where you put your user name and password).  If you've installed kde, you might have inadvertently switched to kdm, which is like gdm but meant for use with kde.  

In order for gnome-panel to get permission to shut the computer down, it has to be able to connect to gdm.  If gdm is not running (in the case of you using kdm or logging in in one of the "real terminals" instead of a GUI login) then you will not be presented the options to shutdown or restart.

On second examination though, I don't think this is your problem because a) you'd know if you switched from gdm and b) you still have a hibernate and suspend option.

One last thing I can think of is this:  is another user logged on to another X session?

---

### Post by randy78 on 2008-01-29
Just found this: "I had the same problem and I don't know about 6.06 but on 6.10 this worked for me:

Go to: System -> Administration -> Login Window

On the Local tab under "Menu Bar" the option "Show Actions menu" has to be enabled. It seems to disable itself sometimes if you change the login themes.

Enabling that brought back the missing Restart and Shut down buttons for me...

Hope this helps!

-W"

[http://ubuntuforums.org/showthread.php?t=387340](http://ubuntuforums.org/showthread.php?t=387340)

---

### Post by Bluestick on 2008-01-29
> **randy78 said:**
> Hmmm... well, try switching to one of the out-of-the box themes, like Human or Clearlooks, to see if that straightens it out...

If nothing else, for now you can open a terminal and type: sudo reboot and sudo poweroff

I'll dig around and see what I can find, but it's starting to sound like the glitch might be within the Emerald theme that you're using.

Let us know and if you fix it, be sure to mark your post as SOLVED ;)
Thank you bro ill try to do what u said.... ive tried changing themes going back and forward to default and such, and others.... But no luck ill be sticking around thank you!
 i will try this now
 sudo reboot and sudo poweroff

---

### Post by randy78 on 2008-01-29
No prob, just be sure to try the other thing I posted a couple of minutes ago too ;)

---

### Post by Bluestick on 2008-01-29
> **randy78 said:**
> Just found this: "I had the same problem and I don't know about 6.06 but on 6.10 this worked for me:

Go to: System -> Administration -> Login Window

On the Local tab under "Menu Bar" the option "Show Actions menu" has to be enabled. It seems to disable itself sometimes if you change the login themes.

Enabling that brought back the missing Restart and Shut down buttons for me...

Hope this helps!

-W"

[http://ubuntuforums.org/showthread.php?t=387340](http://ubuntuforums.org/showthread.php?t=387340)
OK FIXED ^^^^^
wow omg thank you so much that was it... for 3 days i had to just unplung the power it hurts to do that to a computer!
I reallly appreciate all your guys help...ubuntu community is awesome! thx  again! :guitar: :popcorn:

---

### Post by randy78 on 2008-01-29
Cool, glad to help :D

---

### Post by Fruhwirth on 2008-01-30
> **randy78 said:**
> 

Go to: System -> Administration -> Login Window

On the Local tab under "Menu Bar" the option "Show Actions menu" has to be enabled. It seems to disable itself sometimes if you change the login themes.


Thanks Randy78 !  My options disappeared after I created and installed a new gdm login screen.  All is well now. =D>

---

