---
title: "Update manager 3 packages at a time prob"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by Ipodjohnny on 2008-04-09
I just installed a clean version of Ubuntu 8.04 beta and whenever I run update manager I can only update 3 things or less at a time. 4 or more updates at a time causes the system to just crash. Other than Update manager the system has been running stabily. I am a noob so please help me. Or better yet tell me how I can figure this stuff out on my own.

---

### Post by KCormier on 2008-04-09
It may be an issue in your version of update-manager that's been patched.  I honestly couldn't tell you.  I'd try opening up an xterm windows (alt + f2) then type "xterm" and hit enter.

then run the commands:
sudo apt-get update
sudo apt-get upgrade

this will update your package lists and then upgrade everything.  Hopefully that should patch up the update manager.  Remember, 8.04 is beta so if you want a stable product you should still be running 7.10 for the next month or two :)

---

### Post by Ipodjohnny on 2008-04-09
Thanks for the advice although it did not help. I think I will just install 7.10 tomorrow because I want some more stability.

---

