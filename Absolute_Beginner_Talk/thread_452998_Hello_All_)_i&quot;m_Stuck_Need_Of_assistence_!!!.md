---
title: "Hello All :) i&quot;m Stuck Need Of assistence !!!"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by bjbbop on 2007-05-23
Sorry to bother you all i"m stuck cannot install what do i do with this partitions i dont know i have an xp oparation system and now i"m installing the ubuntu 7.04 and i dont succeed to make a partition for it :(
i tryed all the manuals i dont find nothing mentiond about partitions and i dont wanna lose all what i have in the computer ....
your help is well appreciated and mostly needed thanx from advance to all !!!!(i"m brand new at this and i"m already stuck) 
i really want ubuntu on my computer .....

---

### Post by Hobo Joe on 2007-05-23
First, relax, we'll help you.

Second. Defrag Windows. Like, 5 times.

Then, when you boot into the LiveCD, got to System>Administration>Gparted.

Then, resize the Windows partition to the desired size. Second, add a new partition, make it fill all but about 2 GB of the space you made from resizing the Windows one. Set it at 'ext3' format. 
Then make you last partition and fill those last 2GB or so, and format it to 'linux-swap'.

Hope that clears it up.

---

### Post by alienexplorers on 2007-05-23
If you have enough room I would make 2 ext3 partitions.  Make the first one root / and the second one /home.  Remember to leave 2 GB or so for the swap folder

---

### Post by bjbbop on 2007-05-23
thank you very much i will try now i hope it whould be o"k.
just tell me please it whould not destroy all my files in the hard drive when i resize the windows partition (my hard drive is 120GB and it has only one partition plus emergency files partition of about 8 MB .)

---

### Post by discmaster on 2007-05-23
LOL bjbbop,

You sound just like me a couple mo. ago. Hang in there, these guys will get you thru it; I would strongly suggest however, that you backup any critical windows data that you don't want to lose;

GParted is a powerful tool; with a couple wrong clicks, you can easily wipe out the windows partition & everything it - trust the voice of experience, I know...

:D

---

### Post by jbrown96 on 2007-05-23
A few questions:

1.) How far did you get in the install? Did you reach the partition manager?
2.) Do you want to dual boot your computer (Ubuntu and XP)?
3.) If you reached the partition manager and it failed, were there any error messages that you could post here?

Disk partitioning is risky; data can be lost. I have had error messages with the partition manager before, but it always worked.

---

### Post by bjbbop on 2007-05-23
yes i wanna duel boot on my computer and now i"m in the partition manager and it asked me if i wanna divide my drive it gives me 4 options 
- guided resize...
-guided use all disk space
- guided use the most available biggest disk space
- manual 
i think to use the first option and i"l give it 30GB That's good ??? u think ???
and thank you very much for the assistance

---

### Post by rickycodie on 2007-05-24
thirty should be more than enough. and if you're using the installer to partition , it will make the swap partition for you.

---

### Post by bjbbop on 2007-05-24
Thank you all guys for the help i've done something :) i hope it will be o"k 
"only by mistakes we shell learn" u helped me allot all of you thanx again 
viva la linux community

---

