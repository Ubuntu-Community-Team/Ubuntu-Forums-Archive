---
title: "Alternative to Wine for Windows emulation on PPC"
date: 2007-07-27
forum: Apple PPC Users
---

### Post by Sanchoclaus on 2007-07-27
I've been searching the PPC section of the forums, trying to find an alternative to Wine for running windows software.
Does anyone know if wine will been compatible on PPC anytime soon?
Or is there an alternative?

---

### Post by stmiller on 2007-07-27
Unfortunately any software trying to emulate x86 on PPC will be slow, just because of what it is trying to do. 

One possibility is qemu. 

$ sudo apt-get install qemu-launcher

should install a gui launcher and all of qemu.

It will let you install an x86 operating system in emulation (similar to vmware). Windows 98SE seems to work okay for me but it's slow. 

You can also just execute x86 code with qemu like this:

```

$ qemu-i386 *executable*

```

Though there are no promises on that working. (Ex. doesn't work for x86 Linux Skype)

---

### Post by Sanchoclaus on 2007-07-28
Thank you. I will try Qemu.
 You're right emulating another OS tends to be slow. But in my experience Wine (on a toshiba laptop) was a lot faster and  responsive than Virtual PC 7 on MAC

---

### Post by stmiller on 2007-07-28
That's because **W**ine** I**s **N**ot an **E**mulator. :popcorn:

---

