---
title: "strange shut down issue..."
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Andeh on 2008-03-12
Sorry to post yet ANOTHER shut down problem, only i couldn't find anything on the forums similar to the problem I'm having.

i noticed it last night when i shut down my machine, none of the connected USB devices turned off. i wouldn't worry about it because when i turn the machine back on they restart and every thing's fine. The problem is is that my keyboards backlit, and sits in the corner of my bedroom...VERY VERY annoying. Also i've got my Bios to boot up the machine at a specific time, and I've noticed that since installing linux it no longer does this.

any idea's?

thanks guys

Andy

---

### Post by handydan918 on 2008-03-12
> **Andeh said:**
> Sorry to post yet ANOTHER shut down problem, only i couldn't find anything on the forums similar to the problem I'm having.

i noticed it last night when i shut down my machine, none of the connected USB devices turned off. i wouldn't worry about it because when i turn the machine back on they restart and every thing's fine. The problem is is that my keyboards backlit, and sits in the corner of my bedroom...VERY VERY annoying. Also i've got my Bios to boot up the machine at a specific time, and I've noticed that since installing linux it no longer does this.

any idea's?

thanks guys

Andy
This issue cropped up in the mepislovers forums awhile ago, and the expert opinion was that it isn't really a bug. It just doesn't do things the way Windows does (thank God!) I think the suggestion was made to poke around in the BIOS and see if you can do something there, but there wasn't a real fix. I suspect one could write a script to be run at shutdown time that would power down the usb ports, but with the state of HAL and udev, it seems risky.

---

### Post by Andeh on 2008-03-12
that's a shame :/ i'll have a look into my bios settings at some point this evening

thanks for your help

---

### Post by cometa2k7 on 2008-03-16
I had similar things happening with my old computer.

Also, my PS/2 ports, those for the mouse and keyboard, remained wih a power output. I think that it might have just been my computer, because every operating system I've tried did the same.

---

