---
title: "ubuntu on unallocated space !"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by happyweb on 2006-08-19
before installing ubuntu 6.06 ,
i started my pc with a bootable cd and ran fdisk command ,after that i deleted one of my extended dos partitions ( D: ) that was 20 GB in space and was completely empty , and then i shutdowned my pc and then restarted it and ran Ubuntu 6.06 and during installation steps when it reached the option to select hard drive space it is showing three options:
1) erase master hard drive etc..... (which i dont wanna do as i want to keep my windows 98 SE intact and untouched which is on my C: )
2) install in the largest continous free space.
3) make manual partition..

Now i selected the second option
and then it processed the step and then is showed me
that partition #3 will be formatted
and partition #7 will be used for swap purpose..

and then i got confused and aborted the installation

now was this second option correct and would this step had
installed ubuntu in D: (that was previously one of my partitions)

or do i have to follow some other steps in order to install ubuntu in the unallocated space (this unallocated space has been created when i deleted D: partition using fdisk)

---

### Post by ron999 on 2006-08-19
Hi happyweb

I think that you were on the right track using option 2.
It would have installed Ubuntu in the largest unused partition that it could find. This would have been D, which it is referring to as #3. So probably #1 is Windows and #2 is another partition that is less than 20GB.
When it does the install it automatically keeps part of that 20GB to use as a swap file - this is being referred to as #7.
So I'd say yes, go ahead with option 2 - or wait till you get a second opinion from another forum user.

Ron

---

### Post by GeekSpeek'r on 2006-08-19
so, when ubuntu is indicating where / what it will do; what are the sizes of the partitions it would like to manipulate? They should be ~the same size as you have fdisk'd out (combined (~20GB)). Make sure that the size is not the same as your XP partition.

Since we cannot see what is happening real-time, it is impossible for us to know what partitions / areas of the disk it is looking at.

Yes, Option 2 was the correct choice -- this should completely ignore the XP area as it is not free / unallocated

---

### Post by steve.horsley on 2006-08-19
If you aborted after the partitions were written the I guess you will have to delete them again or you won't get the option to use free space again next time you run the installer. 

You were on the right track.

---

### Post by petersjm on 2006-08-19
I concur with the others. Option 2 was the right thing to do. It's the same thing I did, deleted a partition and used "largest continuous free space". I believe it sets up its own swap file - your partition #7. Use fdisk or gparted to see if the space is still unallocated and try again. Good luck!

---

### Post by happyweb on 2006-08-20
Thanks you everyone for your prompt and informative sugestions
following which i managed to get ubuntu installed on my Box,
actually i took the option 2) which i talked a about and many of you also suggested to go for that option, it proved to be the right option as it installed ubuntu in the unallocated space which i had created my removing one of my partitions ( D: )

thanks again to all,
without all your support i would not have been able to
install ubuntu on my pc

cheers
happyweb

---

