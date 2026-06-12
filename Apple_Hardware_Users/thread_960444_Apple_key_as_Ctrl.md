---
title: "Apple key as Ctrl"
date: 2008-10-27
forum: Apple Hardware Users
---

### Post by herzzreh on 2008-10-27
For the love of me, I can't figure out how to map the Apple key to act as CTRL on Xubuntu 8.10. "New" (for me) way of configuring hardware in it is a blah for me... don't know anything.

Any pointers on remapping the CTRL key? I figured out how to do it in GNOME but I'm not using it...

Previous gen Macbook.

---

### Post by paul_mcl on 2008-10-27
***1. In console.***

```

$ sudo dumpkeys | head -1 > /usr/share/keymaps/Ctrl2Command.map

```

Then add the following line to that file:

```

Keycode 125 = Control

```

Finish by referencing the new keymap to the KEYMAP variable in /etc/conf.d/keymaps. The keymaps boot script or the system will need to be restarted.

**Warning:** Don&#8217;t change /etc/conf.d/keymaps and restart the init script (/etc/init.d/keymaps) if the X server is running! It&#8217;s best to work from console with no X server going.

If you have 'loadkeys', you can use:

```

# loadkeys /usr/share/keymaps/Ctrl2Command.map

```

***2. In X11.***

In X Window you can use xmodmap(1) to change the keymaping. See its man page for more information.

The X server has a list of known keyboard mappings in /usr/share/X11/xkb/rules/xorg.lst. From there I was able to map the Control key to Apple:

```

    Option      "XkbOptions"    "altwin:ctrl_win"

```

---

### Post by herzzreh on 2008-10-27
> **paul_mcl said:**
> ***1. In console.***

```

$ sudo dumpkeys | head -1 > /usr/share/keymaps/Ctrl2Command.map

```

Then add the following line to that file:

```

Keycode 125 = Control

```

Finish by referencing the new keymap to the KEYMAP variable in /etc/conf.d/keymaps. The keymaps boot script or the system will need to be restarted.

**Warning:** Don’t change /etc/conf.d/keymaps and restart the init script (/etc/init.d/keymaps) if the X server is running! It’s best to work from console with no X server going.

If you have 'loadkeys', you can use:

```

# loadkeys /usr/share/keymaps/Ctrl2Command.map

```

***2. In X11.***

In X Window you can use xmodmap(1) to change the keymaping. See its man page for more information.

The X server has a list of known keyboard mappings in /usr/share/X11/xkb/rules/xorg.lst. From there I was able to map the Control key to Apple:

```

    Option      "XkbOptions"    "altwin:ctrl_win"

```

Thanks! Do I have to do 1 and 2 or is it 1 or 2?

---

### Post by paul_mcl on 2008-10-27
*>> Thanks! Do I have to do 1 and 2 or is it 1 or 2?*

If you're using primarily X11 (KDE/Gnome/XFCE/Enlightenment/etc.) and don't use console, do variant 2. If you're happy only with console (as I am), do variant 1. If you want total remap everywhere, do them both.

---

### Post by Rog-Mahal on 2008-10-27
Will this map both of the command keys? I found a fix, but it only maps the left one, the right is still dead.

---

### Post by herzzreh on 2008-10-27
> **paul_mcl said:**
> [B][I]1.

***2. In X11.***

In X Window you can use xmodmap(1) to change the keymaping. See its man page for more information.

The X server has a list of known keyboard mappings in /usr/share/X11/xkb/rules/xorg.lst. From there I was able to map the Control key to Apple:

```

    Option      "XkbOptions"    "altwin:ctrl_win"

```

Using the whole hal deal, where do I put that XkbOptions now that xorg.config isn't used...?

---

### Post by herzzreh on 2008-10-28
Anything? Fix posted here I cannot get to work. Either it really doesnt work with 8.10 or I'm an idiot! Someone post a step-by-step, pls.

---

### Post by paul_mcl on 2008-10-28
The following was taken from
[http://jyoseph.com/use-xmodmap-to-remap-keys-on-apple-aluminum-keyboard/](http://jyoseph.com/use-xmodmap-to-remap-keys-on-apple-aluminum-keyboard/)

First, create a file in your home directory. Browse to /home/yourusername/ and create a file called .xmodmap. Open the file and paste in the following:

```

remove control = Control_L Control_R 
keycode 115 = Super_L Super_L 
keycode 116 = Super_R Super_R 
add control = Super_L Super_R

```

Now, open up terminal and type the following:

```

xmodmap ~/.xmodmap 

```

---

### Post by herzzreh on 2008-10-28
> **paul_mcl said:**
> The following was taken from
[http://jyoseph.com/use-xmodmap-to-remap-keys-on-apple-aluminum-keyboard/](http://jyoseph.com/use-xmodmap-to-remap-keys-on-apple-aluminum-keyboard/)

First, create a file in your home directory. Browse to /home/yourusername/ and create a file called .xmodmap. Open the file and paste in the following:

```

remove control = Control_L Control_R 
keycode 115 = Super_L Super_L 
keycode 116 = Super_R Super_R 
add control = Super_L Super_R

```

Now, open up terminal and type the following:

```

xmodmap ~/.xmodmap 

```

This does work but icky about loading it every time. Does anyone know how to load it each time X starts?

---

### Post by cyberdork33 on 2008-10-28
> **herzzreh said:**
> This does work but icky about loading it every time. Does anyone know how to load it each time X starts?
add it to your session.

---

