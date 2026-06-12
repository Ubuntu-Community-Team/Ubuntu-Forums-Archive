---
title: "apearance crashes when I open it"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by LowSky on 2008-02-06
I can't change my theme and its driving me crazy, I know like 3 ways to change the background, without using system>preferences>appearance, but to change theme, not even right clicking works

i took the command that appearances uses and ran it from terminal, this is the output

```


john@john-desktop:~$ gnome-appearance-properties %F

(gnome-appearance-properties:7100): Gnome-WARNING **: invalid gnome config path '=/section/key'


(gnome-appearance-properties:7100): GLib-CRITICAL **: g_markup_parse_context_end_parse: assertion `context->state != STATE_ERROR' failed
Segmentation fault (core dumped)

```

I even tried turning off Glib in Compiz, but that doesn't seem to fix it either...?

anyone know how I can fix the gnome config path =/section/key  ?

---

### Post by LowSky on 2008-02-07
Update: Turning off compiz doesn't fix it,restarting/reinstalling gnome does not either.

I found something about how a KDE install might screw it up, but I dont have any KDE libraries or programs installed, so that can't be it.

Is there a way to change the theme in gnome-config?

---

### Post by erginemr on 2008-02-07
Strange, I have never witnessed such a behavior. Are you currently using Hardy Heron? If so, it is normal to expect such bugs in an OS at alpha / beta stage.

---

### Post by LowSky on 2008-02-07
I know its normal for Alphas to be dodgy but, I been using prereleases of ubuntu before and expect some odd things to happen. I am only posting here because Launchpad doesn't have anyone experiencing the same issue as of yet.

Even in stable releases I have had ubuntu crahs prgrmas like this as well, so I assume that there has to be a file corruption, I would just like to know if anyone knows the file stucture to gnome and if someone has a fix, other than loggin in safemode, purging gnome, then reinstalling

---

