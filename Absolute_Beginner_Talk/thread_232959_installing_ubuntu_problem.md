---
title: "installing ubuntu problem"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by Nabba on 2006-08-09
first, when the live cd is booting up i get this error [please click]("http://nabba64.co.uk/error1.jpg") here, but it still boots up in to ubuntu, but when installing it says it can not make a partions big enough showen [here]("http://nabba64.co.uk/error2.jpg")

my guess is that my hard drive is buggered and it need a format, but i am asking here first before i do something silly.

P.S. i have 70gb free on a 80gb hard drive so i have lots of space

thanks for anyhelp, if you have any questions i be happy to answer

---

### Post by Mach1US on 2006-08-09
Have you resized existing partition to create new partition or the free space is still inside existing partition?

---

### Post by Engnome on 2006-08-09
Free space? It can't use free space on an existing partition. It need's unallocated disk space. You have to use a program to shrink your windows partition.

edit: to late :/

---

### Post by zappafrank on 2006-08-09
Let me take a guess here: You say you have 70 GB of free disk space. That space is probably taken by an empty windows partition, which ubuntu can't use. If this is the case, delete the partition and let ubuntu create its own. If you're unsure how to delete that partition in the ubuntu installer, you can also do delete it in windows.

---

### Post by junamuno on 2006-08-09
do you have windows installed on that HD, because when I installed Ubuntu, I had a lot of problems with the Windows partition not letting me install Ubuntu, Have you tried Gparted????

---

### Post by Mach1US on 2006-08-09
If you still want to keep windows for now you can use windows partitioner to shrink NTFS partition to size you like and let ubuntu partition free space automaticaly.You can use Partition Magic 7  in windows wich if you search the web you can find as free download.

---

### Post by Nabba on 2006-08-09
I have tried to resize the hard drive using Gparted so that I had about 30gb unallocated for ubuntu, it also failed

---

