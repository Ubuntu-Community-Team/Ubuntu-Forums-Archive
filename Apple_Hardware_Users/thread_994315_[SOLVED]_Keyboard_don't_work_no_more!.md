---
title: "[SOLVED] Keyboard don't work no more!"
date: 2008-11-26
forum: Apple Hardware Users
---

### Post by Tu1J4kXk8NUhMz on 2008-11-26
So I've installed Ubuntu on a Macbook Pro Core2Duo (2nd gen i think) and discovered that my keyboard doesn't work. The NumLock button is stuck "on" and at one point I could only input to the computer using the number pad (the embedded one in the MBP keyboard). Now it doesn't even do that, AND when I try fudging with the keyboard settings, I get this in a pop-up.

> Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10400090

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

As requested by the pop-up, here are the appropriate outputs

```
:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"
```

```
:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us	mac]
 model = macbook78
 options = [lv3	lv3:ralt_switch,grp	grp:alts_toggle]
 overrideSettings = true
```

Any suggestions?

---

### Post by Tu1J4kXk8NUhMz on 2008-11-28
bump

---

### Post by Tu1J4kXk8NUhMz on 2008-11-28
Bump...no one knows what to do?

---

### Post by mabovo on 2008-11-29
Mine is configured like this:

mabovo@macbook:~$  xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "apple_laptop", "us", "", "lv3:ralt_switch,compose:rwin"
_XKB_RULES_NAMES(STRING) = "evdev", "apple_laptop", "us", "", "compose:rwin,compose:lwin"
mabovo@macbook:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us]
 model = apple_laptop
 options = [compose	compose:rwin,Compose key	compose:lwin]
mabovo@macbook:~$

---

### Post by _mario_ on 2008-12-02
> **teamjh14 said:**
> So I've installed Ubuntu on a Macbook Pro Core2Duo (2nd gen i think) and discovered that my keyboard doesn't work. The NumLock button is stuck "on" and at one point I could only input to the computer using the number pad (the embedded one in the MBP keyboard). Now it doesn't even do that, AND when I try fudging with the keyboard settings, I get this in a pop-up. As requested by the pop-up, here are the appropriate outputs:
```
:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "mac", "lv3:ralt_switch"
```
these settings are correct, in case you're happy with US layout and not having dead keys. just for reference, my settings on a MacBookPro 4:
```
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "de-addons", "mac_nodeadkeys", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "de-addons", "mac_nodeadkeys", ""

```
ignore 'de-addons'. i patched my language file. normally there should be 'de'.

> **teamjh14 said:**
> 
```
:~$ gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us	mac]
 model = macbook78
 options = [lv3	lv3:ralt_switch,grp	grp:alts_toggle]
 overrideSettings = true
```
Any suggestions?
the model is your problem. never select macintosh. this is completely broken. so disable gnome overrides, by running:
```
gconftool-2 /desktop/gnome/peripherals/keyboard/kbd/overrideSettings --type bool --set false
```
log out and log in.

for reference on my machine:
```
 layouts = []
 model = 
 options = []

```

in case, you want to configure something specific, start from scratch. this time selecting the right keyboard model. you might also add the options to your Xorg configuration or hal X11 configuration depending on what you're using.

ciao,
Mario

---

### Post by cyberdork33 on 2008-12-02
> **_mario_ said:**
> the model is your problem. never select macintosh. this is completely broken. 
Really? I use macintosh and it works fine... or maybe you are referring to non-US layouts...

---

### Post by _mario_ on 2008-12-02
> **cyberdork33 said:**
> Really? I use macintosh and it works fine... or maybe you are referring to non-US layouts...
i double-checked again. using the gnome dialog and selecting "MacBook/MacBookPro", i'll get the model string macbook78 in gconf. and yes it works fine. i was indeed referring to Hardy when i last tried this, and i swear, it didn't work. maybe an Xorg upgrade in the meantime did solve it?

on the other hand, teamjh14's settings should work as well, even if gnome for some reason cannot change the defaults. if i'm remembering correctly, i think i had this problem as well with Hardy. @teamjh14: which Ubuntu release are you running? Hardy or Intrepid?

ciao,
Mario

---

### Post by cyberdork33 on 2008-12-03
i've used it for several releases now. Of course, I am not working on a portable, this is on a full Apple keyboard.

---

### Post by Tu1J4kXk8NUhMz on 2008-12-03
> **_mario_ said:**
> i double-checked again. using the gnome dialog and selecting "MacBook/MacBookPro", i'll get the model string macbook78 in gconf. and yes it works fine. i was indeed referring to Hardy when i last tried this, and i swear, it didn't work. maybe an Xorg upgrade in the meantime did solve it?

on the other hand, teamjh14's settings should work as well, even if gnome for some reason cannot change the defaults. if i'm remembering correctly, i think i had this problem as well with Hardy. @teamjh14: which Ubuntu release are you running? Hardy or Intrepid?

ciao,
Mario

I'm running Hardy. And in response to Cyber, initially I just had the problem of my keyboard being stuck in "NumLock" mode, only allowing me to key in the numbers. This seems to be a common issue with MBPs for some reason (my generation at least). In trying to fix it...well, I broke it more.

Thanks for the responses, guys. I'd nearly lost hope and checked back to a massive amount of replies this evening!

---

### Post by cyberdork33 on 2008-12-04
> **teamjh14 said:**
> I'm running Hardy. And in response to Cyber, initially I just had the problem of my keyboard being stuck in "NumLock" mode, only allowing me to key in the numbers. This seems to be a common issue with MBPs for some reason (my generation at least). In trying to fix it...well, I broke it more.
Hitting F6 a couple times will toggle the numlock mode. Also, I believe that problem is fixed if you update.

---

### Post by Tu1J4kXk8NUhMz on 2008-12-04
> **cyberdork33 said:**
> Hitting F6 a couple times will toggle the numlock mode. Also, I believe that problem is fixed if you update.

F6 didn't actually work for me. I found that solution (fortunately) before I started messing with xorg.conf at all, and it didn't work. Also, I just ran Update-Manager about a week ago. Is this a recent update?

I may have fixed the problem. How, I'm not sure. I just reset Xorg.conf (with the line of code provided in the comments of it) and the keyboard *seems* to work. However, I've only tried it after logging out then in again.

And, on a related note, I'm still getting the error message. I'm a little leery that it is indeed "fixed," as I had a USB keyboard hooked to it at the time. I'll test a bit more later to find out for sure.

---

### Post by cyberdork33 on 2008-12-05
> **teamjh14 said:**
> And, on a related note, I'm still getting the error message. I'm a little leery that it is indeed "fixed," as I had a USB keyboard hooked to it at the time. I'll test a bit more later to find out for sure.
The error message has to do with the keyboard selection in gnome and the keyboard config in xorg are different. (It is actually not a big issue, but it is annoying.) You just need to set the keyboard selections the same in both gnome and xorg.

---

### Post by Tu1J4kXk8NUhMz on 2008-12-07
> **cyberdork33 said:**
> The error message has to do with the keyboard selection in gnome and the keyboard config in xorg are different. (It is actually not a big issue, but it is annoying.) You just need to set the keyboard selections the same in both gnome and xorg.

You rock. Everything works awesome! With all the help you've given me, Cyber, I feel like you should be my Ubuntu mentor. :-P

---

