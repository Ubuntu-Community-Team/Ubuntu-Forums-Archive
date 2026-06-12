---
title: "Mac alu keyboard layout"
date: 2011-11-20
forum: Apple Hardware Users
---

### Post by Dr. McKay on 2011-11-20
Is there a way to get Ubuntu to recognize the complete layout of my mac alu keyboard (wired) ?
As I live in Belgium, I have an AZERTY-layout. The '@' is located at the top left, right beneath the escape key. Took me five minutes to find out how to type it (in my case it's ALT-£) so it's a bit of a pain.

Does anyone know how to do it ?

---

### Post by pauljwells on 2011-11-20
You need to start with the closest layout you can find to your own keyboard (probably a basic PC Belgian layout) then use xmodmap to modify the keys you need.

This is my own for a UK mac keyboard

```
keycode 94=grave asciitilde grave asciitilde dead_grave dead_horn
keycode 49=section plusminus section plusminus section plusminus
```

save this as .Xmodmap (note upper case X) in your home directory, then log out and back in.

You will need to google the correct keys for your layout but this is the right way to start.

---

### Post by Dr. McKay on 2011-11-20
Ok thx, I'll give that a try...

---

