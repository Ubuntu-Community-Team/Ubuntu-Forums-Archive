---
title: "freeze on screensaver"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by notquitehere188 on 2005-12-29
i just installed ubuntu, and, impressed as i was with my ability to follow a step by step guide without destroying my computer i went to get some congradulatory food, however when i got back it was frozen on a screensaver, when i searched the forums it said it was something to do with the 3dness of the screensaver, the suggestion to fix it was something along the lines of apt-get *random letters* what does this mean or can someone tell me another way to fix it

---

### Post by Mustard on 2005-12-29
I think you would have to elaborate a bit more on what random letters is.  I doubt they are random at all, but performing a specific function.

What type of computer is this?  Is it a laptop?

The problem could be that your system is not handing the opengl screensavers which really need to use hardware acceleration on your graphics card.  Not all the screensavers use opengl, so you could fix this by choosing one standard screen saver that doesnt use opengl or by using blanking rather than a screensaver.  This would be a temporary fix until such a time as you were able to deal with the hardware acceleration problem.

 Or if you are using a laptop, it could be a problem with the laptop going into suspend during the screensaver.  Which would be a totally different problem with a different solution.

---

### Post by notquitehere188 on 2005-12-29
it turns out it was for an ati driver, so i went around putting it in search boxes until i found it and installed it.  however, now when i run 3d games (which also froze as i later found out) instead of freezing, they run incredibly slow.  i have a radeon 9200 if that matters

---

