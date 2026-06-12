---
title: "Ctrl+Alt+Backspace does nothing (Xfce)"
date: 2008-03-16
forum: Arch and derivatives
---

### Post by PurposeOfReason on 2008-03-16
Just because these forums are faster, could someone answer why I ctrl alt backspace doesn't restart X, or do anything, when I press it?

[http://bbs.archlinux.org/viewtopic.php?id=45535](http://bbs.archlinux.org/viewtopic.php?id=45535)

---

### Post by K.Mandla on 2008-03-16
Odd. Do you have something else mapped that might be interfering with it?

---

### Post by PurposeOfReason on 2008-03-16
> **K.Mandla said:**
> Odd. Do you have something else mapped that might be interfering with it?
Nope. :/

---

### Post by Gigamo on 2008-03-17
> **PurposeOfReason said:**
> Nope. :/

Have you tried adding a keybind for it in your xfce settings? I see an 'add' button in the picture on the arch forums :)

---

### Post by Tomatz on 2008-03-17
Strange no probs here (xubuntu):confused:

---

### Post by PurposeOfReason on 2008-03-17
> **Gigamo said:**
> Have you tried adding a keybind for it in your xfce settings? I see an 'add' button in the picture on the arch forums :)
I tried to make a whole new profile and that. It's not doing much.

---

### Post by raul_ on 2008-03-17
Do you have ANY .xbindkeysrc on your home folder (I think that's the file)

---

### Post by PurposeOfReason on 2008-03-17
I do. Why would that matter? Here it is. It only uses the FN key for volume and the ctrl + arrow keys for mpd.
```
# For the benefit of emacs users: -*- shell-script -*-
###########################
# xbindkeys configuration #
###########################
#
# Version: 1.8.2

"~/.scripts/changevol -t"
    m:0x0 + c:160

"~/.scripts/changevol -d5"
    m:0x0 + c:174

"~/.scripts/changevol -i5"
    m:0x0 + c:176

"mpc toggle"
    m:0x4 + c:104
    
"mpc next"
    m:0x4 + c:102"
    
"mpc prev"
    m:0x4 + c:100"

"sonata"
    m:0x0 + c:159


##################################
# End of xbindkeys configuration #
##################################
```

---

### Post by Gigamo on 2008-03-17
> **PurposeOfReason said:**
> I do. Why would that matter? Here it is. It only uses the FN key for volume and the ctrl + arrow keys for mpd.
```
# For the benefit of emacs users: -*- shell-script -*-
###########################
# xbindkeys configuration #
###########################
#
# Version: 1.8.2

"~/.scripts/changevol -t"
    m:0x0 + c:160

"~/.scripts/changevol -d5"
    m:0x0 + c:174

"~/.scripts/changevol -i5"
    m:0x0 + c:176

"mpc toggle"
    m:0x4 + c:104
    
"mpc next"
    m:0x4 + c:102"
    
"mpc prev"
    m:0x4 + c:100"

"sonata"
    m:0x0 + c:159


##################################
# End of xbindkeys configuration #
##################################
```

Hey, I know its offtopic, but thanks to you my laptop's multimedia keys now work! :D

---

### Post by raul_ on 2008-03-17
Well, I had some issues in XFCE (whenever I the ALT key, my windows would close), just try renaming that file to .xbindkeysrc_old or something like that and restart X.

---

### Post by PurposeOfReason on 2008-03-17
> **Gigamo said:**
> Hey, I know its offtopic, but thanks to you my laptop's multimedia keys now work! :D
You're welcome? lol. Renaming it right now and all that. It was a busy weekend

Switched from wicd to netcfg2. Way better.
Who uses GDM? autologin with bash_profile and innittab
Got mpd for a normal user
configured the fans
Got the laptop to 4.5 hours on battery

Setting up a personal server too once the old mini dell p3 arrives. :)

---

### Post by PurposeOfReason on 2008-03-17
Well that got it, but is there a way to still keep xbindkeys?

---

### Post by Gigamo on 2008-03-17
Hmm, could you point me to netcfg2/how does it work? (offtopic again!)

---

### Post by PurposeOfReason on 2008-03-17
> **Gigamo said:**
> Hmm, could you point me to netcfg2/how does it work? (offtopic again!)
PM sent so I don't derail my own thread.

---

### Post by D-EJ915 on 2008-03-17
check your xorg.conf or the program which runs X, there's an option to disable that keystroke

---

