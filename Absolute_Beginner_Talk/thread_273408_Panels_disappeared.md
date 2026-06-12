---
title: "Panels disappeared"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by GabrielWolff on 2006-10-08
Hey, I just had both of my panels disappearing while shutting down aMule by force. Don't ask me why, but everything else is still there: wallpaper, desktop icons... only the panels are gone.

Why? What shall I do? Is there any "gnome-panel" command for Xubuntu?

G

---

### Post by crispy_420 on 2006-10-08
My girlfriend has the same issue too. So I'll give this a bump.

---

### Post by crispy_420 on 2006-10-08
here is some thing i found:

[http://www.ubuntuforums.org/archive/index.php/t-184984.html](http://www.ubuntuforums.org/archive/index.php/t-184984.html)

---

### Post by GabrielWolff on 2006-10-08
Ahhh! Way too long.
Here's what helped me: 
```
Alt+F2 => xfce4-panel
```

Thanks anyway :-)

Gabriel

---

### Post by crispy_420 on 2006-10-08
sometimes it is the simplest answer. 
i'll let the girlfriend know, thanks.
must be a default keybind in xfce.

---

### Post by GabrielWolff on 2006-10-08
I just figured out that the simplest way is not always the best (as Einstein said: "Make it as simple as possible - but not simpler"): For some reason when I restart the computer, the same problem stays: I have to load the panels manually.

Plus: When pressing the "Quit" button (which you normally would use to reboot or shut down the machine), it asks me: "Exit Xfce Panel?"

Wa!! My Panels!!! :( 

G

---

### Post by harry555 on 2006-10-08
Actually I think it is way too easy to break things in Gnome.   I stupidly deleted the applications menu.   Then coz. my knowledge of linux is at beginner level I finished up re-installing Ubuntu.   I'd had a good search for easy ways of restoring a default menu and couldn't find any.

Imagine what havoc kids could do by this sort of thing.   :confused:

---

### Post by crispy_420 on 2006-10-10
This is what I ended up doing:

Set up new account
added sudo rights to new account

This solved my problem. I know it is an easy way out but it worked for me. Any important data can then just be moved over to that account.

Back to the simple approach but from it I can assume that xfce configuration is screwed up and that is my problem.

---

### Post by srafx on 2006-10-12
Does anyone know the correct way to fix this?  Not only are my panels not showing up unless i manually launch them, but everything seems to be running slow, like sometimes the terminal turns black and sometimes my system monitor freezes, but if i just wait, it will eventually load or disapear?

---

