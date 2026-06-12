---
title: "mapping a key as fn - possible??"
date: 2009-01-01
forum: Apple Hardware Users
---

### Post by SaiHayashi on 2009-01-01
hi there
i would like to map the right alt key to behave as fn key.
but xev does not pick up the fn key on its own.
so does anyone know how to find out the keycode for fn key?
all i can find on google so far are about F1 keys but not fn keys by itself.

any hint is appreciated. thanks.

---

### Post by kidders on 2009-01-02
Hi there,

The fn key typically doesn't produce a keycode. Keyboards use it to emulate extra keys ... ie whether you're holding down fn determines what keycode gets sent when you push something else.

For example, when you hit fn + F10 on an Apple keyboard, your OS sees XF86AudioMute. It has no way of knowing your keyboard doesn't really have such a key, and was only emulating it.

The only way to achieve the *effect* of remapping fn would be to individually remap RAlt + F1, RAlt + F2, RAlt + F3, etc. There are two problems with doing that ...[LIST]
[*]There would be no way to map RAlt back to fn, so you would lose the use of it with your function keys.
[*]Obviously, the mapping would only work sensibly with one type of keyboard.
[/LIST]

I can't say I blame you for wanting to do this ... The fn key is in a really weird place on Apple's newer keyboards!

---

### Post by SaiHayashi on 2009-01-03
> **kidders said:**
> Hi there,

The fn key typically doesn't produce a keycode. Keyboards use it to emulate extra keys ... ie whether you're holding down fn determines what keycode gets sent when you push something else.

For example, when you hit fn + F10 on an Apple keyboard, your OS sees XF86AudioMute. It has no way of knowing your keyboard doesn't really have such a key, and was only emulating it.

The only way to achieve the *effect* of remapping fn would be to individually remap RAlt + F1, RAlt + F2, RAlt + F3, etc. There are two problems with doing that ...[LIST]
[*]There would be no way to map RAlt back to fn, so you would lose the use of it with your function keys.
[*]Obviously, the mapping would only work sensibly with one type of keyboard.
[/LIST]

I can't say I blame you for wanting to do this ... The fn key is in a really weird place on Apple's newer keyboards!
thanks for the explanations... looks like i just have get used to it

---

