---
title: "GRUB error 22"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by bobby3333333333 on 2007-04-14
i try to boot my machine and i get a GRUB error 22... help plz

---

### Post by N Clement on 2007-04-14
What different OS's did you have before you got this error?

Were you doing something like formatting your hard drive?

[don't worry, I had this very same problem 2 days ago and got it fixed pretty easily]

---

### Post by bobby3333333333 on 2007-04-14
bump

---

### Post by bobby3333333333 on 2007-04-14
i had window and ubuntu on the same harddrive and i was trying to remove ubuntu to put it on a second one

---

### Post by N Clement on 2007-04-14
Ok,  you are in exactly the same boat that I was 2 days ago, but I had just deleted Suse.

Bottom line:

-Grub is hosed
-Windows is not

How to fix it:

1)  Get ahold of a windows xp install CD and start it up (make sure BIOS will start from CD before harddrive)

2)  Go to the Windows Recovery console (the option to get into the console is R)

3)  Type 'fixmbr' and say yes when it tells you that it is dangerous, you may want to read that message anyway

4)  Restart without the XP CD in your drive and it should just boot straight to windows.

5)  Post if that doesn't work

---

### Post by r4ik on 2007-04-14
Try,

[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console)

Good luck !

---

### Post by bobby3333333333 on 2007-04-14
ah! thank you! it worked

---

