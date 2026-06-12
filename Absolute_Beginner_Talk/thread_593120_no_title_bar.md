---
title: "no title bar"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by metzy85 on 2007-10-26
Ok so i upgraded from ubuntu fiesty fawn. to the new version and when i went to ran beryl and like it had same settings i had before and like there are no title bars at top of the windows. how can i fix that?

I have dell b130 inspiron notebook. 2gb of ram 1.8ghz, 128mb integrated graphics card.

---

### Post by benerivo on 2007-10-26
In Gutsy, the beryl package has combined with compiz and is now just listed as compiz. If you install and run 'Compiz configuration settings manager'  you can try ticking the 'Window Manager' option to see if that puts the title bars back on.

---

### Post by metzy85 on 2007-10-26
Ok thanks man i don't like compiz s much harder to configure then beryl.

---

### Post by zero244 on 2007-10-26
Hello: Make sure Window Decorstion is check in the beryl settings.
Also there might be a option line you need to add to your xorg.conf file. Do a search here.........there are many posts related to your problem.
Most likely you can fix this by editing your xorg.conf file.
This is the line I added to the screen section of my xorg.conf file.

Option         "AddARGBGLXVisuals" "True"

I had the same problem......this fixed it.

---

