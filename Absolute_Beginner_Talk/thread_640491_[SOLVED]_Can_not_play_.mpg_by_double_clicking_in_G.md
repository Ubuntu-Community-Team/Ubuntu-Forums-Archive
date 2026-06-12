---
title: "[SOLVED] Can not play .mpg by double clicking in Gutsy."
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by rfurman24 on 2007-12-14
I can play them by opening either Totem or Mplayer and browsing to the files but I get an error if I double click in nautilus.

---

### Post by FuturePilot on 2007-12-14
What exactly is the error?

---

### Post by spydon on 2007-12-14
Can you right-click and open with?

---

### Post by rfurman24 on 2007-12-14
The error just says can not play such and such file. Right click open with does not work either. It works normally if I open the player and then browse to the file.

---

### Post by arist0tle on 2007-12-14
When you right click on an mpg file annd go to properties, does it have one of your programs selected in the "Open With" tab?

---

### Post by spydon on 2007-12-14
> **rfurman24 said:**
> The error just says can not play such and such file. Right click open with does not work either. It works normally if I open the player and then browse to the file.

What does it say when you try "open with" then?

---

### Post by rfurman24 on 2007-12-14
When I right click to open with it just says can not open/link/to/file/.mpg which is the same thing it says when trying to double click. Mplayer is selected as my default "open with" but I have tried changing it back to Totem. If I open Totem or Mplayer and manually open the files all is well. I have no problems in Feisty. Not that it has anything to do with this thread but Gutsy was not ready. I think it has a lot of great features/improvements but it has way to many broken things compared to Feisty. I can tell you if Gutsy had been my first Ubuntu I would have left and not come back. Feisty was the best distro I have ever used. Thank God the community is great.

---

### Post by daengbo on 2007-12-14
Can you give us the exact path? Are there any strange characters?

---

### Post by rfurman24 on 2007-12-14
The path is ~/videos/file name.mpg. No strange characters the names do have spaces. I have a second drive with Feisty installed and It works fine. With the same files.

---

### Post by rfurman24 on 2007-12-14
Rereading my post I am not sure if I was clear. When I double click on the .mpg it opens Mplayer or Totem and then says it can not play the file.

---

### Post by spydon on 2007-12-14
> **rfurman24 said:**
> Rereading my post I am not sure if I was clear. When I double click on the .mpg it opens Mplayer or Totem and then says it can not play the file.

Have you installed ubuntu restricted drivers?

---

### Post by FuturePilot on 2007-12-14
Just a wild guess, but try renaming the file so that it has no spaces in the name.

---

### Post by rfurman24 on 2007-12-14
I have the restricted drivers. Everything works in Firefox and if I manually open the files. I have not tried renaming the files but I should not have to. These same files open fine by double clicking in Feisty.

---

### Post by FuturePilot on 2007-12-14
I know you shouldn't have to but it's an easy way to find out if you may be affected by this bug.
[https://bugs.launchpad.net/bugs/164709]("https://bugs.launchpad.net/bugs/164709")

---

### Post by rfurman24 on 2007-12-14
I will try when I get home but I am very confident that is the problem. I guess I will have to try to figure out how to degrade a package. Thanks very much for sharing the find.

---

### Post by rfurman24 on 2007-12-14
Installing Mplayer rc1 solved my problem. Thanks.

---

### Post by spydon on 2007-12-15
> **rfurman24 said:**
> Installing Mplayer rc1 solved my problem. Thanks.

I still think it's very weird that it didn't work without it... :S

---

### Post by rfurman24 on 2007-12-15
I do too. I am not fond of the idea of putting rc's in a distro. I love new stuff but I love stable more.

---

