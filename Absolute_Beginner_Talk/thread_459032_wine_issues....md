---
title: "wine issues..."
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by jordn on 2007-05-30
hey there,

i am having a few problems copying over some .DLL files from my native windows partition, into my wine system32 folder.

i cd to the wine system32 folder, and issue this command:

```
jordn@jordn-desktop:~/.wine/drive_c/windows/system32$ sudo cp '/media/hda1/WINDOWS/system32/msvcp60.dll' ~/.wine/drive_c/windows/system32$

```

the command clears, and acts as if it has worked, but when i use ' ls ' to look back into the wine directory, the files that i attempted to copy over are not there.

am i making a blatantly obvious mistake?

thanx in advance,

jordn

---

### Post by dfreer on 2007-05-30
I'm thinking you should not need the ' ' quotes or the $ sign at the end. You can add the -v switch so that cp will tell you what it does. Also, in order to put the files IN the system32 directory you should add a final slash. so...
```
sudo cp -v /media/hda1/WINDOWS/system32/msvcp60.dll ~/.wine/drive_c/windows/system32/

```

Also, use the <Tab> feature that way you don't accidently misspell something :D

---

### Post by jordn on 2007-05-30
thankyou very much dfreer, i think it was because i was missing teh / from the end. i completey forgot about the  verbose extension as well, ill be sure to use it in future!  :)

---

