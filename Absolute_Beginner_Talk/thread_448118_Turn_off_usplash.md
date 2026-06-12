---
title: "Turn off usplash"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by whayong on 2007-05-18
Hello there!  I've been having slow boot times with a Feisty install.  I installed bootchart, but don't know how to post it as a thumbnail, lol!  Anyway, if I'm reading it correctly, it seems that usplash is what's keeping me from booting up quickly.  Is there a way to turn this off?  I've been trying a few things but can't seem to figure it out.  Thanks guys.

---

### Post by yabbadabbadont on 2007-05-18
Using sudo, edit /boot/grub/menu.lst and remove the word, "splash" from the line that starts with
```
# defoptions=
```
Then run, "sudo update-grub".  (no quotes of course)  The next time you reboot, usplash should not be displayed.  You may also want to remove the usplash package using synaptic.

---

### Post by whayong on 2007-05-18
Wow!  Thanks for the quick reply.  I will try it now and hopefully my laptop boots just as fast as your reply!

---

### Post by whayong on 2007-05-18
Whooohooooo!  I shaved 10s from my boot time.  I'm now down to 54s.  Anyone happen to know what "readhead" is on the boot chart?

---

### Post by yabbadabbadont on 2007-05-18
It basically "cat's" all the binaries needed for startup to /dev/null so that they are all in the file cache and will start faster.  I never cared for it myself, but I can see where it could help some people.

---

