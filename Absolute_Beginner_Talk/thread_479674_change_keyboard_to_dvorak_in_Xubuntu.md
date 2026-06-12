---
title: "change keyboard to dvorak in Xubuntu?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by hotani on 2007-06-20
I want to use Xubuntu, but every time I try it, I can't change the keyboard to Dvorak. In the keyboard settings there is a box checked which reads "use X settings." While this is checked, no options are available for editing. If i uncheck it, I can add Dvorak as a layout, but after closing the window it is not there. When I open it again, the box is magically checked again and my settings are gone.

Is this a flaw in XFCE, or with my system? Is anyone else using dvorak with Xubuntu?

I did install the Xubuntu-desktop package on top of Ubuntu, so I'm not sure if that has anything to do with this issue or not.


EDIT: I found a fix, but only partial. This command will change the layout:
```
setxkbmap dvorak
```

However, I haven't found a way to add it to my startup programs a la gnome.

---

### Post by capecove on 2007-06-20
Hey hotani, have you seen this?

[https://answers.launchpad.net/ubuntu/+question/1848](https://answers.launchpad.net/ubuntu/+question/1848)

It may help somewhat. When you say "In the keyboard settings there is a box checked which reads "use X settings." I suppoe you could be remarking about that which I just sent you. Please let us know if you still need assistance.

---

