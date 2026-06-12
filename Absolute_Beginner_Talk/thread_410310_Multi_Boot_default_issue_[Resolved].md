---
title: "Multi Boot default issue [Resolved]"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by sixou on 2007-04-15
Hi everyone,
I have a small issue and I am sure it's been asked a thousand times, but I just can't find the answer to it.

I recently installed Ubuntu after and in parrallel of Windows XP. (called under GRUB: Windows XP Home Media Edition or something like that).

Everything works just fine, except tha**t I'd like Windows XP Media Edition to be the default boot instead of Ubuntu.** I tried one solution found on the internet, but the result was GRUB to boot another version of Windows which was not installed on the computer, and therefore didn't work.

Btw, I am using a Inspiron E1505 laptop from Dell.

What should I do?

Thanks

---

### Post by zvacet on 2007-04-15
in the grub menu list put right name of your windows and 
[http://ubuntuforums.org/showthread.php?t=409771&highlight=grub+order]("http://ubuntuforums.org/showthread.php?t=409771&highlight=grub+order")

---

### Post by JLB on 2007-04-15
if you only have Windows and Ubuntu installed you need to change 1 entry in /boot/grub/menu.lst .
```
default     0
```

change it to ```
default     4
```

for example:  (snippet from my own menu.lst)
> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

see the last line? Change the 0 to a 4.

---

### Post by aysiu on 2007-04-15
More details here:
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by sixou on 2007-05-07
Thanks it worked.

---

