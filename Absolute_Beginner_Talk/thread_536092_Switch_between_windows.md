---
title: "Switch between windows"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by dr.koljan on 2007-08-27
Yesterday I found a cool feature in Ubuntu. :)

I was going to turn off my computer, but accidentally missed the red button and clicked in the top-right-most corner of the screen. It produced an unexpected effect which you can see on the screenshot attached (or try doing it yourself).

I am wondering if there is a key shortcut to do this and if not how can I make it?

Thanks in advance :)

[IMG]http://img512.imageshack.us/img512/1575/switchun2.png[/IMG]

---

### Post by Lexyboy on 2007-08-27
Nice isn't it?  It's a standard feature of Compiz (the fancy window manager now included in Ubuntu) - actually you don't need to click in the corner, just move the mouse to the top right corner.  You can probably set a key alternative, but not sure how - unfortunately there isn't a nice settings manager for Compiz like there is for Beryl (you can do it through configuration editor but it's not that obvious - maybe someone who knows what they're doing will post a reply!).

Also, try going to the bottom right corner - also quite handy when you have a cluttered desktop!

---

### Post by dr.koljan on 2007-08-27
> **Lexyboy said:**
> Also, try going to the bottom right corner - also quite handy when you have a cluttered desktop!

Hmmm... It opens Trash :)

---

### Post by Lexyboy on 2007-08-27
Don't click anything - just move to the far corner.  For me, all the windows whizz to the top/bottom of the screen - just out of view - so that you can get to the desktop.  Go back to the bottom right and they come back.  I think it's like that by default, but I could have set it up and forgotten.

---

### Post by dr.koljan on 2007-08-27
> **Lexyboy said:**
> Don't click anything - just move to the far corner.  For me, all the windows whizz to the top/bottom of the screen - just out of view - so that you can get to the desktop.  Go back to the bottom right and they come back.  I think it's like that by default, but I could have set it up and forgotten.

Nope, doesn't work 4 me

---

### Post by Lexyboy on 2007-08-27
Hmm will have a look when I get home - I must have changed some setting to get it.  If you run configuration editor ('gconf-editor' in a terminal), you can play with the features of compiz if you navigate to /apps/compiz/general/allscreens and /apps/compiz/general/plugins

See [here]("http://compiz.org/Gconf-Editor") for a bit more detail, but it's not that clear...

Another trick that might work: hold CTRL+ALT and, still holding these keys down, left click and drag the mouse around.  You should get the now legendary cube effect to switch between workspaces.

---

