---
title: "Nautilus ignores can_change_accels"
date: 2012-03-30
forum: Any Other OS
---

### Post by veggen on 2012-03-30
I'm trying to change some Nautilus accelerators, but ticking can_change_accels in gconf-editor doesn't seem to do anything for me.
I do see 
(gconf-editor:3346): GLib-GObject-WARNING **: g_object_get_valist: property `type' of object class `GConfEditorWindow' is not readable
in the terminal as soon as I open it, but this does not look relevant to me...

Does it work for you?

I'd be grateful for some help...

---

### Post by veggen on 2012-04-01
*bump*

Can someone please just verify this on their machine, so I know if it's a bug or some problem with my installation?

---

### Post by gordintoronto on 2012-04-02
I doubt if one person in a thousand understands what you mean by "I'm trying to change some Nautilus accelerators," Are you really running 10.10?

---

### Post by veggen on 2012-04-02
Well, I'm really on Mint 12 (hence the other_os prefix), but since it's Ubuntu 11.10 underneath, I've now changed my profile to reflect it. In the end, I guess the only relevant thing is that it's Nautilus in Gnome 3 that I'm talking about (is it Nautilus 3?).
Back to the accelerators... I honestly can't see how could someone who doesn't know what Nautilus accelerators are help me fix them, but ok. I'm talking about keyboard shortcuts in Nautilus (like ctrl+shift+N for creating a new directory). I know that ticking the /desktop/gnome/interface/can_change_accels flag in gconf-editor allows one to dynamically change them, but for some reason my Nautilus is ignoring it.
I can't bother anyone to install gconf-editor just for this, so I just asked the way I did in hopes that someone with knowledge and tools can just see if it works for them...

[This thread]("http://forums.fedoraforum.org/showthread.php?t=273182") suggests trying the same with dconf-editor, so I'll give that a go.

Thanks.

---

### Post by Perfect Storm on 2012-04-02
Moved to Other OS/Distro Talk.

---

### Post by stinkeye on 2012-04-02
> **veggen said:**
> Well, I'm really on Mint 12 (hence the other_os prefix), but since it's Ubuntu 11.10 underneath, I've now changed my profile to reflect it. In the end, I guess the only relevant thing is that it's Nautilus in Gnome 3 that I'm talking about (is it Nautilus 3?).
Back to the accelerators... I honestly can't see how could someone who doesn't know what Nautilus accelerators are help me fix them, but ok. I'm talking about keyboard shortcuts in Nautilus (like ctrl+shift+N for creating a new directory). I know that ticking the /desktop/gnome/interface/can_change_accels flag in gconf-editor allows one to dynamically change them, but for some reason my Nautilus is ignoring it.
I can't bother anyone to install gconf-editor just for this, so I just asked the way I did in hopes that someone with knowledge and tools can just see if it works for them...

[This thread]("http://forums.fedoraforum.org/showthread.php?t=273182") suggests trying the same with dconf-editor, so I'll give that a go.

Thanks.

For dconf, in the terminal use
```
gsettings set org.gnome.desktop.interface can-change-accels true
```

It works here on 12.04 unity.

After setting **can-change-accels true**, to work in nautilus I need to kill nautilus 
```
nautilus -q
```

and because I'm using the unity global menu, start nautilus showing the menubar (doesn't work with the global menu)
```
UBUNTU_MENUPROXY=0 nautilus
```

---

### Post by veggen on 2012-04-02
Ha! Great! This one worked! Thanks a bunch stinkeye!

---

### Post by stinkeye on 2012-04-02
> **veggen said:**
> Ha! Great! This one worked! Thanks a bunch stinkeye!

Good.
You may want too turn it off so you don't accidentally change shortcuts.
```
gsettings **reset** org.gnome.desktop.interface can-change-accels
```

---

### Post by hyfanious on 2012-04-30
Hi
Is there any similar method for changing shortkeys in thunderbird too?
os : 12.04
thanks in advance

---

### Post by wizardeye on 2012-07-26
Another way to change keyboard accelerators in Nautilus is to use [this extension]("https://github.com/vitaut/captain-nemo"). It works even with global menus.

---

