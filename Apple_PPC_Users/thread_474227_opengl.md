---
title: "opengl"
date: 2007-06-14
forum: Apple PPC Users
---

### Post by Auria on 2007-06-14
for opengl, is there a way to turn of hardware acceleration, i.e. render it all on the processor?

i'm in a situation where i don't care about speed, and need high reliability. it will be as slow as it needs, i just need to get rid of the open-source ati driver bugs

thanks

---

### Post by stmiller on 2007-06-15
I *think* just commenting out 

load "dri"

will disable dri, but leave a slow/usable opengl implementation.

Might also have to leave

load "glx"

as is. That may be required for opengl. 
Anyone know?

---

### Post by Auria on 2007-06-16
> **stmiller said:**
> I *think* just commenting out 

load "dri"

will disable dri, but leave a slow/usable opengl implementation.

Might also have to leave

load "glx"

as is. That may be required for opengl. 
Anyone know?

Hi, thanks for the answer

Is it likely it could stop booting if it turns out it is not that?

I am willing to try out stuff, but i would rather not risk a crash at startup like it once happened to me after changing X config files

---

### Post by stmiller on 2007-06-16
No, this just disables the loading of DRI. For 3D. Has nothing to do with the computer booting or not. :)

---

### Post by tcrroadie on 2007-06-16
If your mac has an ATI Radeon video card, you can also add an option to disable hardware acceleration in the "Device" section of your xorg.conf.

```
Option    "NoAccel"    "true"
```

As stmiller said earlier, disabling dri should also do it for you.

---

