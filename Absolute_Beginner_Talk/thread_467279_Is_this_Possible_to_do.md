---
title: "Is this Possible to do?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-06-07
I would like to know if I can have Ubuntu 7.04 on one HD and Windows on another within the same machine.

If this is possible how do you launch them at startup? Can they run together at same time?

---

### Post by zach12 on 2007-06-07
yes it is i think

---

### Post by Rocket2DMn on 2007-06-07
You certainly can!  The boot manager (GRUB) will have to be configured to recognize the XP partition along with the Ubuntu one.  However, you can only boot one OS at a time.
I'm not sure on the configuration for GRUB, but hopefully this helped and somebody else can get you the other details.

---

### Post by Seisen on 2007-06-07
Here is a link that should help you out.

[http://ubuntuforums.org/showthread.php?t=179902]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by w4ett on 2007-06-07
> **lentomies said:**
> I would like to know if I can have Ubuntu 7.04 on one HD and Windows on another within the same machine.

If this is possible how do you launch them at startup? Can they run together at same time?

This is exactly how my machine is set up.  The Feisty Live CD will install the OS this way for you.  Make sure you select your second drive for Ubuntu and your master drive for the Grub loader.

---

### Post by RelativelyQuantum on 2007-06-07
Dual booting - or even triple booting - is quite common, and easy to set up from live CD, as mentioned earlier. I currently have three operating systems on my machine; Ubuntu, openSUSE, and Windows XP.

---

