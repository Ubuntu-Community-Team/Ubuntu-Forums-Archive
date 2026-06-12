---
title: "swap space trouble"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by tom cuda on 2007-03-07
Hi all in Ubuntu land. Has anybody out there had the error message "Creation of Swap Space in partition #5  of IDE2 (Hdd) failed"?? If you have or know of any fixes please reply. I get to the partition part of installing Ubuntu Edgy Eft 6.10 AMD 64 version LiveCD and the info for the H/Drive that I want Ubuntu in does'nt show any free space, just unallocated space. Has any one got any ideas for me to try?
I have order the Alternative CD but I won't have that for another 4-5 weeks so I would really like to start using Ubuntu as soon as possible.
Thanks to anyone who can help.

---

### Post by chewearn on 2007-03-07
> **tom cuda said:**
> Hi all in Ubuntu land. Has anybody out there had the error message "Creation of Swap Space in partition #5  of IDE2 (Hdd) failed"?? If you have or know of any fixes please reply.

Never seen this error before; but just guessing if you might already have four primary partitions on that harddisk already?  If you don't know how to check, just post this output (run it from a terminal in ubuntu LiveCD):
```
sudo fdisk -l
```

> I get to the partition part of installing Ubuntu Edgy Eft 6.10 AMD 64 version LiveCD and the info for the H/Drive that I want Ubuntu in does'nt show any free space, just unallocated space. Has any one got any ideas for me to try?

Free space and  unallocated space means the same thing.

---

### Post by tom cuda on 2007-03-08
Hi Asta la Vista and thanks for the reply. I formatted the disk with XP and did not put any partitions on it. This really has me stumped because it's a healthy disk with no errors and I had XP on it before with no probs. Is there a central base anywhere that collects issues and problems with Linux or do we only have the forums to utilise?

---

### Post by chewearn on 2007-03-08
> **tom cuda said:**
> Hi Asta la Vista and thanks for the reply.
No problemo. :)

>  I formatted the disk with XP and did not put any partitions on it. 

I think you do have partition on it, because you can only format after you have partition.  If you do not have any partition on a disk, you cannot format it.

> This really has me stumped because it's a healthy disk with no errors and I had XP on it before with no probs.

Perhaps, you should start from beginning; tell us what install you want.  Example, single ubuntu, or dual boot.  What steps did you take to install, and where you got stuck.

>  Is there a central base anywhere that collects issues and problems with Linux or do we only have the forums to utilise?

See here:
[http://www.ubuntu.com/support](http://www.ubuntu.com/support)

---

### Post by go2dell on 2007-03-08
> **tom cuda said:**
>  I formatted the disk with XP and did not put any partitions on it. 

Unless you told XP a specific partition size to use, it used 100% of your available disk space for its partition, then formatted that partition as NTFS.

If you want any space for Ubuntu, swap or otherwise, you'll have to shrink the NTFS partition.

When installing XP, you *do* have the option of choosing a smaller size for the Windows partition.  Something to keep in mind if you repeat this process in the future.

---

### Post by tom cuda on 2007-03-09
I have been trying to install Ubuntu Edgy 6.10 AMD64 version as a dual boot (which hopefully once I get it to work I'll be considering geting rid of windows altogether) but as I mentioned before, the install gets to the formatting stage in the auto settings and then returns an error message about not being able to create a swap space. I believe that you may be on the right track go2dell, Ubuntu must not be able to find any free space because of the NTFS partition. Thanks all for the replies. I'll try shrinking the NTFS partition and see what happens.
Wish me luck and thanks again Asta la Vista and go2dell. :))

---

### Post by tom cuda on 2007-03-13
Eureka!!!!! I've finally managed to install Ubuntu :) and it looks and feels great. I'll be starting to install all the packages soon and to configure my internet setup. A big thank you to all that have helped me and hopefully I may now be of help to others that have had similar problems.
If there is an easy way to configure an internet setup in Ubuntu, please feel free to pass on any tips to me. A little help goes a long way.
:))

---

### Post by Patrick K on 2007-03-13
My DSL configured itself (onboard NIC). I had web access immediately. I didn't have to do anything other than give the email program my password and mail portal. I am using a NATS router so it may have picked up the URL needed from there. Without a router, you'll need to know the URL your ISP wants you to connect to (probably just the ISP's regular URL, like [www.xyz.com)](www.xyz.com)).

---

