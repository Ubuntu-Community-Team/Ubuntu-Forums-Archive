---
title: "apple keyboard xmodmap atl and super"
date: 2007-10-28
forum: Apple Intel Users
---

### Post by zeusfaber on 2007-10-28
I am attempting to setup my macbook with the correct key bindings. I have turned the left apple key into left ALT but it seems that I cannot seem to get the original left ATL/option to turn into left super. I have modified my xmodmap (below) to do so as well. Below is a snip from the 'xev' command and it looks like it is interpreting the keys right but when attempt to use super in X (compiz key combos etc) it does not seem to work as expected. Any ideas on how to correct this?

```

KeyPress event, serial 30, synthetic NO, window 0x3600001,
    root 0x59, subw 0x0, time 3886262327, (626,120), root:(632,139),
    state 0x0, keycode 115 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3600001,
    root 0x59, subw 0x0, time 3886262439, (626,120), root:(632,139),
    state 0x8, keycode 115 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 30, synthetic NO, window 0x3600001,
    root 0x59, subw 0x0, time 3886264831, (626,120), root:(632,139),
    state 0x0, keycode 64 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 30, synthetic NO, window 0x3600001,
    root 0x59, subw 0x0, time 3886264943, (626,120), root:(632,139),
    state 0x8, keycode 64 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

my .xmodmap:
```

keycode 115 = Alt_L
keycode 64 = Super_L
keycode 116 = Pointer_Button2
keycode 108 = Pointer_Button3

```

---

### Post by FunkyM on 2007-10-28
gnome-keyboard-properties > Layout Options > Alt/Win Behaviour > Swap Left-Alt with Left-Win key

Works for me :)

---

### Post by zeusfaber on 2007-10-28
i am running xubuntu ... anyone know what this changes? so i can adjust it in the underlying system? know of a xfce way to do the same thing?

---

### Post by [woodstock] on 2007-10-30
This work for me on a MBP C2D

> !! xmodmap for Apple MacBook - German layout
!!
! Let the left apple key act as mode switch
keycode 115 = Super_L

! Use the right apple switch as "ALT_GR" key, provides the additional
! characters you find on a tradition pc keyboard (example @)
keycode 116 = ISO_Level3_Shift NoSymbol

! Use the Delete key correctly
! Maps to center mouse if used with left apple key
keycode 108 = Delete Delete


---

### Post by zeusfaber on 2007-10-30
cool, i will give it a shot.

---

### Post by doublemeat on 2007-11-01
Yes, Swap Left-Alt with Left-Win key is the way to go.  I tried doing it with xmodmap too--and although it worked, it had some issues.  The "Swap Left-Alt with Left-Win key" option is not perfect, but much cleaner, and, well, you do it in a GUI.

---

