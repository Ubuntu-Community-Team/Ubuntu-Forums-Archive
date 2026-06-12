---
title: "Map Lower &quot;Enter&quot; key as &quot;Ctrl&quot;?"
date: 2007-10-20
forum: Apple Intel Users
---

### Post by dmber on 2007-10-20
Is there an easy way to do this?  I'd like a Ctrl key on both sides of the space bar.

Thanks.

---

### Post by mert on 2007-10-20
execute these two shell commands:

xmodmap -e 'keycode 108 = Control_R'
xmodmap -e 'add Control = Control_R'

I think you can also put them in a file named ~/.xmodmap or ~/.xmodmaprc then they will be executed at login time but I haven't tried it yet.

---

### Post by dmber on 2007-10-20
when you "execute shell commands" that means run each of those lines by itself in the terminal, right?

thanks.

---

### Post by mert on 2007-10-20
Yup! :)

---

### Post by dmber on 2007-10-20
> **mert said:**
> execute these two shell commands:

xmodmap -e 'keycode 108 = Control_R'
xmodmap -e 'add Control = Control_R'

I think you can also put them in a file named ~/.xmodmap or ~/.xmodmaprc then they will be executed at login time but I haven't tried it yet.
i can't find that file...

and the two shell commands didn't work.

---

### Post by [woodstock] on 2007-10-21
I have tried these two commands too since I wanted to check aother keyboard configuration. These commands work and the effect is applied immediately.

The file probably doesn't exist in most cases, juste create it.

This is my file (german layout)

> ! Use the right apple switch as "ALT_GR" key, provides the additional
! characters you find on a tradition pc keyboard (example @)
keycode 116 = ISO_Level3_Shift NoSymbol

! Use the Delete key correctly
! Maps to center mouse if used with left apple key
keycode 108 = Delete Delete

! Page Up/Down with ALT_GR additionally to FN-Key
!keycode 98 = Up NoSymbol
!keycode 104 = Down NoSymbol
!keycode 100 = Left NoSymbol
!keycode 102 = Right NoSymbol


! maps @ on L key, too
!keycode 46 = l L at at at at
keycode 46 = l L  NoSymbol NoSymbol 

! maps euro symbo
!keycode 26 = e E EuroSign EuroSign EuroSign EuroSign
!keycode 26 = e E

Note, that the lines with the excalmation mark will be ignored. I am not fully satisfied with my configuration yet, so this file is experimental and contains a lot of garbage.
You would have to change keycode 108 which is mapped to the delete key by me.

Using a xmodmap file, restarting the x server is required to make the changes work.

---

