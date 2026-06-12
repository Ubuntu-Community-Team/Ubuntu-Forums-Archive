---
title: "Where do I get the clearlooks-cairo engine?"
date: 2007-05-26
forum: Art &amp; Design
---

### Post by Forlong on 2007-05-26
I installled the GTK-theme Gilouche from here: [http://art.gnome.org/themes/gtk2/1284](http://art.gnome.org/themes/gtk2/1284)
Then I got some error-messages in the terminal and I found out that the theme depends on clearlooks-cairo engine while Ubuntu only has regular clearlooks.

Can somebody tell me what's the easiest way to get clearlooks-cairo for Ubuntu Feisty?
Every How-To I found is outdated...

---

### Post by mech7 on 2007-05-26
doesn't this mean that you need to use compiz or xgl ?

---

### Post by kpolice on 2007-05-27
It is just the standard clearlooks, you don't need anything else.

---

### Post by Forlong on 2007-05-28
> **kpolice said:**
> It is just the standard clearlooks, you don't need anything else.
Well, here's the error-message:
```
/usr/share/themes/Gilouche/gtk-2.0/gtkrc:42: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Gilouche/gtk-2.0/gtkrc:43: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/Gilouche/gtk-2.0/gtkrc:44: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
```
and this is the mentioned section in the Gilouche-gtkrc:
```
	  engine "clearlooks"  {
    menubarstyle      = 0       # 0 = flat, 1 = sunken, 2 = flat gradient
    menuitemstyle     = 0       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
    listviewitemstyle = 0       # 0 = flat, 1 = 3d-ish (gradient)
    progressbarstyle  = 0       # 0 = candy bar, 1 = supercandy, 2 = flat
  }
```
When I change **engine "clearlooks"** to **engine "ubuntulooks"** the error-message is gone.
So it's either a problem with the Theme or the engine.
Then I read somewhere that there's a clearlooks-cairo engine and Ubuntu still has the standard clearlooks...

Did you check on Arch if it works for you?

---

### Post by kpolice on 2007-05-28
The error is because in the latest clearlooks engine the 3 options are depreciated and are not used anymore.

---

