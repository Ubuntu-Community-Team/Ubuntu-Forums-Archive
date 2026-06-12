---
title: "[SOLVED] Turn off desktop mouse scroll feature"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by devils3cups on 2008-02-24
Hey guys,

How do I turn off the feature that allows me to change desktops by using the mouse scroll.

I have a laptop and if i'm looking at the desktop sometimes it will start changing the desktops because i'm on the scroll.

Thanks,
raig

---

### Post by Presto123 on 2008-02-24
Hey there. Do you have the Compiz Configuration utility installed?

I can guide you from there.

---

### Post by devils3cups on 2008-02-24
Yes i do

---

### Post by Presto123 on 2008-02-24
Okay...go into there (note that this will only disable THAT feature since it is what is giving you trouble) and find "Rotate Cube". Click on the tab marked "Actions". It will probably show "General" and nothing else, click on it so that it will expand the menu and the first thing there says "Initiate". You can type in "None" in the button field and exit.

That should get it.

---

### Post by Presto123 on 2008-02-24
I apologize...that is incorrect.

It's actually the "Rotate Left" and "Rotate Right" ones in there.

In case you have already changed the "Intiate" button, click on it and enter in this again:

```
<Control><Alt>Button1
```

---

### Post by devils3cups on 2008-02-24
Unfortunately that didn't work

---

### Post by Presto123 on 2008-02-24
Sadly...I thought I had done this before and it worked. But, I am getting the same problem as you. Turning off "Rotate Cube" is the only thing that is working on that. I'll keep twiddling around with it and hopefully find which one it is exactly.

---

### Post by Presto123 on 2008-02-24
Looks like turning off "Rotate Cube" is it. As I said before, I'll remember to let you know if I find out anything different. Or someone else here may have a clue.

---

### Post by devils3cups on 2008-02-24
Actually turning off rotate cube makes the problem worse. When it switches from desktop to desktop it does it very fast and I'm not able to control which screen I go to. This probably means it has nothing to do with Compiz right?

---

### Post by jordanmthomas on 2008-02-24
Try disabling the "Viewport Switcher" plugin.
I had to enable it to get desktop-scrolling to work, so I'd assume it works the opposite way too.

---

### Post by devils3cups on 2008-02-25
And this is found where?

---

### Post by devils3cups on 2008-02-25
Stupid me. Thanks that was it!

---

### Post by Ripfox on 2008-02-25
It's called "Desktop Wall"

---

