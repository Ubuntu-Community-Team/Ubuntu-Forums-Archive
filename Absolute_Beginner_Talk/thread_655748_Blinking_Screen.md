---
title: "Blinking Screen"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by skaldicpoet9 on 2008-01-01
I just enabled the drivers for my ATI Radeon 200M graphics card. But I have a slight problem. Whenever I play any games the screen keeps blinking. I can play the game just fine, however when I am playing the screen keeps blinking, it is not blinking so bad that I cannot see the game it is just doing it to where it constantly keeps making the screen blink. Is there a way to fix this?

---

### Post by skaldicpoet9 on 2008-01-01
Is there any way to fix this?

---

### Post by JoshuaRL on 2008-01-01
What driver are you using?  "fglrx" (the proprietary one from ATI) or "ati"/"radeon" (open-source workaround from DRI?)  If "fglrx", try this:

```

aticonfig

```

If you are using "ati" or "radeon" try this:

```

driconfig

```

Something else you might try is searching the forum for your exact video card and computer type (if you didn't piecemeal yours together) and see if anyone has any tweaks that help.

And you could always try setting the framerate down some in whatever game menu you're in.

---

### Post by skaldicpoet9 on 2008-01-01
It isn't "blinking" a lot. It just looks like it is constantly refreshing the screen. It is slightly annoying.

---

### Post by skaldicpoet9 on 2008-01-01
> **JoshuaRL said:**
> What driver are you using?  "fglrx" (the proprietary one from ATI) or "ati"/"radeon" (open-source workaround from DRI?)  If "fglrx", try this:

```

aticonfig

```

If you are using "ati" or "radeon" try this:

```

driconfig

```

Something else you might try is searching the forum for your exact video card and computer type (if you didn't piecemeal yours together) and see if anyone has any tweaks that help.

And you could always try setting the framerate down some in whatever game menu you're in.


Well, I installed the ATI driver through Envy. I would assume that it is the regular ATI propietary driver...

---

### Post by JoshuaRL on 2008-01-01
Cool.  Try aticonfig, it may be able to get it configured a little better for you.  That and looking for tweaks here could fix it.

---

