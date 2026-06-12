---
title: "Beryl Human Theme"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by chen_tso on 2008-03-25
Hey, 

I love Compiz, not for the 3D fancy stuff, but i Iike the extra desktop space and the convenience of switching the workspace. I also like the default human theme. But I noticed with Compiz, even using GTK theme rather than Beryl I get this semi-transparent windows title bar when the window is inactive. How do I turn that transparent thing off? I've tried looking for the setting in Compiz configuration but could not find anything to turn that off. 

Please help.

Thanks, 
Peter.

---

### Post by angry_johnnie on 2008-03-25
Open Emerald settings manager,   Click on the tab that says 'edit themes.'   Then scroll down to where it says 'select engine.'   You've probably selected 'truglass' which is the transparent one.  Just choose a different engine and see which one you like.  You can download lots of other themes for emerald from [www.gnome-look.org](www.gnome-look.org)

---

### Post by chen_tso on 2008-03-25
Hi,

thanks for the reply. But I'm not sure that's what I'm looking for. I disabled Emerald theme and just stuck with the GTK Human theme (because I like it). 

Peter.

---

### Post by angry_johnnie on 2008-03-25
Hmm... that's rather strange... It doesn't make sense that it's transparent without emerald.   But, then, maybe that's just something I'm missing...

Anyway, I came across this:

[http://gnome-look.org/content/show.php/Ubuntu+Human+Emerald+Theme?content=69935](http://gnome-look.org/content/show.php/Ubuntu+Human+Emerald+Theme?content=69935)

That is, if you're interested in re-enabling emerald.  You'd still have the default human theme. :-)

---

### Post by sarixe on 2008-03-26
yeah, compiz does that with its 'gtk-window-decorator'.

---

### Post by chen_tso on 2008-03-26
I figured it had something to do with compiz. I have tried mucking around with the settings but I couldn't figure what would turn that off.

---

### Post by chen_tso on 2008-03-26
Hang on,  may have just found something on the compiz wiki. Thanks.

Edit: So yeah. It looked like using Gconf-editor and changing the value for

/apps/gwd/metacity_theme_opacity

did the trick. Thanks again.

---

