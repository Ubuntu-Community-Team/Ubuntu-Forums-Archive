---
title: "[SOLVED] 8.04 beta updated to final release? (re-post sorry!)"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by -random on 2008-04-06
hi iv'e read a couple of other threads and haven't found a clear awnser...

If i install the beta version now, and just do the updates , will it be exactly the same as the final release version on the 24th(5,6,7..th) ?

I cant w8!! :guitar:but i don't want 2 install, then re-install on the 24th again.

thnakx

---

### Post by Tatty on 2008-04-06
Yes if you keep updating then when the final release comes out, your system will be updated to that version.

---

### Post by JoshuaRL on 2008-04-06
Yep, should be the same if you keep updating.

---

### Post by -random on 2008-04-06
cool bananas! \\:D/:-\"=D>=D>\\:D/\\:D/

---

### Post by JeSTeR7 on 2008-04-06
I realize this has already been answered, but someone explained it to me in a way that made me really understand.  All of the releases are just snapshots of the repositories.

---

### Post by -random on 2008-04-07
Aaaou! i think i get it..

but there must be something different that makes it different, otherwise all versions would be lts's kinda? Dont quite think i know what u mean?

(btw is there a keyboard shortcut for console?)

---

### Post by forestpixie on 2008-04-07
Not default - open keyboard shortcuts in system> preference menu - look in Desktop - it's close to bottom - Run a terminal' and add your shortcut.

---

### Post by Tatty on 2008-04-07
> **-random said:**
> Aaaou! i think i get it..

but there must be something different that makes it different, otherwise all versions would be lts's kinda? Dont quite think i know what u mean?

(btw is there a keyboard shortcut for console?)

each version of ubuntu has its own set of repositories (the repos you are using are set in /etc/apt/sources.list).  When something gets changed in the repository you are using, your package manager will see there is a new version of that package availabe and ask if you want to update it.

As hardy is currently in development, the hardy repos will be changing a lot and the changes may be quite big alterations to the code.  This of course might result in things breaking, and then those breakages will have to be spotted and fixed (via bug reporting) - which is why an alpha or beta cannot be relied upon to work all the time.

When it is stabe enough (hopefully by apiril 24th), the code will be "frozen".  From then on, the only changes to it will be security updates or if they find a bug big enough  that it simply has to be fixed in the repos.

---

### Post by -random on 2008-04-08
Aaaaahh.. now i see. That makes a lot of sense! Thanks a mil.

also thnkz for keyabrd shortcuts.. it was right there in front of me, yet i didn't c it lol :P

---

