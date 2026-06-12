---
title: "Problems with cp"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by iluvatar85 on 2007-06-16
Hello 
I have a problem with cp. i would like to copy a directory ~/test/ to all the subdirectory of ~/Desktop/prova/
I have read the man cp and tried a 'cp -R ~/test/ ~/Desktop/prova/*/ ' but it gave me a very strange result.
Supposing that in ~/Desktop/prova/ were the empty directory 
~/Desktop/prova/1/ 
and
~/Desktop/prova/1/ 

the result is:

~/Desktop/prova/1/ 
~/Desktop/prova/2/1/
~/Desktop/prova/2/test/


How can I correctly copy the test directory to the 1/ and 2/ directory?

P.s. sorry for my awful english... :(

---

### Post by Happy_Man on 2007-06-16
I believe you could have just dragged and dropped. For some things, (like cp), they become irrelevant when you've got a GUI. Although I think you could have done
```
cp -r ~/test/ ~/Desktop/test
``` with the same results.

---

### Post by Nekiruhs on 2007-06-16
Well, wildcards come in handy alot of times. From doing one thing many times, to sorting mp3s its useful.

---

### Post by Happy_Man on 2007-06-16
> **Nekiruhs said:**
> Well, wildcards come in handy alot of times. From doing one thing many times, to sorting mp3s its useful.
True, but OP doesn't seem to want to sort stuff; he just wants everything copied.

---

### Post by Bachstelze on 2007-06-16
> **iluvatar85 said:**
> Hello 
I have a problem with cp. i would like to copy a directory ~/test/ to all the subdirectory of ~/Desktop/prova/
I have read the man cp and tried a 'cp -R ~/test/ ~/Desktop/prova/*/ ' but it gave me a very strange result.
Supposing that in ~/Desktop/prova/ were the empty directory 
~/Desktop/prova/1/ 
and
~/Desktop/prova/1/ 

the result is:

~/Desktop/prova/1/ 
~/Desktop/prova/2/1/
~/Desktop/prova/2/test/


How can I correctly copy the test directory to the 1/ and 2/ directory?

P.s. sorry for my awful english... :(

If your ~/Desktop/prova dir contains only subdirs, you can do

```
for i in ~/Desktop/prova; do cp -R ~/test $i; done
```

---

### Post by Gwasanaethau on 2007-06-16
> **iluvatar85 said:**
> Hello 
I have a problem with cp. i would like to copy a directory ~/test/ to all the subdirectory of ~/Desktop/prova/
I have read the man cp and tried a 'cp -R ~/test/ ~/Desktop/prova/*/ ' but it gave me a very strange result.
Supposing that in ~/Desktop/prova/ were the empty directory 
~/Desktop/prova/1/ 
and
~/Desktop/prova/1/ 

the result is:

~/Desktop/prova/1/ 
~/Desktop/prova/2/1/
~/Desktop/prova/2/test/


How can I correctly copy the test directory to the 1/ and 2/ directory?

P.s. sorry for my awful english... :(

I think it might have thought:
```
cp -R ~/test/ ~/Desktop/prova/*/
```
meant: 'copy ~/test/ and everything in ~/Desktop/prova/ into the last folder in ~/Desktop/prova/' as only the very last directory is used as the destination. You could try:
```
cp -r -t ~/Desktop/prova/*/ ~/test/
```
to see if it makes a difference, as this will tell the terminal exactly what the destination directory should be. It might just do the same thing though&#8230;

---

