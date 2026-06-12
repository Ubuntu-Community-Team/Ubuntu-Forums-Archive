---
title: "installing ==&gt; partitioning help (beginning - end ?)"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by shadows123 on 2007-08-17
when i'm installing ubuntu, partitioning it,
i want to make a new swap partition,ok fine, i tick 3000 MB (3GB) and then choose swap and then there's BEGINNING or END ? which do i choose??

now for the next partition, the main partition.. i think it must be EXT3 right? with mounting : "/" and should it be BEGINNING or END?

Thanks..

---

### Post by diatribe on 2007-08-17
are you working with an empty harddrive?  if so I believe the beginning/end refers to which cylinders it will be using.  in this case you would put your primary partiton (/) at the beginning and swap at the end.  and also your / partiton doesnt HAVE to be ext3, but it is preferable

---

### Post by shadows123 on 2007-08-17
i also have XP installed on it.. i want to keep my xp..
Thanks..

---

### Post by ashmew2 on 2007-08-17
When ur installing Ubuntu , just put the size and dont worry about the start or end , just put the size in and press Create Partition.
The Swap should not exceed 2 GB (its MORE THAN ENOUGH) , make it of the type linux-swap
The / partition should be of ext3

---

### Post by shadows123 on 2007-08-17
you sure i shouldn't worry about beginning and end? 
thanks..

---

### Post by ashmew2 on 2007-08-17
I believe you have XP installed to ur C: drive , if you have a single hard drive , the partitions must be named something like :
/dev/sda1 ===> that is your c: drive
after that there'll be a bigger parition (the size of the whole hard drive excluding c: drive) , something like /dev/sda5
then your other drives , d: , e: f: will be in serial order 
/dev/sda6 =>d: drive
/dev/sda7 = > e: drive 
and so on..
you can have different numbers.

If you want to keep XP , ull want to make sure you dont do anything with the Xp partition.
You can delete the other partition (any other ) and make the swap and root partitions from the size ull get after deleting.
But , you will lose all the data on the partition you delete.

---

### Post by shadows123 on 2007-08-17
yeah, i know, i had change space of a partition.. so i have 30 gigs left for swap and other one..

so what shouldi put beginning or end?

could you explain me what it means?
thanks..

---

### Post by ashmew2 on 2007-08-17
and by the way , i highly recommend backing up data before partitioing.
Although it doesnt usually go wrong , but in rare cases it does !! (lol)
So , you better not take any chances !
And yes i have never really worried about the start and the end ,  i just give the size and it does the rest on its own.
I have only installed ubuntu about 50 times :lolflag:

---

### Post by shadows123 on 2007-08-17
yeah but it's not my xp partition i have resized hehe :p.. it's a partition with some stuff i don't really need lol..

---

### Post by ashmew2 on 2007-08-17
Ok , ill try to be general here.
Your hard drive is divided into many little little parts called cylinders.
Like 1 gb is divided into 1024 parts (called MB).
So these parts are in order (1 , 2 , 3 , 4 , 5, 6 ....so on..)
So if you put the start of a partition at 9000 and make the size to be 2000 then your partition will be from 9000 to 11000 (9000+2000) on your hard drive. You'll still have the 1 - 9000 left and the 11000 to the end of your hard drive.
Although it doesnt really matter , but usually the partitions are in order (if you've installed XP , it usually does it in order , but you never know with windows lol..). So u can always disturb the order , it doesnt really matter !!

---

### Post by shadows123 on 2007-08-17
ok, so if i put for the ext 3 partition mounting point : "/" i will be able to check my xp too huh?

---

### Post by ashmew2 on 2007-08-17
See , a mount point is nothing but the location which the ubuntu system thinks the harware is at , for example  , if you put your mount point for c: drive as /media/hda1 , then ubuntu will consider the path 
/media/hda1 to be the c: drive.

the "/" is the root partition (just as you have the windows directory in XP) , Ubuntu creates this system partition. This HAS to be an Ext3 (or reiserfs etc , but i prefer Ext3) . I didnt quite understand what you meant "I will check out my Xp too" . I took it to be something and i think its correct. You should be able to access all your hard drive parititions from under ubuntu. They'll be at the mount points you specify after the installation. the xp partition will be at /media/sda1 (hopefully :P ) .
If i got it all wrong , let me know !

---

