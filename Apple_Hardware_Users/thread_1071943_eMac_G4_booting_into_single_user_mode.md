---
title: "eMac G4 booting into single user mode"
date: 2009-02-16
forum: Apple Hardware Users
---

### Post by kerryhall on 2009-02-16
I have tried "Linux 1" with no success. I have tried "Linux init=/bin/sh", and that works, but it mounts my filesystem as read only, I need to fix /etc/sudoers. I have also tried booting up with live CD, no success. I have tried booting up with the text mode installer, I can get to BusyBox, but then mounting my hard drive fails (no such device)

Suggestions?

---

### Post by kerryhall on 2009-02-16
Ok, for some reason "Linux single" works, but "Linux 1" does not.

I can get to the recovery menu, but the arrow keys do not let me select an option. How do I navigate this menu?

---

### Post by kerryhall on 2009-02-18
Bump.

---

### Post by tiresia on 2009-02-18
Is it a fresh install? Have you tried the Ubuntu Hardy LiveCD? You say no success? What does it mean?

---

### Post by kerryhall on 2009-02-18
The liveCD just gives me a black screen.

There has to be some way to navigate the recovery menu. Why don't the arrow keys work? That seems like a pretty serious bug.

---

### Post by tiresia on 2009-02-18
Please, you should give us more infos about your hardware (ram?) and what you are trying to do. Is that a fresh install? Did you download the right Cd for PPC? 
When you try to boot the Live CD, what happens? Do you try to give there video=ofonly?

---

### Post by kerryhall on 2009-02-18
I have already installed UbuntuPPC with the text mode installer. I accidentally removed myself from the admin group (whoops!) I thought the Ubuntu installer put the first user into sudoers, I didn't realize that it relied on a group for sudo.

Anyway, all I am trying to do is boot into single user mode.

I can do this by doing "Linux single" at the yaboot prompt, but when I get to the recovery menu, it cannot be navigated. The arrow keys simply do not work. This seems to me to be a serious bug.

---

### Post by kerryhall on 2009-02-23
Bump.

---

### Post by tiresia on 2009-02-23
Sorry, I forgot to answer... I'm not sure, that it is a bug. At least, I haven't heard anything about it. Maybe you can't work in single user mode.
Anyway the easiest solution is to start from the LiveCD, giving at the yaboot prompt video=ofonly
Have you already tried it?

---

### Post by kerryhall on 2009-03-04
Thanks, using the live CD with those commands worked!

However, that bug with the recovery menu seems liek a serious problem.

---

