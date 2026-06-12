---
title: "Kernel Panic"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by marshall700 on 2008-03-02
I get this error 
"Kernel panic - not syncing: No init found. Try passinginit= option to kernel."

I cant get into ubuntu i cant type anything it just stops on the black screen....

---

### Post by Cypher on 2008-03-03
If you're booting from the HD, looks like Linux can't find your HD and in turn can't find the /sbin/init program to run..At the GRUB menu, [E]dit the default ubuntu entry and remove the "quiet splash" from the line, then exit and allow it to boot up. You should see a lot of text now, try to see if you see any errors..

---

### Post by marshall700 on 2008-03-04
Ok ive just done that it says:

"failed to execute /init" as you said 
So what should i try the laptop isnt accepting any other disks now not the windows one either so ive kinda got to get it working.....

---

### Post by Cypher on 2008-03-04
Do you still have the LiveCD that you used to install Ubuntu? If so, pop that in and boot into it, that will allow us to get a terminal to type some commands and check out what's going on..

---

### Post by marshall700 on 2008-03-04
Well my dvd rom isnt booting to Cd its all set up in the BIOS but it just ignores every disk except Vista ultimate so im installing vista atm so then i can use the.exe i was told to use b4 to install it!

---

