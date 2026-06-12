---
title: "Master Boot Record"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by Abu Imak on 2006-07-20
Hi, My laptop dual boots winXP and Ubuntu, I liked Ubuntu so i want to put it on my home computer, however, I want to completly remove it from my laptop because my university uses soley windows products, If I reformat my laptop with my windowsXP cd, will it overwrite my MBR? I ask just to make sure that i won't completly screw up my laptop when it tries using Grub when Ubuntu is no longer there, thank you

---

### Post by wahman143 on 2006-07-20
Yes - the windows install cd will overwrite your MBR.

HTH,
W.

---

### Post by ajgreeny on 2006-07-20
You don't need to reformat the windows partition when you remove the ubuntu partition.  Boot into the windows CD and chose the recover option (I think that's what it is).  When you get to the point of asking which windows you want (you will probably only have one) accept that and then do *fixmbr,* which will put your original mbr back as if nothing had changed.  There will be some warning messages about only doing this as a last resort as it can make your windows unbootable, but ignore that as it wil be completely unbootrable if you do nothing anyway, and I've done it many times with no problems.

---

### Post by Abu Imak on 2006-07-20
Thank both of you for your replies

---

