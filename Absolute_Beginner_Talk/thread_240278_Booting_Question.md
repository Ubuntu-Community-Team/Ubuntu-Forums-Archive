---
title: "Booting Question"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by Hillbilly Tilley on 2006-08-20
After I select ubuntu in grub, there is some text that flashes up, I think it says the kernal is loading.  There is a flash of that says something failed, this is just before the unbuntu splash screen.  How can I stop this screen so I can see what is failing?  Everything seems to be ok, I just hate to see the failing thing.

---

### Post by anaconda on 2006-08-20
In my machine there reads "Fail" in initialising RAID support.. or something similar.. I dont have RAID.. of course it fails when I dont even have one.. Maybe you have the same?

Boot time messages can be read
after booting. Write: (to terminal)

gmesg |more

But I dont really thin this is what you want.. it doesn't show the messages you want..

---

