---
title: "KDE/Gnome"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Benbow on 2007-07-02
I am a little confused, I have installed through synaptic. a program called "kreetingkard" for my wife. I am now unable to find it. I believe it is in KDE and I am running Gnome. Is this a problem, and how can I solve it?
Thanks

---

### Post by reset3x on 2007-07-02
> **Benbow said:**
> I am a little confused, I have installed through synaptic. a program called "kreetingkard" for my wife. I am now unable to find it. I believe it is in KDE and I am running Gnome. Is this a problem, and how can I solve it?
Thanks

What happens if you run kreetingkard in a terminal?

---

### Post by arijit on 2007-07-02
Press "ALT+F2" in gnome desktop.
type "kreetingkard" and ENTER.

alternatively, you can add menu item from "System -> Preferences -> Main Menu".

---

### Post by Pragmatist on 2007-07-02
what happens if you type this in a terminal:
```
kreetingkard
```Did that run the program?  edit: Sorry I see someone already posted this suggestion.

If not, try typing these commands:
```
sudo updatedb
```Wait for this to finish--it can take a few minutes.  Then,

```
locate kreetingkard
```

---

