---
title: "Help, just installed Ubuntu and having desktop problems"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Dragabain on 2008-02-18
I just installed ubuntu and updated the system to the current stable of everything and now I don't have a bar above my windows that I can click on to move them...also it doesn't have the minimize, resize, close buttons.  Did I do something wrong?

---

### Post by Joeb454 on 2008-02-18
Do you have desktop effects enabled?

First check that, under System>Preferences>Appearance :)

If you don't then hit Alt+F2, and type ```
metacity --replace
```

---

### Post by Dragabain on 2008-02-18
Ok, I had the normal visual effects selected, however when I go to none or type the command you told me to the bar comes back.  How can I get normal or extra and have a bar?

Thank you for your help so far Joeb454.

---

### Post by Tyke91 on 2008-02-18
Which graphics card do you have? Have you downloaded the correct drivers for it?

---

### Post by Dragabain on 2008-02-18
I believe I did.  I have an nvidia 7400Go installed on this and downloaded the nvidia-new drivers and did the sudo nvidia-glx-config like the package said to.

---

### Post by Tyke91 on 2008-02-18
go to System>Administration>Restricted Drivers Manager and make sure the Nvidia driver's light is *green* instead of *red* (or *in use* depending on what theme you are using)

---

### Post by Dragabain on 2008-02-19
I checked and yes it is checked green and in use.

---

