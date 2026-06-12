---
title: "pointer freezes when typing (and i want it not to)"
date: 2007-07-18
forum: Apple Intel Users
---

### Post by ryan86corolla on 2007-07-18
whenever i hold down a key on my keyboard, the pointer freezes on screen. i can move the mouse but the changes are only visible on screen when i release the key. how can i get simultaneous input from both the usb keyboard and my usb mouse?

i am on a first gen black macbook. i have this problem only with my usb mouse, whether i am holding down a key on the built in macbook keyboard or my external usb keyboard. the trackpad does not have this problem. i've tried every possible combination of plugging the mouse and keyboard into different usb ports, with no change. i did not have this problem on os x or windows running on this computer. i tried changing the keyboard settings to not repeat the key if held down, but that setting doesn't seem to affect the mouse; the pointer still freezes whenever a key is held down.

thanks in advance, and if i can give any more information please let me know.

the main thing i would like this for is for gaming - i can't move with wasd and aim with the mouse at the same time, making games like tremulous impossible to play. :(

---

### Post by ryan86corolla on 2007-07-18
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/113344](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/113344)

there it is. fixed it by killing mouseemu, and all my buttons (and middle/right click trackpad settings) still work.

---

