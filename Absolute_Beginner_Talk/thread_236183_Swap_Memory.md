---
title: "Swap Memory"
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by MarvinZurcher on 2006-08-14
What is swap memory and what is it used for? Is mine working correctly? Thanks in advance.

---

### Post by TMR on 2006-08-14
It's where progs and data are 'swapped' to when you are running out of RAM.  They are written to that area of the disk and, when you want them, they are copied back into memory (and something else gets swapped out to make room).

TMR

---

### Post by TMR on 2006-08-14
PS, nothing on the pic to suggest you have a problem.  If you want to exercise it a lot, try firing up loads of apps and/or allocing huge amounts of memory.

TMR

---

### Post by bruce89 on 2006-08-14
3GiB seems like overkill, the size of it should just over the amount of memory you have.

---

### Post by MikeMLP on 2006-08-14
If you are familiar with windows, than swap memory is like the Windows Pagefile:  it is a place on the hard drive that is used as memory.  In linux, this area is given its own partition (probably so that you don't accidentally fill up your HD and cause your machine to be unbootable when there is no room for a swap file, a concieveable occurrence in Windows.

Now to your screenshot:
The general rule of thumb is to make your swap partition 1.5 to 2 times your physical memory [http://psychocats.net/ubuntu/installing.html]("http://psychocats.net/ubuntu/installing.html")
In this case, your screenshot indicates that you have a 2.9 GB swap partition, and 1 GB of physical memory.  So in theory, your Swap partition is about 1 GB too large.  Additionally, in that screenshot you aren't using any swap space.  Congratulations! because that means your performance will be better, as the hard drive is much slower than your physical memory.  If hard drive space is an issue you may want to consider making your swap file smaller, as it could yield about 1 GB more space.  This may or may not work depending upon how your Hard drive is partitioned.  If have lots of space left on your hard drive, than it is probably best just to leave things alone.

---

### Post by bulldog on 2006-08-14
Swap memory is used when your fysical memory is in use.
If you have 1 GB or more fysical memory,swap will almost not been used in normal use.

If you made a swap partition when you installed Ubuntu [mostly 1-2 GB] you have not to be worried if it "works" it does when it's needed by the system.

Windows does the same,only it uses your C:/ drive and not a separate partition.

Hope this answer your questions.

---

### Post by schurtek on 2006-08-14
This little trick gives me a major performance boost on my linux box. When I install linux, I partition the drive manually. The first partition is my swap partition. Then my system/root/boot partition. Then everthing else. 

Natively, Linux puts the swop at the end of the hard drive. This slows things down cos the heads have further to travel every time you open a program or file.

Your operating system will only use the physical RAM on your PC for what it is currently working on at that moment. Everything else is stored in Swap space.

My formula for Swop Space...

Standard PC: SWOP = RAM x 2
Standard Server: SWOP = RAM x 1.5
HiEnd PC: SWOP = RAM X 4
HiEnd Server: SWOP = RAM X 3

---

