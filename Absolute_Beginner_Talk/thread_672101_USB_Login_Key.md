---
title: "USB Login Key"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Jinx-Wolf on 2008-01-19
I know this was posted somewhere else, but I got no help there.

I'm using pamusb

I managed to get it to authenticate my sudo password, however, removing it does not lock the computer.

When I disable one_time_pad, it makes me enter my password when I login or launch a program, which beats the purpose of even having the USB key.

When formating to a unmountable format, it no longer recognizes the USB drive, because it needs the UUID.

after messing around for a couple hours, I've managed to make it not work at all.

I purged then reinstalled fresh, reconfiguring everything. Now it works fine, but still won't lock.

Well, now it doesn't work again. All I did was add the commands to lock, and changed the device name in both the device's field, and my user's field. Now I get:

```

* Authentication request for user "wolf" (pamusb-check)
* Device "LEXAR" is connected (good).
* Performing one time pad verification...
* Pad checking failed !
* Access denied.

```

Even after changing everything back to the way it was before, I still get the same message. :confused:

---

### Post by Jinx-Wolf on 2008-01-19
Bump

---

### Post by Jinx-Wolf on 2008-01-19
No suggestions?

---

