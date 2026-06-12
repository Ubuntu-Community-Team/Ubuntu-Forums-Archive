---
title: "Accessing files on a seperate kernal."
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-10-03
So my computer broke a few months ago - I tried to fix it for days but eventually gave up..in the process I broke my main kernal installation by trying to install a graphics driver. Today I decided to start it up again and its working perfectly. Problem is that all my bookmarks,etc are stored on my other kernal installation - is there anyway I can access them?

---

### Post by molly_001 on 2007-10-03
I suppose you have already considered this, but are you using GRUB as your boot manager?  And if so, do you still have the boot lines for the other kernel versions in your /boot/grub/menu.lst text file?

I generally remark out (using # at beginning of line) the boot line for any older kernels in that file.  But then I have them for later in case they are needed.

---

### Post by jordanmthomas on 2007-10-03
Just boot whichever kernel works.  Your bookmarks should be there still.  The kernel is only one part of the whole system and your bookmarks are not related to it in the least.

...or am I missing something here?

---

### Post by llamakc on 2007-10-03
Yeah it sounds like the OP reinstalled Ubuntu again, and used separate partitions for the second install.

If that's the case you can easily mount the old partition and get what you want off of it. Confirm what is going on and we can show you how to get your stuff.

---

### Post by auraithx on 2007-10-03
Nope - I just used updated the kernal through the update wizard whenever it asked me to

I have 4 kernal builds or so that no longer work and then it said "Older Kernals" and the ones underneath werent affected.

tell me how to mount the seperate partition though and I'll give that a bash incase I somehow have managed to reinstall Ubuntu - even though I've only went through the installation processes once.

---

### Post by auraithx on 2007-10-08
bump

I now see that it actually says "Other Operating Systems"

So I've corrupted Fiesty and am currently running (my old copy of) Edgy.

---

