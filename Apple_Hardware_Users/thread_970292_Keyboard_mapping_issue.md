---
title: "Keyboard mapping issue"
date: 2008-11-04
forum: Apple Hardware Users
---

### Post by AlainJLEB on 2008-11-04
Hi there,

After the upgrade to 8.10, my keyboard mapping is "shitty".

The thing is that it is well set to Mac French keyboard, but the functions keys are not mapped, so can't use them ... except for the F10-11-12, which are mapped to sound.

When looking at the log from X, it seems it is correctly loaded, but there are some strange messages as well:
```
grep -i keyb /var/log/Xorg.0.log
(**) |-->Input Device "Generic Keyboard"     
(II) Initializing built-in extension XKEYBOARD
(**) Option "CoreKeyboard"                    
(**) Generic Keyboard: always reports core events
(**) Generic Keyboard: Protocol: standard        
(**) Generic Keyboard: XkbRules: "xorg"          
(**) Generic Keyboard: XkbModel: "pc105"         
(**) Generic Keyboard: XkbLayout: "fr"           
(**) Generic Keyboard: XkbVariant: "mac"         
(**) Generic Keyboard: CustomKeycodes disabled   
(II) evaluating device (Generic Keyboard)        
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Apple Mac mini infrared remote control driver: Configuring as keyboard  
(II) XINPUT: Adding extended input device "Apple Mac mini infrared remote control driver" (type: KEYBOARD)
(II) config/hal: Adding input device Apple, Inc Apple Keyboard                                            
(**) Apple, Inc Apple Keyboard: always reports core events                                                
(**) Apple, Inc Apple Keyboard: Device: "/dev/input/event11"                                              
(II) Apple, Inc Apple Keyboard: Found keys                                                                
(II) Apple, Inc Apple Keyboard: Configuring as keyboard                                                   
(II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)                    
(**) Apple, Inc Apple Keyboard: xkb_rules: "evdev"
(**) Apple, Inc Apple Keyboard: xkb_model: "pc105"
(**) Apple, Inc Apple Keyboard: xkb_layout: "fr"
(**) Apple, Inc Apple Keyboard: xkb_variant: "mac"
(II) config/hal: Adding input device Apple, Inc Apple Keyboard
(**) Apple, Inc Apple Keyboard: always reports core events
(**) Apple, Inc Apple Keyboard: Device: "/dev/input/event10"
(II) Apple, Inc Apple Keyboard: Found keys
(II) Apple, Inc Apple Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Apple, Inc Apple Keyboard" (type: KEYBOARD)
(**) Apple, Inc Apple Keyboard: xkb_rules: "evdev"
(**) Apple, Inc Apple Keyboard: xkb_model: "pc105"
(**) Apple, Inc Apple Keyboard: xkb_layout: "fr"
(**) Apple, Inc Apple Keyboard: xkb_variant: "mac"
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(WW) Apple, Inc Apple Keyboard: unable to handle keycode 469
(WW) Apple, Inc Apple Keyboard: unable to handle keycode 470

```
What is this "evdev" rule? 

Beside this, there is no layout specified in KDE in the Regional settings that might override it.
Any idea on how to sort this? This is pretty annoying

---

### Post by valahul on 2008-11-05
I have the same problem after upgrade to 8.1 on a Dell Inspiron 1501.
For example, my down key produce a screen capture!
Somebody can help me?

---

### Post by AlainJLEB on 2008-11-08
> **valahul said:**
> I have the same problem after upgrade to 8.1 on a Dell Inspiron 1501.
For example, my down key produce a screen capture!
Somebody can help me?

This is an Apple forum.

Anyone here having his french keyboard working correctly under 8.10 ??? There are keys like Alt which are also not working, so this is a really annoying issue. And what about evdev?

---

### Post by stream303 on 2008-11-09
Although I can't help with the immediate problem, many years ago I remember a tip from someone else stating that when installing on an Apple, let the system use the American keyboard configuration first, and then once installed, go ahead and switch to the language of your specific locale.

For some reason, choosing your specific non-american locale during install sometimes corrupted the settings, even if it looks like it was setup properly during install.  So the best bet for the Apple machines was to set it up for a non-American keyboard later.

I never had this problem so perhaps this is an urban-legend? :)

---

### Post by AlainJLEB on 2008-11-09
> **stream303 said:**
> Although I can't help with the immediate problem, many years ago I remember a tip from someone else stating that when installing on an Apple, let the system use the American keyboard configuration first, and then once installed, go ahead and switch to the language of your specific locale.

For some reason, choosing your specific non-american locale during install sometimes corrupted the settings, even if it looks like it was setup properly during install.  So the best bet for the Apple machines was to set it up for a non-American keyboard later.

I never had this problem so perhaps this is an urban-legend? :)

Since it was working (almost) fine before the upgrade, I guess it's more an urban legend ...

---

### Post by AlainJLEB on 2008-11-13
In my initial post I'm pointing the following:
```
(**) Apple, Inc Apple Keyboard: xkb_rules: "evdev"
(**) Apple, Inc Apple Keyboard: xkb_model: "pc105"
(**) Apple, Inc Apple Keyboard: xkb_layout: "fr"
(**) Apple, Inc Apple Keyboard: xkb_variant: "mac"
```

I've read that evdev is a feature between kernel and X linked to devices. I'll also read that I can see what are the keys recognized under X through xev ... but after, how can I correct this ?

---

