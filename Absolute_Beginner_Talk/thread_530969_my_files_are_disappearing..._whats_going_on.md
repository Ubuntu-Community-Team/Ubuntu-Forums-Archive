---
title: "my files are disappearing... whats going on?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by yellowband on 2007-08-21
hi

i just noticed tonight ath a lot of files have just disappered from my computer.  Things from movies, documents, and whole directories have vanished without a trace.  I'm an idiot and didn't back my stuff up, although i didnt' lose anything critical, i lost some time-consuming documents.  What could've happened?

possibley a hard drive failure? my laptop is pretty new....

a virus? a misbehaving program?   any help at all would be awesome.

---

### Post by K.Mandla on 2007-08-21
Can you give us a little more information? Are you using separate hard drives? Did you uninstall any software? 

A hard drive failure would probably be a lot more dramatic. For the mean time. ...

```
find / -iname "*name_of_the_file_that's_missing*"
```
might help you track down your missing stuff.

---

### Post by yellowband on 2007-08-21
thanks.i;ll try that

my laptop has a single internal hard drive.  i've been tinkering with new programs and whatnot, i installed qt4 today, that's about it for a while.  

i've had a few weird screen glitches when disconnecting projectors and monitors to my computer, had to do an xserver restart a couple of times.  

its wacky, its like all references to tiles and folder have gone.  for example, i had a shortcut to my documents folder in the "places" menu at the top of the gnome panel.  now the documents folder, and that link shortcut are gone....

---

### Post by AceofSpades19 on 2007-08-21
can you access your folders or files from the terminal?

---

### Post by yellowband on 2007-08-21
no, they are completely gone!!! i'm rattled

check this. i also had a folder of all the seinfelds, and they are all buggreed.  the files are there bgut they are all garbage now.... so strange.

guess i'll do a reinstall, never thought i would have to with linux. hope it doesn't happen again.


does anybody know of a hard drive diagnostic i would run in ubuntu to just check if my hard drives aren't messed up?

---

### Post by hyper_ch on 2007-08-21
fschck

---

### Post by steve.horsley on 2007-08-21
It's fsck (check the man page if it's still there). But it's probably best to run it from a live CD - I'm not susre if you can fsck the running system partitions.

---

