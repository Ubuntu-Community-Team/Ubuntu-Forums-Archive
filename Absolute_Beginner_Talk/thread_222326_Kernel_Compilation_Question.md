---
title: "Kernel Compilation Question"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by herrdoktor330 on 2006-07-24
Hello again all,

I compiled the new 2.6.17.6 kernel for my system with my prefered options and it's running nicely. However, I have a question in regards to the Ubuntu Startup Loading Screen. After I compile a new kernel, I lose the Startup and Shutdown screens. How can I compile with those options back on and working like they should?

I'm sure this is just a beginner level question.

---

### Post by MrSmith on 2006-07-24
To get usplash you need to make sure you enable this in the config:

Graphics support:
-VGA 16-color graphics support - module (m)
-VESA VGA graphics support - build in kernel (y)

Console display driver support:
-VGA text console and Video mode selection support- build in kernel (y)
-MDA text console-module (m)
-Framebuffer Console and Framebuffer Console Rotation support-build in kernel (y)

Doing this will get the usplash screens back. However when I tried it the screens were in a strange high resolution and could not be changed. You might tinker with these settings and see if you can make the screens appear normally.

Hope this helps
MrSmith

---

### Post by herrdoktor330 on 2006-07-24
> **MrSmith said:**
> To get usplash you need to make sure you enable this in the config:

Graphics support:
-VGA 16-color graphics support - module (m)
-VESA VGA graphics support - build in kernel (y)

Console display driver support:
-VGA text console and Video mode selection support- build in kernel (y)
-MDA text console-module (m)
-Framebuffer Console and Framebuffer Console Rotation support-build in kernel (y)

Doing this will get the usplash screens back. However when I tried it the screens were in a strange high resolution and could not be changed. You might tinker with these settings and see if you can make the screens appear normally.

Hope this helps
MrSmith

This would be in the <kernel compile name>.config file? or would this be when I build the makefile for the kernel? I'm not at my computer to tinker, but I'll poke around as soon as I do. I'm having a couple newb issues I need to look into.

---

### Post by MrSmith on 2006-07-25
These instructions would be placed in the config file. If you are successful please let me know. I am curious how to not have the usplash screen appear in such high resoulution.

MrSmith

---

