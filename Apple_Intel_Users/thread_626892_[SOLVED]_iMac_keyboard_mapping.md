---
title: "[SOLVED] iMac keyboard mapping"
date: 2007-11-29
forum: Apple Intel Users
---

### Post by AlainJLEB on 2007-11-29
Hi there,

I am fighting hard to solve a stupid issue: I have a belgian azerty keyboard (very similar to the french one), but there are some characters I can display, like pipe, sqare brackets, ...

When I look at the content of xorg.conf, I see the following regarding the keyboard:
```
Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "fr"
        Option      "XkbVariant" "mac"
EndSection

```

When I look at the /usr/share/X11/xkb/symbols/macintosh_vndr/fr file, I can see that bar (=pipe sign) is set to alt-shift-L ... which is working fine under MacOS-X ... but no way under Ubuntu.

What am I missing? In the the Xorg.log, I can see the following:
```
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "fr"
(**) Generic Keyboard: XkbLayout: "fr"
(**) Option "XkbVariant" "mac"
(**) Generic Keyboard: XkbVariant: "mac"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
```

Good or not?
Help would be appreciated :)

---

### Post by cyberdork33 on 2007-11-29
do you not want the belgian keyboard layout?
```
  Option  "XkbLayout"     "be"
```

---

### Post by AlainJLEB on 2007-11-30
I don't find mapping for belgian keyboard under /usr/share/X11/xkb/symbols/macintosh_vndr ...

I bought the iMac in Belgium, and thekeyboard is an azerty one ... but I can't find if there is any difference between belgian and french one ... both are azerty. There are differences on Dell's keyboards between french and belgian, is the same for Apple's ones?

On the other hand, I don't really care if it is belgia or french: the only thing I want is to be able to enter special characters, which I can't succeed.

Any idea on what I can check under kubuntu or X?

---

### Post by cyberdork33 on 2007-11-30
try forgetting about the mac keyboard variant. There are really not enough differences to matter. comment out that line and change to be layout, then try restarting Xorg.

From what I could tell, there are some slight differences betweeen the belgian standard and french standard azerty.

There are also options in Gnome for keyboard layouts, but I do not know where they are located in KDE.

According to [this]("http://en.wikipedia.org/wiki/AZERTY"), the pipe symbol is AltGr + 1 on a Belgian variant and AltGr + 6 on the French Variant.

---

### Post by AlainJLEB on 2007-12-02
When booting OSX, and checking the keyboard, it is set to French azerty keyboard, and I can get the pipe sign, square brackets and so on.

But no way under Linux; the keyboard mapping is set to be mac/fr/pc105, but impossible to display those symbols, despite the fact that the mapping is there in /usr/share/X11/xkb/symbols/macintosh_vndr/fr:
```
    key <AC08> {        [         k, K,      Egrave,     Ediaeresis     ]       };
**[COLOR="Red"]    key <AC09> {        [         l, L,     notsign,            bar     ]       };[/COLOR]**
    key <AC10> {        [         m, M,          mu,         Oacute     ]       };
```

Is someone using an azerty french keyboard and being able to display those symbols? If yes, please provide me with your xorg.conf and kemap file.

Thanks

---

