---
title: "software updates......"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-07-02
ok, so ive turned on the pc, as i do every morning, and after ten minutes or so the software updates icon appears, so i click on it to see what it wants to install, and to my surprise it wanted to install a shed load of compiz stuff, so i thought what the hell and let it install.
now i have no idea what to do with it all, im using beryl, i did try and install compiz fusion and well the less said about it the better, i made a mess of the install and only just managed to get my system back with out having to re-format.
so how do i use it ? and do i have to remove beryl  ? i did try compiz --replace, but i had no way to change any settings and such like, also isnt there meant to be an icon ? like the red beryl icon ? 
cheers.

---

### Post by dfreer on 2007-07-02
What's your /etc/apt/sources.list look like?
basically, you probably got some compiz repository in there that is breaking your beryl install. I would uninstall, clear the sources.list, reinstall beryl and see if that fixes it.

---

