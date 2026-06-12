---
title: "Cant load PitGen.dll?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by internetishere on 2008-03-01
im installing halo but i get this error right after i enter my cdkey Can't load PidGen.dll

---

### Post by PeterJS on 2008-03-01
I assume you're using wine. Odds are the dll is actually missing, that's not a standard library. Your best bet would be to salvage that dll off of a win box that has Halo installed on it

---

### Post by internetishere on 2008-03-01
i have the dll its on my halo cd i can cleary see it but it just wont load =/

---

### Post by PeterJS on 2008-03-01
You could copy it to ~/.wine/drive_c/windows/system32 and give it another go.

---

### Post by internetishere on 2008-03-01
> **PeterJS said:**
> You could copy it to ~/.wine/drive_c/windows/system32 and give it another go.

didnt work :( maybe i should just go to wal-mart and buy it again ='(

---

### Post by PeterJS on 2008-03-01
Don't waste your money on a second copy it will have the same files, and won't solve your problem of getting wine to find them. If the file is in the wine sys32 folder and it's still not finding it I don't know what to tell you.

Here's the Wine DB entry on it, hopefully there's a solution.guide somewhere in there:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2720)

---

