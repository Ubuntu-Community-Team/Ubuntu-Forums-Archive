---
title: "Fesity - no window borders and no sound after updates"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by General_Ts0 on 2007-04-17
AFter applying 150 some odd updates, now all apps launch w/ no window border and are 'stuck' in upper left corner of the desktop.  Also sound is broke.  So on my 1680x1050 res desktop, I can't make firefox any bigger than probably 640x480 'stuck' in left corner.  No window borders (no minimize or X close buttons.  Apps don't show in bottom 'task bar' and sound is broken.  OMG, WTF can I do to fix this ?

---

### Post by dbbolton on 2007-04-17
press Alt + F2, and type 

```
metacity --replace
```

---

### Post by General_Ts0 on 2007-04-18
damn, and voila. it's fixed.  Thx !!

Alt+F2 does nothing btw.  But ran from terminal.

---

### Post by dbbolton on 2007-04-20
oh, i guess they changed the keyboard shortcut for the run prompt.

---

### Post by AtrejuT on 2007-04-20
> **dbbolton said:**
> oh, i guess they changed the keyboard shortcut for the run prompt.

no they didn't -  at least it still works for me...
I think Beryl, or Compiz catch the keycombo and don't pass them on when they're broken. Or something to do with focus or so... ??

---

### Post by General_Ts0 on 2007-04-20
sh!t, I was in Windows XP when I read this post (since my window borders in Ubuntu were all screwed up) so Alt+F2 does nothing, heh.  yes it still works.

thx again.

---

### Post by guice on 2007-04-21
Any updates to the sounds issue? I did a fresh install of Fesity and now i have no sound. It seems sound is a common problem; the forums are littered with posts about that.

Before the fresh install, all sound worked. After, only my USB (which is tied to my stereo) works. Fesity sees my Audigy card, but no sound comes through the speakers.

---

### Post by AtrejuT on 2007-04-23
well I reinstalled the alsa drivers manually, that helped and wasn't really a lot of work, but I don't know if that's an option for you

---

