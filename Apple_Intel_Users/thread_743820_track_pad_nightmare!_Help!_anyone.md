---
title: "track pad nightmare! Help! anyone?"
date: 2008-04-03
forum: Apple Intel Users
---

### Post by hackersmovie on 2008-04-03
So, I've read and read, and tried and tried with no luck. I tried this thread
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa) and many, many more. Nothing has worked. I edited the xorg.config file, enabled SHMConfig, installed gsynaptics track pad GUI interface, etc, etc, etc, NOTHING IS WORKING. The track pad, kinda works but is very, very buggy/quirky. It doesn't scroll smoothly at all and forget about tapping of any kind, it just makes the cursor jump around like crazy. When I just try 

```
synclient -m l
```

I get this:

```
Can't access shared memory area. SHMConfig disabled?
```
Now, I've set, reset, and reset again, the 

```
option        "SHMConfig"     "on"
```

in the xorg.config file, many many times. I've tried "on", "true", "TRUE", "ON" nothing seems to work. I installed a patched kernel per a wiki "how to" for getting the trackpad working, etc, etc, Most likely if it's out there I've tried it.

Can anyone point me in the right or even a better direction? 

Thanks in advance, and sorry for posting another similar thread. . .

---

### Post by Viro on 2008-04-04
When you have set your SHMConfig flag, did you restart your machine (or the X-server at least)? The config files are only read each time the X-server starts up.

---

### Post by hackersmovie on 2008-04-04
> **Viro said:**
> When you have set your SHMConfig flag, did you restart your machine (or the X-server at least)? The config files are only read each time the X-server starts up.
Yes, crtl, alt, del out, and complete shut downs. . . .

---

