---
title: "ERROR 17 (tried to reinstall ubuntu)"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by bubi1980 on 2006-09-23
hi all,

Nothing works, cant start windows Xp and reinstallation of ubuntu freezes. When i try to boot from hard disk (try to start up windows xp) i get an error message.

here is what i did:
I have (a dualboot system (ubuntu windows xp) on the same hard disk.
I tried to reinstall ubuntu, I run the LiveCD and boot from the cd.
Ubuntu was starting up, then I used GParted, I deleted and reformated the /root and /home partitions to ext3. After this I clicked  "install" ubuntu. It works fine until "prepare partitions" window. (I selected manual edit partitions) The "prepare partitions" is running (loading)and freezes, cursor doesnt move, cant do anything...

And then the worst thing is I cant even boot WIndows XP anymore, when the pc is starting up i get the following message:

"Booting from local disk...
GRUB loading stage 1.5

GRUB loading, please wait...
ERROR 17"

thats it, i think i messed up everything...
please help me out

---

### Post by xyz on 2006-09-23
There's pretty much the exact same thread started a few lines down from yours on the Absolute Beginner Page!!!!!

---

### Post by bubi1980 on 2006-09-23
yep,

I thought here i can get help quicker,
is it a problem to post a thread twice in different forums?

---

### Post by xyz on 2006-09-23
I think moderators don't really like doubles!

---

### Post by xyz on 2006-09-23
How about booting on your XP CD and , at the prompt, type "fixmbr" 
but in case Ubuntu is still there, the fix will be different.
If I understood you right, you've got nothing working at all!

---

### Post by bubi1980 on 2006-09-23
i gona try that one, but should i start XP in recovery mode and then type fixmbr?

---

### Post by xyz on 2006-09-23
I think you boot on it and go to the rescue console.

---

