---
title: "Shift + Backspaces crashes session (xgl)"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2006-09-27
When I press Shift + Backspace, my session shuts down,
I know this is actually a function, but i dont want it. :D

How do I get rid of this?

---

### Post by Dinerty on 2006-09-27
```
xmodmap -e \"keycode 22 = BackSpace Delete\"
```

Add that line to:

System > Preferences > Sessions > Startup Programs

---

### Post by alex-desktop79 on 2006-09-27
wont that delete just backspace? thus not letting me erase text?

---

### Post by Dinerty on 2006-09-27
> **alex-desktop79 said:**
> wont that delete just backspace? thus not letting me erase text?

it will be fine mate, it's a bug in xgl/compiz, everything will work fine I use it myself.

You will still be able to erase with backspace

---

### Post by smartalecks on 2006-09-27
Try it in Terminal first (Applications>Acessories>Terminal). I'm pretty sure it won't "delete your backspace key". :)

---

