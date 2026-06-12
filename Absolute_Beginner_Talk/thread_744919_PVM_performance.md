---
title: "PVM performance?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Rylin on 2008-04-04
I recently installed win xp on the parallel virtual machine software I have on Ubuntu, but it doesn't seem very practical to me. It sounds very popular, but how do you get it to run smooth? I gave the virtual xp system 1gig of ram to work with but its still sluggish when moving windows around. VM also won't allow the installation of nvidia drivers either, which I thought would fix the sluggish performance. 

My main reason for getting xp up on PVM is to use adobe products while still sticking with Ubuntu.

Any help would be appreciated. :)

---

### Post by 3rdalbum on 2008-04-04
Slow window-moving is a classic symptom of unaccelerated video. Since Windows won't have direct access to the graphics card, you can't add graphics drivers.

However, I believe there's a product from VMWare which allows the use of a graphics card from within your guest OS.

Adobe products will all work without accelerated video, fortunately.

---

