---
title: "Screen goes black after selecting Ubuntu from the GRUB"
date: 2011-05-10
forum: Apple Hardware Users
---

### Post by Ecstatic23 on 2011-05-10
I finally managed to install Ubuntu on my Mac Mini which I had to use post #3 from [this thread]("http://ubuntuforums.org/showthread.php?t=1753338") to get it installed. After I select Linux from the rEFIT boot menu, it takes me to the GRUB. After selecting Ubuntu, an _ flashes on the top left corner for a few seconds then a message something like "[11.375092] [drm] mouveau 0000:05:00.0: pointer to BIT loadval table" appears for half a second, then my monitor stops receiving video signal.

I'd be very greatful for help. Need to get this mess sorted out ASAP.

Thank you.

---

### Post by Ecstatic23 on 2011-05-11
Bump...

---

### Post by DoubleClicker on 2011-05-11
See this thread [http://ubuntuforums.org/showthread.php?t=1753338](http://ubuntuforums.org/showthread.php?t=1753338)
Maybe it should be made sticky.

---

### Post by Ecstatic23 on 2011-05-11
> **DoubleClicker said:**
> See this thread [http://ubuntuforums.org/showthread.php?t=1753338](http://ubuntuforums.org/showthread.php?t=1753338)
Maybe it should be made sticky.

Fixed this by pressing 'e' at the GRUB and editing adding nomodeset in the code.

---

