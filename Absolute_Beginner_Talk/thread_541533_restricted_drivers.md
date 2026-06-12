---
title: "restricted drivers"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by wsx123 on 2007-09-02
I was trying to install compiz-fusion. I can't get into restricted driver manager. I get a window that states "your hardware does not need any restricted drivers" after I enter my admin password.

---

### Post by jordanmthomas on 2007-09-02
What kind of graphics card do you have?  It's possible you don't need restricted drivers.

---

### Post by wsx123 on 2007-09-02
ATI Radeon Mobility M6 LY, compiz fusion installed, I can get into the settings manager but nothing happens.

---

### Post by jordanmthomas on 2007-09-02
Just going the the settings manager won't start compiz.

I *think* (not an ATI guy) with ATI you're better off with the open-source drivers in terms of easiness.
What happens if you run
```
compiz --replace
```
from a terminal?

---

### Post by wsx123 on 2007-09-02
"failed test from _pixmap support"

---

### Post by asmoore82 on 2007-09-02
> **wsx123 said:**
> "failed test from _pixmap support"

the current ATI propreitary driver does not support any form of compiz.

to get compiz working with ATI and their driver, you have to use Xgl.

---

### Post by jordanmthomas on 2007-09-02
You may want to look into [envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install the restricted drivers for your card.

Note that if you do this, you'll also need to read up on how to use an XGL session instead of AIGLX.

(I'm gonna hand this thread off to someone who uses an ATi card because I wouldn't be any more help than google in helping here since that's where I'd get anything I could help you with from)

good luck

---

### Post by wsx123 on 2007-09-02
I installed XGL but it does not start up or show up as a session option when logging out.

---

