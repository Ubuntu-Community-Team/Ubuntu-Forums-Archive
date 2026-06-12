---
title: "firefox, epiphany, iceweasel problems ... opera ok"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by marsplus on 2007-05-27
i was using firefox on dapper without any probems ... but it now no longer starts ... i installed epiphany and iceweasel and they don't start either ... finally, i installed opera and it works fine ... any with an explanation? thanks

---

### Post by stimpack on 2007-05-27
start firefox from a console, then you usually get some output which may shed some light.

Firefox/Epihany are GTK apps (gnome)
Opera is a Qt app. (kde)

Maybe a gnome/gtk problem.

---

### Post by DJ Wings on 2007-05-27
Epiphany and Iceweasel are Firefox-based- they use FFX libraries and settings.

---

### Post by alienexplorers on 2007-05-27
Try setting up a new profile in Firefox.

> [http://kb.mozillazine.org/Profile_Folder](http://kb.mozillazine.org/Profile_Folder)

[http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

---

### Post by marsplus on 2007-05-29
thanks for your  replies and comments ... i received the following errors when i tried to run firefox and iceweasel, respectively ... any idea what they mean? thanks

/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libdocshell.so: undefined symbol: PR_GetPhysicalMemorySize

/usr/lib/iceweasel/run-mozilla.sh: line 131:  5800 Segmentation fault      "$prog" ${1+"$@"}

---

### Post by marsplus on 2007-05-29
update: just installed mozilla browser and it is ok

summary: firefox. epiphany and iceweasel are installed but won't start ... mozilla and opera are okay ... still confused ... any further comments? thanks

---

### Post by dolphin_oracle on 2007-05-29
well, until you said Mozilla worked, I was beginning to suspect some sort of library issue since the three you mentioned all use the gecko rendering engine and opera does not.  But I thought mozilla did to, so that throws me for a loop! Have you tried removing them and reinstalling?

---

### Post by marsplus on 2007-05-29
dolphin_oracle ... yes, removed firefox and epiphany and reinstalled them ... but that didn't fix the problem

btw, i was trying to trying to install an alien application (suse) when this happened ...

---

### Post by marsplus on 2007-06-01
problem fixed ... i removed the alien application and now firefox and epiphany are okay

---

### Post by zvacet on 2007-06-01
>  i installed opera and it works fine ... any with an explanation? thanks

It is simply the best.You can run others because of curiosity,but if you want fast and elegant browser Opera is the choice.

---

