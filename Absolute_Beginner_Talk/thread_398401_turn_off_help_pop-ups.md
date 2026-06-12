---
title: "turn off help pop-ups?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Merick on 2007-04-01
I just installed ubuntu for the first time, can anyone tell me how to turn off the context help pop-ups that show up every time the mouse moves over an item on the desktop or in a menu?

---

### Post by nonewmsgs on 2007-04-01
i know they're called tooltips, but im not sure how to shut them off.

---

### Post by irish_flu on 2007-04-01
I'm not sure this will turn of ABSOLUTELY every kind of pop-up, but it's a good start.

Open up a terminal (Applications ---> Accessories --> Terminal).

At the prompt, type:

```
sudo gconf-editor
```

and enter your password.

This will fire up the Gnome configuration editor (Gnome is the default "desktop" that is installed with Ubuntu, so I'll assume that's what you're using).

In the Editor window that pops up, drill down to Apps ---> Panel ---> Global.

Find the setting (they're arranged alphabetically) called "Tooltips Enabled" and uncheck the box next to it.

Boom, you're done.

You might have to restart Gnome in order to make this work, I'm really not sure.

Here's a fun tip:
If you want to restart your GUI without rebooting the whole machine (just to save you some time), hit CTRL+ALT+Backspace.

Cheers, and I hope this helps you out.

---

### Post by dhughes on 2007-04-01
Thanks for the info I was looking for that option in gconf-editor but there is so much there I didn't know where to look or what you called them, I was thinking popup and couldn't think what else they would be called.

 That one thing I don't like about Ubuntu, the tool tips seem to be everywhere and are very annoying much worse than Windows!

 Firefox still has them but maybe I have to restart X to clear them from that.

---

### Post by irish_flu on 2007-04-01
> **dhughes said:**
> 
 Firefox still has them but maybe I have to restart X to clear them from that.

I don't think that what I suggested will turn them off in Firefox, only in the Gnome Panel.

If you want to turn them off for Firefox:

In the Firefox address bar, type:
```
about:config
```

In the "filter" box that appears, filter for
```
browser.chrome.toolbar_tips
```

You should then see the setting.  In the last column, the "Value" is set to "true". Double-click it to change (toggle) it to "false".

I think this will do what you want (for Firefox, anyway).  IIRC You will have to restart Firefox for it to take effect.

---

### Post by Merick on 2007-04-01
> **irish_flu said:**
> I'm not sure this will turn of ABSOLUTELY every kind of pop-up, but it's a good start.

Open up a terminal (Applications ---> Accessories --> Terminal).

At the prompt, type:

```
sudo gconf-editor
```

and enter your password.

This will fire up the Gnome configuration editor (Gnome is the default "desktop" that is installed with Ubuntu, so I'll assume that's what you're using).

In the Editor window that pops up, drill down to Apps ---> Panel ---> Global.

Find the setting (they're arranged alphabetically) called "Tooltips Enabled" and uncheck the box next to it.

Boom, you're done.

You might have to restart Gnome in order to make this work, I'm really not sure.

Here's a fun tip:
If you want to restart your GUI without rebooting the whole machine (just to save you some time), hit CTRL+ALT+Backspace.

Cheers, and I hope this helps you out.

Ok, I just tried that, then rebooted. I still get the tooltips when the mouse hovers over items in the panel menu. Also, using CTRL+ALT+Backspace does absolutely nothing:confused:

---

