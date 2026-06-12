---
title: "Macbook Pro - need help with keyboard setup ..."
date: 2008-12-01
forum: Apple Hardware Users
---

### Post by skullmunky on 2008-12-01
Hi,

I just installed Kubuntu 8.10 on my MacBook Pro.  So far, so good, but I'm stuck on the keyboard setup.  I've been banging my head against xmodmap, setkeycodes, loadkeys, etc. for hours, but I'm sure this is not that hard to solve.  I've been trying to use the xmodmap examples in the Wiki, but no luck :( 

Here's what I want:

1. use Apple key for Alt
2. use Ctrl+Click for R-Click
3. maybe R-Apple-Click for M-Click, or something.  

(1) and (2) are how OSX uses those keys, and my fingers are used to those positions on the mac keyboard, so that's why I want to do this.  

so far this is the only thing that's less than stellar, everything else worked out of the box, which I must say I'm really excited about. :)

---

### Post by cyberdork33 on 2008-12-01
> **skullmunky said:**
> 
1. use Apple key for Alt
2. use Ctrl+Click for R-Click
3. maybe R-Apple-Click for M-Click, or something.  

(1) and (2) are how OSX uses those keys, and my fingers are used to those positions on the mac keyboard, so that's why I want to do this.
I don't think anyone has gotten pressedkey+click to work for anything yet. there are several other ways to get right (and middle) click working though.

Apple uses the alt key as the alt key, so I don't know what you mean there. Maybe you are talking about the Control key?

---

### Post by skullmunky on 2008-12-03
I stumbled on the two-finger and three-finger tap option completely by accident :)  Turns out it was set up automatically, and I couldn't figure out why I kept accidentally copying and pasting text all over the place ... 

For the Alt key: what I mean is, on my keyboard the keys go:

Fn   Ctrl   Option/Alt   Apple/Splat/Command   Spacebar

Yes, the Option/Alt key does work as an Alt key correctly.  But, it's in the wrong place.  On a normal PC keyboard Alt is bigger and right next to the spacebar, which is where Apple/Splat is.  In OSX, AppleSplat + Tab is the window switcher, and I want to use the same key combination in Ubuntu because my fingers are so trained for it.  And the amount of wrist rotation / thumb strain it needs is less uncomfortable than OptionAlt + Tab.  

Here's what I did:

.Xmodmap
```

keycode 133 = Alt_L Meta_L Alt_L Meta_L Alt_L Meta_L
keycode 64 = Super_L NoSymbol Super_L NoSymbol Super_L

```

and it mostly worked, although now when I Alt-Tab and choose another window, it doesn't recognize -releasing- the key. I have to hit Tab again for that.  But it's close enough.

---

### Post by cyberdork33 on 2008-12-03
Control+Tab works for window switching too... but yes swapping the Option and Command  keys is what you want to do. I think there is an option to swap alt and super in the gnome keyboard config.

---

### Post by _mario_ on 2008-12-04
> **skullmunky said:**
> 
Yes, the Option/Alt key does work as an Alt key correctly.  But, it's in the wrong place.  On a normal PC keyboard Alt is bigger and right next to the spacebar, which is where Apple/Splat is.  In OSX, AppleSplat + Tab is the window switcher, and I want to use the same key combination in Ubuntu because my fingers are so trained for it.  And the amount of wrist rotation / thumb strain it needs is less uncomfortable than OptionAlt + Tab.  

Here's what I did:

.Xmodmap
```

keycode 133 = Alt_L Meta_L Alt_L Meta_L Alt_L Meta_L
keycode 64 = Super_L NoSymbol Super_L NoSymbol Super_L

```

and it mostly worked, although now when I Alt-Tab and choose another window, it doesn't recognize -releasing- the key. I have to hit Tab again for that.  But it's close enough.
if you move modifier keys, you'll have to update the modifier map as well.

however, what about configuring your window manager to use command+tab to switch between windows? or use the GNOME preferences dialog to swap those keys?

ciao,
Mario

---

### Post by skullmunky on 2008-12-10
> **_mario_ said:**
> if you move modifier keys, you'll have to update the modifier map as well.

however, what about configuring your window manager to use command+tab to switch between windows? or use the GNOME preferences dialog to swap those keys?

ciao,
Mario

oh, yeah, that would be easier, wouldn't it :)  I'll go see if I can find where to do that in KDE 4 ...

---

