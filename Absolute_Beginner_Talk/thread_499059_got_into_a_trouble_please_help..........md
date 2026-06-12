---
title: "got into a trouble please help........."
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by kartik2104 on 2007-07-12
hi!
while installing ubuntu i selected resize existing partition wid 50:50 then linux used 20 gigs out of the available 80 gb hdd 40gigs was available for windows and the rest 20 was left unpartitioned , unfortunately i made a new partition out of the available 20gigs of unpartitioned space which was supposed to be used by fiesty using the windows partition wizard now when i m starting my system i m getting the following

loading grub stage 1.5

loading grub. please wait.......
error 17
_


nothing else is available.
i ran the live cd of fiesty and found that both windows and fiesty are safe at their positions just i m unable to go through the boot loader.
what shall i do now?
please send ur valuable suggestions.
thank you for having a look at my problem.
thanks in advance for your replies.

---

### Post by tbresson on 2007-07-12
You need to re-install GRUB. I think there's a couple of guides here on the forum.

Like this one: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by kartik2104 on 2007-07-12
i dont see any partition wid \boot
there is swap and ext3.now what shall i do please tell me....

---

### Post by kartik2104 on 2007-07-12
at least somebody tell me how can i start my system in windows which is safe..
please its so important...

---

### Post by robertc36 on 2007-07-12
Grub is written to the MBR.
Looks like you have killed that either follow the guide to reinstall grub or you could reinstall ubuntu that would reinstall the grub.
I would also suggest choosing the manual option when partitioning this time.

---

### Post by kartik2104 on 2007-07-12
thanks robert for your suggestion now can u spend some more time and tell me how to repartition, i have tried doing that but when i delete the existing partitions of swap and ext3 and make new partitions out of it under the names of swap i.e 1024mb and ext3 18000odd mb and hit forward, it is asking me for the root directory saying no root directory specified.
please help me.....
i will be waiting for your reply.......

---

### Post by kartik2104 on 2007-07-12
i mean to ask u for the manual partition.

---

### Post by kartik2104 on 2007-07-12
> **kartik2104 said:**
> thanks robert for your suggestion now can u spend some more time and tell me how to repartition, i have tried doing that but when i delete the existing partitions of swap and ext3 and make new partitions out of it under the names of swap i.e 1024mb and ext3 18000odd mb and hit forward, it is asking me for the root directory saying no root directory specified.
please help me.....
i will be waiting for your reply.......


thanks robert for your suggestion now can u spend some more time and tell me how to repartition manually, i have tried doing that but when i delete the existing partitions of swap and ext3 and make new partitions out of it under the names of swap i.e 1024mb and ext3 18000odd mb and hit forward, it is asking me for the root directory saying no root directory specified.
please help me.....
i will be waiting for your reply.......
__________________

---

### Post by robertc36 on 2007-07-12
When use choose the drive .
Delete the partition and there is an option to automatically partiton the available space.
That will set up the swap for you.

---

### Post by kartik2104 on 2007-07-12
you mean i must delete the partitions first and leave the unpartitioned space of 20gigs as unpartitioned only and then hit forward.
please tell me more before i proceed with this..
anyways thaks for your suggestion.

---

### Post by kartik2104 on 2007-07-12
are u sure robert that my windows partitions will not be touched by this.

---

### Post by kartik2104 on 2007-07-12
> **kartik2104 said:**
> are u sure robert that my windows partitions will not be touched by this.


Robert i m sorry if i am disturbing you but please write me something about manual partitioning before i proceed with that.
i am waiting for your reply...

---

### Post by robertc36 on 2007-07-12
ok just had a look at your set up.
Just use 20 gig for ubuntu as planned and leave the other 20 just in case.
You can always partition that later as ntfs and then mount in ubuntu.
Apart from ubuntu , i have all my other drives etc mounted as ntfs not ext3.
I left it like this in case i wanted to go back to windows (which i don't).

---

### Post by kartik2104 on 2007-07-12
okay robert thank you very much for your valueable suggestions,

---

### Post by robertc36 on 2007-07-12
by the way it took me 4 installs initially as i kept killing things so i am there with you
Just make sure you double- triple check through the options!!!!
Delete the correct partition.

---

