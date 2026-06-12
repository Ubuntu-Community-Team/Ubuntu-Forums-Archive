---
title: "acroread and exit"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by utab on 2006-01-20
Hi there, 

Typing acroread xxx.pdf goes fine on terminal and xxx.pdf(softcore :D) opens.

I guess there must be a way to exit the file from the terminal also or am I wrong ?

thx.

---

### Post by darth_vector on 2006-01-20
```
sudo apt-cache show acroread
``` says the following about acroread:
> Description: Adobe Acrobat Reader: Portable Document Format file viewer
 Adobe Acrobat Reader for viewing and printing Adobe Portable Document
 Format (PDF) files.
it is only a reader.

you may want to check the manpage for more details.

---

### Post by ekarni on 2006-01-20
By exit you mean close the file and exit from acroread?  Just hit Ctrl-C!  This kills the acroread process and you're back to the command prompt.

---

