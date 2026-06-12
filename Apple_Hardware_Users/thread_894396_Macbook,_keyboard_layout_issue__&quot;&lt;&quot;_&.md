---
title: "Macbook, keyboard layout issue : &quot;&lt;&quot; &lt;=&gt; &quot;@&quot; and &quot;&gt;&quot; &lt;=&gt; &quot;#&quot;"
date: 2008-08-19
forum: Apple Hardware Users
---

### Post by harobed on 2008-08-19
Hi,

I've Ubuntu 8.04.1 on Macbook 3,1 laptop.

Before last upgrade two week ago, my keyboard layout worked perfecly. Since, I've this key switched : 

"<" <=> "@"

and

">" <=> "#"

Is someone have this issue ?

This my xorg configuration :

```

Section "InputDevice"
    Identifier  "MBP Keyboard"
    Driver      "kbd"
    Option      "CoreKeyboard"
    Option      "XkbRules" "xorg"
    Option      "XkbModel" "macintosh"
    Option      "XkbLayout" "fr"
    Option      "XkbOptions" "lv3:lwin_switch" 
EndSection

```

Thanks for your help,
Stephane

---

### Post by volanin on 2008-08-19
Go to SYSTEM > PREFERENCES > KEYBOARD > LAYOUTS TAB.
And check if you have the correct keyboard layout set there!
:)

---

### Post by harobed on 2008-08-21
> **volanin said:**
> Go to SYSTEM > PREFERENCES > KEYBOARD > LAYOUTS TAB.
And check if you have the correct keyboard layout set there!
:)

I've already looked this, my keyboard layout is MacBook/MacBook Pro (Intl).

Regards,
Stephane

---

### Post by cyberdork33 on 2008-08-21
> **harobed said:**
> I've already looked this, my keyboard layout is MacBook/MacBook Pro (Intl).That is your keyboard type, what about the "layout" just below that.

---

### Post by harobed on 2008-08-21
> **cyberdork33 said:**
> That is your keyboard type, what about the "layout" just below that.

It's "French". I've a French Macbook keyboard. It's right.

Other idea ?

---

### Post by cyberdork33 on 2008-08-21
So is this not what your layout looks like? Did you not try the "macintosh" variant?

---

### Post by harobed on 2008-08-21
> **cyberdork33 said:**
> So is this not what your layout looks like? Did you not try the "macintosh" variant?

No, there aren't ! This key are swaped :

"<" <=> "@" and ">" <=> "#"

There aren't before my last synaptic upgrade.

Can I send to you other information about my configuration ?

---

### Post by harobed on 2008-08-21
> **harobed said:**
> No, there aren't ! This key are swaped :

"<" <=> "@" and ">" <=> "#"

There aren't before my last synaptic upgrade.

Can I send to you other information about my configuration ?

The keyboard layout picture is good on my configuration but real keyboard mapping isn't ! I don't understand.

---

### Post by cyberdork33 on 2008-08-21
> **harobed said:**
> The keyboard layout picture is good on my configuration but real keyboard mapping isn't ! I don't understand.
If that is the case, then it is probably a bug, and I would file a report in launchpad.

I think you can remap the keys manually, but I an not aware of how to do that. If you run 'xev' in a terminal, you can see the output information when you hit keys and use xmodmap to map them to the correct code. I am not familiar with how to do this though.

---

### Post by mabovo on 2008-08-21
> **cyberdork33 said:**
> If that is the case, then it is probably a bug, and I would file a report in launchpad.

I think you can remap the keys manually, but I an not aware of how to do that. If you run 'xev' in a terminal, you can see the output information when you hit keys and use xmodmap to map them to the correct code. I am not familiar with how to do this though.

Please, report for pt-br also.

Thanks !

---

### Post by _mario_ on 2008-08-23
I had a similar problem on a MacBookPro 4,1 with german keyboard layout, so this might not help you.

A few months ago after installing hardy, I observed that two keys were swapped: the one on the left side of 1 (^/°) and the one on the right side of left shift (</>). According to cyberdork33's screenshot, these are the keys you mentioned with french keyboard layout.

The reason is: Apple's keyboards report swapped keycodes for these two keys (observable on a text console and in X). Some months later, the Ubuntu kernel solved this problem, so these keys worked in both worlds. Until this time, I had to instruct the X server to swap these keys by using:
```
Option "XkbOptions" "apple:badmap"
```
(The text console still didn't work correctly).

I don't know why this problem occurs now. It should already be fixed. However, my keyboard configuration currently looks like this:
```

Section "InputDevice"
    Identifier  "MacKeyboard"
    Driver      "keyboard"
    Option      "XkbRules"              "xorg"
    Option      "XkbModel"              "pc105"
    Option      "XkbLayout"             "de"
    Option      "XkbVariant"            "mac_nodeadkeys"
    #Option     "XkbOptions"            "apple:badmap"
EndSection

```

The model is pc105 because macintosth didn't work well (no command keys, couldn't switch to text console, ...)

Hopefully this helps you ...

---

### Post by _mario_ on 2008-08-24
There is an easier way than the mentioned option: you can use the GNOME keyboard configuration as depicted below.

[IMG]http://www.ifsr.de/~mario/ubuntu/gnome-keyboard-options.png[/IMG]

---

### Post by fakt00r on 2009-04-23
Same problem here with my MacBook and Swiss German keyboard. As you wrote I tried to reconfig the xorg.conf. But compared to your keyboard configuration is mine commented out:
```
# commented out by update-manager, HAL is now used
#	InputDevice	"Generic Keyboard"
```

Still if I use the same configuration as you <> and §° are interchanged. How can I solve this problem. :confused:

---

### Post by cyberdork33 on 2009-04-23
> **fakt00r said:**
> Same problem here with my MacBook and Swiss German keyboard. As you wrote I tried to reconfig the xorg.conf. But compared to your keyboard configuration is mine commented out:
```
# commented out by update-manager, HAL is now used
#    InputDevice    "Generic Keyboard"
```Still if I use the same configuration as you <> and §° are interchanged. How can I solve this problem. :confused:
Please check this bug report:
[https://bugs.edge.launchpad.net/mactel-support/+bug/214786](https://bugs.edge.launchpad.net/mactel-support/+bug/214786)

---

