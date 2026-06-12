---
title: "Uh-Oh, Resizing Partitions on Dual Boot!"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-10
Alrighty so I have been using Ubuntu for a few months now and i love it!  although i had to reconfigure my xserver and my wireless was a pain in the *** to get set up i am quite happy.  So now it comes time to shrink my Vista partition.  I have a lot of questions pertaining to this issue so bear with me haha

My vista partition was 75GB give or take a few and in vista it will not let me shrink it less than 60GB or so even though i'm only using 32GB!?!?  
Does anyone know if the 10GB labeled "recovery" can be tampered with or is it better to leave it?  
Now to ubuntu to resize my /home partition i have to unmount it then move/resize but how do i do so if it is part of an extented partition?  

if anyone has any thoughts or has successfully resized their partitions on a dual boot machine that could help me out i would greatly appreciate.  I'm going to boot the live CD now and take some screenshots to help you all out.

Thanks, Alain

---

### Post by S15_88 on 2007-07-10
Here is a screen shot of my partitions their locations and their respective formats.

Thanks, Alain

---

### Post by regomodo on 2007-07-10
do you have a full install vista disk or a recovery disk. If it's the latter leave the recovery partition well alone.

About resizing, i've read (i may be wrong) not to use linux partions apps on NTFS and use acronis instead. Acronis has saved my bacon a few times in xp

---

### Post by S15_88 on 2007-07-10
Acronis is a pretty sweet program but it's not doing what i need it to do :(  i'm not sure how i should go about extended my /home!  in vista i shrunk the partition but it won't let me expand my /home, and using the live CD i can't do it either! i don't know what to do next!

Thanks, Alain

---

### Post by bluknight on 2007-07-10
If you're using grub to boot new UUIDs for resized partition must be inserted in the menu.lst file
>vol_id /dev/sdx (new partition) | grep UUID
(paste new UUIDs into old menu.lst)

---

