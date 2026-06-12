---
title: "SWAP File"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by axlr8fullrpm on 2007-08-22
I  installed ubuntu and everything is fine, the only thing i noticed is an application that i installed is always using the swap file instead of the physical memory making the application very slow. I have 2GB ram and i think it is enough to run the application without using the swap file. My question is, Is there a way to run an application on the physical memory and not on the swap?

---

### Post by heimo on 2007-08-22
> **axlr8fullrpm said:**
> I  installed ubuntu and everything is fine, the only thing i noticed is an application that i installed is always using the swap file instead of the physical memory making the application very slow. I have 2GB ram and i think it is enough to run the application without using the swap file. My question is, Is there a way to run an application on the physical memory and not on the swap?

It'd be interesting to know how to do the opposite, forcing application to use just swap. I don't think there's a way to do that. What is the application? How have you diagnosed that it's only using swap?

---

### Post by schorsch on 2007-08-22
Do you really use a swap **file** or are you using a swap **partition**? Using a swap file is waaaaay slower than using a swap partition .....

---

### Post by anaconda on 2007-08-22
> **schorsch said:**
> Do you really use a swap **file** or are you using a swap **partition**? Using a swap file is waaaaay slower than using a swap partition .....

actually this isn't true anymore! Because swap file is nowadays mounted directly in fstab it is just as fast as swap partition, which is mounted the same way... (the difference is very small) 

Eg. accessing data from the swap file you dont access the filesystem first and THEN access the swap from that file. Like it used to be. Now swap file is accessed directly.

---

### Post by schorsch on 2007-08-22
Uups, that was quite new to me. Thanks for the info .... I learned the difference between swap file and swap partition many years ago .. ;-)

---

### Post by axlr8fullrpm on 2007-08-22
Whenever im running a instance of dynamips the swap usage rises, but the actual memory remains the same.

---

### Post by heimo on 2007-08-22
> **axlr8fullrpm said:**
> Whenever im running a instance of dynamips the swap usage rises, but the actual memory remains the same.

But how much does it use memory? And how your memory is used for different purposes before and after launching this application (run *free *on command line before and after)? It's perfectly possible for your RAM usage to stay about same even if this program takes part of it. What does output from top or ps tell for this program?
```
ps aux | less
```And what happens if you stop swapping and run this application.
```
sudo swapoff -a
```

---

### Post by 2manydrugsago on 2007-08-26
I and a new Linux user and I need some help. My situation is this. I am installing Ubuntu on my XP box, I have 2G of ram, And I have a raid 0 set up (the raid controllers are  on the motherboard) When I install Ubuntu do I need to reate a new partition on the same physical drive or can I use a separate HDD? Also what size should I make the swap partition? 
Thanks

---

### Post by david_e on 2007-08-26
> **2manydrugsago said:**
> I and a new Linux user and I need some help. My situation is this. I am installing Ubuntu on my XP box, I have 2G of ram, And I have a raid 0 set up (the raid controllers are  on the motherboard) When I install Ubuntu do I need to reate a new partition on the same physical drive or can I use a separate HDD? Also what size should I make the swap partition? 
Thanks
With 2Gb of RAM your swap partition will be unused for the 99.999% of the time. You really need it only if you plan to make memory consuming task frequently. I have 2Gb of RAM plus 1 Gb of swap because sometimes I run numerical software (Matlab, FreeFEM++ and others), but actually its always empty. Even when I am building FreeFEM++, which makes an heavy use of template metaprogramming, with make -j3 I don't use more than 1.8 Gb of RAM.

If you plan to use ubuntu for desktop you should not need swap. (You can always make a swap file if you need a lot of memory and you didn't plan that).

*** EDIT ***
Can't help with the RAID stuff.

---

### Post by 2manydrugsago on 2007-08-26
Thank you so much for the advice. I have more questions  not related to swap file. Is ther a way to see a list of programms that work on windows  that will not work on Ubuntu  box? I ask because if I can stop  using any MS products I will feel better about myself.

---

### Post by david_e on 2007-08-26
Some Windows application is available for Linux too.

Many Windows applications have an excellent Linux substitute.

For the others you can try wine. This is the database of the working ones :

[http://appdb.winehq.org/](http://appdb.winehq.org/)

or there are other alternatives, like CrossOver Office for MS Office.

Finally you can emulate windows to run some apps using vmware (search the ubuntu wiki).

It's very hard to know if you won't need windows anymore until you try ubuntu for a while.

---

