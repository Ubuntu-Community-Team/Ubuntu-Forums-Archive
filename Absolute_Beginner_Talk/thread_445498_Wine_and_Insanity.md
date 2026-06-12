---
title: "Wine and Insanity"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-05-16
I have spent hours trying to get Wine to do anything with no joy. It sees C: but all the folders are empty. Went back to XP and made sure that "Show Hidden Folders" was selected. Still nada. Than I noticed that Wine sees C: as NTFS not Fat32. Do I have to change my file system in order for this to work?

Also, after many fruitless searches, I have been unable to find a decent tutorial for Wine. Does one exist? Mighty helpful if so.

BTW: I have opened Wine using winefile and winecfg, same results; Zilch.

Thanks for any help,

Jon

---

### Post by Gmbrdilos on 2007-05-16
wine is not running your part of windows
it acts as windows
think of it as an emulator (yes I know its called something else, but you get the idea)

---

### Post by Romin-1 on 2007-05-16
Thanks for the reply but it didn't really address my questions.

Jon

---

### Post by MoxJet on 2007-05-16
You're not supposed to have wine running on an installed windows version. Instead, it uses an own "installation", located on a folder on your linux partition. It is practically empty when installed. 

If you have a program you want to install in wine, locate it using the terminal and then type
```
wine setup_aom.exe
```
Or whatever the file may be called.

If you want to try to use an installed windows version (I have not done this and I'd not recommend it), you can probably find the folder wine mounts as C: under winecfg.

Tutorials should be everywhere.

---

