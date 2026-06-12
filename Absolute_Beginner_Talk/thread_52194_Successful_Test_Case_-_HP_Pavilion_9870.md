---
title: "Successful Test Case - HP Pavilion 9870"
date: 2005-07-26
forum: Absolute Beginner Talk
---

### Post by ericmarceau on 2005-07-26
<PRE>

Just to let people know that there is not always bad news, 
I thought I should post some good news.


PHASE I - [COMPLETE]  Install from CD Distribution
===============================

I used the Ubuntu 5.04 "Hoary Hedgehog" release distribution disk included in

    LINUX FORMAT - July 2005 Issue   

and the install went very smooth onto a virgin disk.

    N.B. For this excellent choice, I have to thank my Debian-Fanatic brother,
             David Marceau,  Ottawa, Ontario   (davidmarceau@sympatico.ca) 

It auto-detected the domain name server for my ISP, Rogers HIghSpeed.
I only needed to tell it in one of the configuration windows

   => AFTER FIRST LOGIN   =>  Linux OS fully operational 

to map the detected server as the formally tagged DNS host.

I had full immediate access to the web.

   N.B.  Cable Modem:   Motorola SURFboard      P/N 500887-025-00


PHASE II - [COMPLETE]  Web-based Update of Distribution
====================================

I used the "aptitude" tool recommended by my brother for identifying
any recent updates for download and performed the updates without
a hitch.

   OBSERVATION:  There is even a category for "virtual packages", namely
       dependency tracking and update information for packages which are
       not under Ubuntu control (i.e. commercial packages) so as to 
       again keep the process of managing the platform as simple as possible.
       I am extremely impressed ... so far!


PHASE III - [No problem anticipated]  Configuration of e-mail services
===========================================

I have not yet attempted this, because I need to re-attach my computer
cable to set my old Windows ME C: drive as boot to extract the setup
details for my account and servers (now outsourced by Rogers to Yahoo!


PHASE IV -  [TBD]   VMWare (or equivalent) for Windows ME C: Drive Migration
================================================

I will be installing a new Linux filesystem (Reiser FS) for use as my 
Windows emulation environment.  This will be my failsafe fallback in case
some of the legacy application data is not imported directly or interpreted
correctly by the new Ubuntu-signed application suite.


MY BACKGROUND
===========

I am a mechanical engineer.   I have been an HP-UX Administrator since 
1984 but had    ** NO **   exposure to Linux until this attempt to install 
from CD. 


CONCLUSION
========

My opinion is that Ubuntu 5.04 "Hoary Hedgehog" release is as close 
as it can be to the ultimate turnkey install of the base Linux.  My own
experience with software development and deployment in the CAD/CAM
and technology transfer world has never seen anything which performed 
so smoothly, hence my need to broadcast the good news.

I wish every other newbie the same smooth first cruise on the LInux wave!

</PRE>

 =D>

---

### Post by ericmarceau on 2005-07-26
One slight point of irritation:  Swap partition size assignment.

I was limited to establishing 1.5 Gbyte as my swap partition.
I know that I would like to expand my memory (currently 512Mb)
but my own experience is that performance is optimum when
swap size is of the order of 5-10 times RAM. 

Does anyone know why this size limitation was imposed, rather
than have a BIG FAT UGLY WARNING that if you venture into
larger than recommended (1.5 Gb) you should have concrete
reasons for it.

Thanks,

---

### Post by aysiu on 2005-07-26
[QUOTE=ericmarceau]
but my own experience is that performance is optimum when
swap size is of the order of 5-10 times RAM. [/QUOTE] Maybe that's what your own experience has been, but I've never read of such a thing--in the books or on the internet. The most I've heard is twice the RAM. Sometimes I've heard of the same as RAM or 1.5 times the RAM.

---

### Post by ericmarceau on 2007-02-13
The experience I had at tuning an old HP9000/500 system was that optimum performance was reached if the "Segment Swap" time was 6 times the "Partition Swap" time and that the "Partition Swap" time was 4 ticks (not the 50 and 50 that were default).  This gave me a measure performance boost (by benchmark) of over 92% pre-tuning.  The Virtual Memory reserved for the arrangement was 6 times the RAM (also adjusted from a default of 2).  When you have large quantities of coding that need to remain accessible in RAM, it is best to load from a memory-formatted swap than constantly loading from non-formatted disk library, hence, my desire to configure more than the 2 times RAM for swap, and my irritation at not being able to set a larger value because of some hard-coded ceiling based on someone's assumption of the end operating environment.

Eric

---

### Post by ericmarceau on 2007-02-13
Sorry, the "Partition Swap" should have been "Paging Swap".

Eric

---

### Post by mikewhatever on 2007-02-13
Depending on the size of RAM, it is advised to size the swap partition about 1-2 the size of RAM. If you have 1GB or more of RAM, you can even do away without the swap, but 512 MB is fine too. I have 1GB of RAM and about 900 MB of swap, and was surprised to find out, that it is never used. Windows, on the other hand, regularly uses 300-600 MB of page file.

Just to mention, before I forgot, I don't think 5.04 will be supported much longer. You might want to check on that.

---

