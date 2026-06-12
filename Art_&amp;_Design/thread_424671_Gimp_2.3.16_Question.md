---
title: "Gimp 2.3.16 Question"
date: 2007-04-26
forum: Art &amp; Design
---

### Post by episodic on 2007-04-26
Does anyone know if you can do anything about this error message.

Using the greystoration plugin (an excellent noise removal script) I get this error message.

Procedure 'gimp-progress-init' has been called with a wrong value type for argument 'gdisplay' (#2). Expected GimpDisplayID, got GimpInt32.


Anyway to deal with this?

Thanks!

---

### Post by zgornel on 2007-04-27
> **episodic said:**
> Does anyone know if you can do anything about this error message.

Using the greystoration plugin (an excellent noise removal script) I get this error message.

Procedure 'gimp-progress-init' has been called with a wrong value type for argument 'gdisplay' (#2). Expected GimpDisplayID, got GimpInt32.


Anyway to deal with this?

Thanks!
Probably, it is an older script that uses a now obsolete call gdisplay in gimp-progress-init. Gdisplay's prototype changed. You could modify the script so that instead of GimpInt32 there is GimpDisplayID. Submitting a bug to the Gimp development team will get you no nowhere, try contacting whoever made the script.

---

