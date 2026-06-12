---
title: "get rid of xgl and get gnome back?"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-08-12
i used the script from this thread to try to install xgl. when i rebooted (as instructed) i found xgl added to the gdm menu. however, whenever i would try to login to xgl, i would get a black screen (as if it were going to login) but then, get popped right back to gdm. the worse thing is that this now happens when i try to login to gnome, as well. i have absolutely **no** further interest in attempting to get xgl going. all i want is to get rid of it and return to how things were before i ran that script. how can i do this?

btw, i have pm'ed the author of the script in hopes he may be of help.

---

### Post by Greycloak on 2006-08-12
I'm completely frustrated with Xgl also. I haven't been able to make it work at all. After all of the hassle this is what I did:

```
sudo gedit /etc/gdm/gdm.conf-custom
```

After [ servers ] erase the 0=xgl

Erase the entire [ server-xgl] section (to the end of 'flexible=true'

Then take a look at your startup programs and see if there is an entry for startcompiz or compiz-start.  Erase the entry.

I had to do this a few times after my failed attempt to get Xgl working, and it did the trick for me.

---

### Post by fuscia on 2006-08-12
> **Greycloak said:**
> I'm completely frustrated with Xgl also. I haven't been able to make it work at all. After all of the hassle this is what I did:

```
sudo gedit /etc/gdm/gdm.conf-custom
```

After [ servers ] erase the 0=xgl

Erase the entire [ server-xgl] section (to the end of 'flexible=true'

this is odd. yours is the second mention of this suggestion. the first time i checked gdm.conf-custom, i found nothing after *[ servers ]*

> Then take a look at your startup programs and see if there is an entry for startcompiz or compiz-start.  Erase the entry.

'startup programs'? i have no idea where to look for such (just a humble end user here).:???: 

> I had to do this a few times after my failed attempt to get Xgl working, and it did the trick for me.

you know, i should have known better than to try this. oy! thanks for the response.

---

### Post by xpod on 2006-08-12
Could i just ask......I have been watching the many hassles people have been having not just installing this xgl thingmajiggery BUT then Uninstalling it when they realise it`s not for them.

Do any of you`se know then what the 3d desktop is thats listed in both "synaptic" in ubutno and "adept" in kubutno??

IS that the same thing...Sorry if it`s a stupid question but i had decided to pass on the xgl hassles until i noticed the 3d desktop in the package managers......

OR is that something else all together??Thanks

---

### Post by fuscia on 2006-08-12
no idea, xpod.

---

### Post by xpod on 2006-08-12
I had figured it was`nt ..BUT ..how many 3d desktop packages can be out there?

Im sure if it was just a case of "clicking" install in those package managers
I would`nt be seeing all the complicated looking "install"guides eh.

AND YOU would just be clicking "UNinstall"eh....

I obviously NEED to read what it say`s a bit better :shock: THANKS anyway.

And good luck

---

### Post by fuscia on 2006-08-12
i got gnome back. i couldn't find any of the things in gdm.conf-custom that everyone was suggesting i needed to get rid of, so i just went into synaptic and removed all the xgl/compiz stuff and now, gnome is back.

---

### Post by calvinthomas on 2006-08-12
I used this link to install XGL and it worked perfectly, also it created a separate login for XGL & Gnome so I could log in to whichever I want, only problem is the lack of Shutdown & Restart buttons in XGL which isn't a big issue with the terminal commands or the option to log out and then shutdown, incase anyone is interested the link is below:

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

Calv

---

### Post by GuitarHero on 2006-08-12
I got XGL/Compiz working with that script, but I dont like it at all.  Reduces productivity.

---

### Post by calvinthomas on 2006-08-12
Thats true, expecially if you don't tweak the bouncing windows and stuff, i'm not in a huge rush to do things (i'm not working to tight deadlines) so I quite like the extra eyecandy, can always log back into Gnome or KDE if I really need the extra productivity.

Calv

---

### Post by fuscia on 2006-08-12
i was mostly just in a 'wtf, why not?' kind of mood. (i've never seen the compiz stuff and thought "omg! i *must* have it!") any curiousity was quickly annihilated by the ensuing difficulties.

---

