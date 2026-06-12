---
title: "split -b file archive"
date: 2005-10-25
forum: Absolute Beginner Talk
---

### Post by hiptrop on 2005-10-25
hello and thank you for reading ! 

i got a small problem ... i use ubuntu linux and windows .. ( mostly windows )

well .. my windows partiton crashed .. (  ) and i did a backup with linux using the split -b command ... 

well now i got all the files .. and i don´t know how to join these archive files under windows  

file have no extension ( aa, ab , ac ... ) and so on .. 

with winrar i can only unpack the first one ( aa for example ) but then gives me an error .. so what i have to do is join the files somehow .. i know that it is possible somehow  with a windows command ! 

i hope you understand my problem cause my english is not the best ! 

thanks for any help !

---

### Post by asimon on 2005-10-25
My DOS knowledge is very rusty, but something like
```
C:\> copy /b file1 + file2 + file3 + ... + fileN newfile
```
under a dos shell in windows should work.

There is also a Windows freeware program (with GUI) called HJSplit which can join files, but AFAIR it wants the splitted files with extensions .000 .001 .002 etc.

---

### Post by hiptrop on 2005-10-25
thanks alot ! your solution works partly :) 

i can join the files ! but i cannot unpack them ! winrar ( or should i use another one ? ) 

it only unpacks the first archive file that i joined !

---

### Post by asimon on 2005-10-25
How did you made the backup, surely not with split alone. Did you made a big tar archive and split that into multiple files?

If winrar only unpacks the first part of the joined file than I would say that the joining somehow didn't worked correctly.

Anyone an idea?

---

