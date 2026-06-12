---
title: "Splash manager will no longer load"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2007-10-29
I have installed a couple of splash screens recently, but now the 'Splash Manager'  no longer loads. A very quick view of it then it disappears. Anyone know of a solution to this problem? I'm using Gutsy and have used the Splash Manager recently.
regards

---

### Post by 1337455 10534 on 2007-10-29
Do you have multiples installed and none selected? or compiz fusion?

---

### Post by Sbarton on 2007-10-30
Thanks for your reply, and sorry for the delay in answering.
I have a few installed and 1 selected which loads as it should do. The problem is I cannot get splash manager to load, when selected in 'system/preferences/splash, (should I want to change the splash screen) it very briefly makes an appearance and then disappears from view , a fraction of second.
regards

---

### Post by Sbarton on 2007-10-30
Forgot to mention, I have not enabled Compiz, my graphics card isn't good enough at present.
regards

---

### Post by Sbarton on 2007-10-31
Bump! Is there anything else I could try?
regards

---

### Post by realvz on 2007-10-31
the splash image is in /usr/share/pixmaps/splash
and the config key is: /apps/gnome-session/options/splash_image (in gconf-editor)
the default key for "splash_image" is "splash/ubuntu-splash.png"

Gutsy doesnt have Splash by default...

also try launching splash manager from terminal and note any errors that it may show

---

### Post by Sbarton on 2007-10-31
Thanks for your reply realvz. This seems to be unsolveable at the moment. I have tried uninstalling -reinstalling, but this has not helped. I cannot see any real error except a problem with one jpeg. I have included a attachment of gnome-spalsh-screen manager just incase you or some other person sees a problem with it.
However, thanks for your input.
regards

---

