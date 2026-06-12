---
title: "Title bar missing (not beryl!)"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by enduser on 2007-07-24
Running newest Ubuntu fiestyfawn on  IMB t30 thinkpad.  512 ram?

1) in firefox maximizing windows causes missing titlebars. I don't run beryl or compiz so i don't think the "similar topic" solutions apply to this. It becomes difficult to resize windows quickly.   Cant move window.

2) Cube effect quit after update.

3) fierfox starts up really slow. i often get an error message saying another instance is already running and to close it down, but this is just from too many clicks. (the natural result of not knowing whether or not all the clicks registered + variable system response times)

---

### Post by Mornedhel on 2007-07-24
Then...> **enduser said:**
> I don't run beryl or compiz so i don't think the "similar topic" solutions apply to this. You do... not ? Then... > **enduser said:**
>  2) Cube effect quit after update. ... where does the cube come from ?...

---

### Post by por100pre1 on 2007-07-24
Try turning off Desktop Effects.

Click the Firefox icon once and wait. If another instance is running use this in a terminal:

```
pkill firefox
```

---

### Post by enduser on 2007-07-24
cube workspace was preinstalled with unbuntu version i got. After it stopped working i disabled desktop effects. *note this is not that fancy 3d cube effect in beryl but just the default desktop effect.

---

### Post by Mornedhel on 2007-07-24
> **enduser said:**
> *note this is not that fancy 3d cube effect in beryl but just the default desktop effect.

I know that, but if you had it enabled, it's likely to cause the same problems as Compiz would. Now, seeing as you disabled it anyway, I'm guessing there has been at least a reboot since that, so, it doesn't seem to be the source of the problem.

---

### Post by gubemton on 2007-12-03
I had a "missing" title bar problem: it seemed as if the titlebar of my browser had somehow disappeared, or had "slipped under" the Ubuntu menu bar, which sometimes happens. I moved the menubar, but the browser titlebar wasn't revealed. I changed the display settings of my monitor in case the titlebar had somehow slipped of the edge of the display, but that didn't fix it either. 

Here's a solution that worked for me: look under system/preferences/windows to check which movement key is enabled (CTRL, ALT, or Windows), then click anywhere in the window with the missing titlebar and ALT-drag (CTRL-drag, or whatever key you have set  for movement) and the title bar will magically appear!,

---

