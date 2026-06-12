---
title: "Need help with command structure in Terminal session"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by popuptarget on 2007-02-03
I have a task I want to complete and I know it can be done easily in a terminal session but until I can get some formal training on Linux I want to see if you guys can help.  What I would like to do is extract specific named log files out of multiple named (but structured) directories.  ie: the .doc file I want always starts with rh2 and these are located with directories that start with a one or two digit date. I want the rh2 files to be put into a dir named RH2. BTY I am new to both Linux and Ubuntu so go slow. On the up side I did figure out with cat and * to combined mulitiple files (in the same directory) into one file organized and formated the way I want.  <--that would have taken me a while in Windows but I was never that good a windows either. Thanks Jason

---

### Post by lamego on 2007-02-03
Open the terminal and type "man find", probably is what you are looking for.

---

### Post by kidders on 2007-02-03
Hi there,

I might not have this quite right. Let's see...

You have a source directory (let's call it ~/src) and a destination directory (let's call it ~/rh2). It sounds like you want to copy (move?) any file that starts with "rh2" and ends with ".doc" from the source to the destination, as long as the source file is in a subdirectory whose name starts with a digit. (With luck, I read your o/p correctly!)

How much trouble you need to go to depends on how elabourate your source directory structure is. For instance, if the date-stamped directories you mentioned are only one level deep, **cp ~/src/[0-9]*/rh2*.doc ~/rh2** should do the trick. On the other hand, dealing with source files spread across multiple levels on your directory tree would be a little more complicated.

There is one technical wrinkle you need to be aware of. Copying from multiple source directories to a single destination one creates the possibility that one or more of the source files may have the same name.

How close is this to what you were looking for?

---

### Post by popuptarget on 2007-02-03
Kidders.  You are dead on! I knew this could be done. Man you make this look easy.  Luckily the the files I want are just one layer deep.  I just used your instructions and bam its done.  This sure as heck beats windows. I have a buddy attempting to do this in windows as I type.  I love it. I just pulled up a terminal and typed the command. DONE. He is now seriously pissed.  Again Thank you for you help.  Jason

---

### Post by kidders on 2007-02-03
Hehe. I have no idea why certain operating systems make basic little things like this so complicated. :confused:

You might also like to take a look at the utility lamego suggested. Imo **find** really is very handy. It takes a bit of effort to learn the ropes, but it's tremendously powerful. It just so happened that you didn't need it in this specific case.

**Edit:** If, for instance, you didn't know whether the files you were after started with "Rh2", "rh2", "RH2" or "rH2", you could use "find" to select them, with something like **-iname rh2* -exec cp {} ~/dst \;**

---

