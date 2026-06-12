---
title: "Volume Control Graphic"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by satjat on 2008-02-08
I just changed the monitor on my PC/Feisty and it "lost" the graphics card. Recognized it as legacy vesa or sth.
When I reenabled the correct drivers (nvidia) the image quality is degraded and some eye candies are lost. Most obvious is the volume control graphic that pops when changing volume from keyboard. It reverted back to the old bar.

The weird thing is that it only happened on one account. On another, the volume graphic is compiz's big square one and image quality is not degraded.

Most compiz effects work in the problematic account so it is certain that compiz is enabled.

Any ideas?

---

### Post by TeaSwigger on 2008-02-08
Nope! Worse, I don't use Compiz, as my hardware is too ah, venerable. But wanting to help anyway... I can offer a generic suggestion; if I read your meaning right, you note these issues only appear in one account while everything is working ok again in others, so the errors would presumably be in configuration files in the home folder of the user with the problem. Hidden files. Does Compiz Fusion have a hidden config. folder for instance? You could log in with Compiz disabled, delete related config files (as always, make a backup so if anything is wrong, just put 'em back), log back in and enable Compiz. This would presumably create new config files which wouldn't be affected by whatever went wrong after the monitor change. This is only a vague suggestion, so please be cautious if you investigate it. Luck :)

---

