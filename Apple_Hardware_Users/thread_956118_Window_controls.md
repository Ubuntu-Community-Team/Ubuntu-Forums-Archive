---
title: "Window controls"
date: 2008-10-22
forum: Apple Hardware Users
---

### Post by fatum on 2008-10-22
I first installed Kubuntu on my powerbook last week and have now switched that over to Ubuntu. One thing that I found in Kubuntu easily was how to change over the window controls (maximize, minimize and close) to the left side of the windows. I know this can be done in Gnome also but can not figure it out. Anyone have ideas? I did a search figuring that this was already covered but didn't come up with anything. thanks in advance.

---

### Post by cyberdork33 on 2008-10-22
I think this is defined in the theme.

OK found it.

hit ALT+F2 and run 'gconf-editor'

Navigate to apps > metacity > general

Now on the right side, you will see a item named "button_layout". double click on it to edit the value of this key.

Change it from the default:
"menu:minimize,maximize,close"

To the same order it appears in OSX:
"close,minimize,maximize:menu"

Click OK and everything should change!

---

### Post by scott.nightingale on 2010-05-10
brilliant thank you!

---

### Post by faithsnathan on 2010-10-12
> **cyberdork33 said:**
> I think this is defined in the theme.

OK found it.

hit ALT+F2 and run 'gconf-editor'

Navigate to apps > metacity > general

Now on the right side, you will see a item named "button_layout". double click on it to edit the value of this key.

Change it from the default:
"menu:minimize,maximize,close"

To the same order it appears in OSX:
"close,minimize,maximize:menu"

Click OK and everything should change!

When I installed Ubuntu today, all the buttons were on the left side of the screen (I was so confused for a minute!).  Following your advise in reverse, I got it back on the right side of the screen where I was used to from using Win7.  Thanks!

---

