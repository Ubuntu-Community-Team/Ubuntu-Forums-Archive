---
title: "how resize this wine window"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by Tok-Tok on 2007-10-12
I make a mistake at Virtual Desktop setting in winecfg, so how i can change windowsize from this unresizeable window?

---

### Post by ryanVickers on 2007-10-12
can you not grab the side?!

---

### Post by Tok-Tok on 2007-10-12
sorry no, that would be a bit to easy ;)

---

### Post by ryanVickers on 2007-10-12
can you right-click on it's bar in the window list (you know, in the panel, shows all open windows) and pick "resize"? (please say yes! [-o<)

---

### Post by Tok-Tok on 2007-10-12
I try this to, it´s grey out, fourth from above.

---

### Post by qamelian on 2007-10-12
Can't you just run winecfg again and correct the settings for a virtual desktop?

---

### Post by Tok-Tok on 2007-10-12
that was u see on my last attachmets it was i get whit winecfg, the window is to small,cant go in whit the mouse pointer and cant reach the settings blindly whit tabulator.

---

### Post by ryanVickers on 2007-10-12
is there some way to force it to open with certain dimensions? ;)

---

### Post by Tok-Tok on 2007-10-12
I dont realy know it but if anybody give me a reg file whit the right key to change the Virtual Desktop whit command line regedit to off it can possibly help.

Solve the problem by my self but thanks try to help me

Mak a file like this

REGEDIT

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"Desktop"="N"

save as whatuwant.reg

type: regedit whatuwant.reg

---

