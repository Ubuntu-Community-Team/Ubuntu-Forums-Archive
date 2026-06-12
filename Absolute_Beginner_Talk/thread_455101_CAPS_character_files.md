---
title: "CAPS character files"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ASPCartman on 2007-05-26
How to make linux to understand that i don't want to have two idienteffic files in one folder (sorry for my English ;) )
For exemple: I have 'Steam' dirrictory with 'steam.exe' file. And in another dir i have 'STEAM.exe' file. If i copy 'STEAM.exe' into 'steam' dir then in 'steam' dir will be 2 files: 'steam.exe' and 'STEAM.exe'. WTF!?
I need for exemple to rewrite 'steam.exe' by 'STEAM.exe'. Then i must to do many operation to do what i want. It's just stupid. Why it cannot understand that steam.exe = STEAM.exe and it must ask what to do with all these while copy'ing.

Sory again for my English )

---

### Post by cymen on 2007-05-26
That's just how Linux works I'm afraid. It's case sensitive. Capital letters matter. STEAM.exe and steam.exe might be exactly the same file in content, but the names are different and so Linux will treat them differently. The files aren't identical if they have different names! I see it as an advantage rather than a disadvantage.

If you want steam.exe to be overwritten or replaced by STEAM.exe, then it isn't very hard just to rename STEAM.exe to steam.exe and then copy it. You'll be asked if you want to overwrite the original file.

I'd advise you to get into the practice of using lowercase letters in naming files to avoid difficulties in the future. Whatever you choose to do, do it consistently. If renaming things one by one gets too tedious, then somebody might be able to make you a script to, for example, automatically rename everything in a directory to lower case.

Sorry if I misunderstood anything.

---

### Post by ASPCartman on 2007-05-26
Thanks. Alll is right :) Thanks again

---

