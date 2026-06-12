---
title: "Keyboard mapping issue after upgrade to 8.04"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by AlainJLEB on 2008-04-25
Hi there,

After the sound problem, I've just discovered a new annoying one: since the upgrade, the keyboard mapping is no more correct.

On my alumni iMac 24, I'm using a French azerty keyboard ... in 7.10, I had configured it correctly to have thing working fine, except the F7 to F12 special keys (back,play,fw,sound, ...)

Since the upgrade, those keys are now working ... but the @/# key (below ESC) has been switched with the </> (at right of left shift).

Beside this, CTRL-F1 to CTRL-F4 is not working anymore ... when I try to change the shortcut sequence in the system settings of Kubuntu, hitting CTRL-F1 is recognized as Ctrl-XF86LaunchD ... CTRL-F1 is recognized as Ctrl-XF86LaunchE ...

The keyboard config of Xorg is the following:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "mac"
EndSection
```

When looking at the content of the fr file in /usr/share/X11/xkb/symbols/macintosh_vndr, it seems that mapping is correct there:
```
key <TLDE> {        [          at,    numbersign,   periodcentered,         Ydiaeresis      ]       };
```

Any idea?
Alain

---

### Post by cyberdork33 on 2008-04-25
> **AlainJLEB said:**
> Any idea?
Alain
check the keyboard setting in gnome as opposed to xorg. System > Preferences > Keyboard, Layout tab

---

### Post by AlainJLEB on 2008-04-26
> **cyberdork33 said:**
> check the keyboard setting in gnome as opposed to xorg. System > Preferences > Keyboard, Layout tab

I'm under Kubuntu ... and there keyboard mapping is also set to mac-fr

In /var/log/kdm.log, I see the following:
```
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
```
Any idea on this?

```
grep -i key Xorg.0.log
(**) |-->Input Device "Generic Keyboard"
(II) Initializing built-in extension XKEYBOARD
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Generic Keyboard: Protocol: standard
(**) Generic Keyboard: XkbRules: "xorg"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Generic Keyboard: XkbLayout: "fr"
(**) Generic Keyboard: XkbVariant: "mac"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled
SetGrabKeysState - enabled
```
Above is extract from the Xorg log file ... where does come this extended input?

---

### Post by AlainJLEB on 2008-04-28
Following my investigations, it is still not working. Applying a keyboard scheme in Kubuntu does not change anything. 

I still have 2 keys swapped (@# with <>), and the functions keys are not working as desire ... can one let me know where I can search to solve this annoying behavior?

Regards
Alain

---

### Post by blurg on 2008-04-28
The kernel changes they did with mac keyboards may have changed the f-key behaviours, if I recall correctly.

What is the difference in the f-key behaviours between now and your old setup?

---

### Post by AlainJLEB on 2008-05-09
> **blurg said:**
> The kernel changes they did with mac keyboards may have changed the f-key behaviours, if I recall correctly.

What is the difference in the f-key behaviours between now and your old setup?

[LIST]
[*]The key at the left of 1 is <> instead of @#
[*]As a result, the key at the left of w (azerty keyboard) is @# instead of <>
[*]The function keys F1, F2, F3 and F4 are not recognized - they have special functions under OSX
[*]F7 to F12 keys are recognized as "multimedia keys", as they are under OSX.
[/LIST]

So it looks like the keyboard is similar to what it is under OSX, except for the swift between 2 keys ... but the annoying effect is that F1 to F4 are not recognized, keys are switched, ... **how can I solve this? There is no keyboard mapping applied, and the same behavior applies in console mode.**

Thanks

---

### Post by mul14 on 2008-12-03
I have same problem.. after upgrade Ubuntu kernel from 2.6.27-7-generic to 2.6.27-9-generic, right button, up button and down button can not work..

Someone.. please help me..

---

### Post by mul14 on 2008-12-03
Hi.. My keyboard now worked properly after do this
```

sudo dpkg-reconfigure xserver-xorg

```
Reboot,
then everything back to normaly. Except my nvidia driver, so I ran this
```

sudo nvidia-xconfig

```
Done..

---

### Post by _mario_ on 2008-12-03
EDIT: is the forum broken? i surely selected another thread to reply to.

---

