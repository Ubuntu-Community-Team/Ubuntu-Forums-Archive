---
title: "first installation &amp; partition"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Armand_i on 2006-10-01
Hi- I have an old laptop and successfully installed ubuntu.

some background:

This laptop is for ubuntu only. No windows- no other OS. I am only using ubuntu on this laptop.

Before this, I've really only ever used windows, so I tend to think of everything in windows terms. 

Most of the things I will be doing are very simple: Word processing, mp3, web browsing, some spreadsheets, pdf stuff, email.

I had the ubuntu set up the partitions automatically.

so here are my questions:

1. Are partitions analogous to "drives" in windows? for example does "dev/hda1" = my windows "C drive"? Or am I thinking about this all wrong?

2. I don't understand what I need a swap partition for. It sounds like it's connected to RAM.

3. The OS created 2 partitions for me. One is the swap partition (called dev/hda5). The other is dev/hda1. I presume this is what people call a 'root directory'.

4. If the big directory is hda1 and the swap is hda5, and together they take up all the space on the hard drive, then what happened to hda 2,3 & 4 ?

5. I read somewhere that some people reccomend having three partitions: swap, root and "home" and that "Home" is for all of my files (documents, music etc.) Is this a good strategy for beginners, or do you think it will simply make my life confusing?

thanks in advance for any thoughts or answers.

- Armand

---

### Post by devils_casper on 2006-10-01
Hi !

whole filesystem under / (root) can be installed in separate partitions. so.... its not like windows C: drive. you can create a separate parition for each folder under root. even then it will be treated as folder under root.

you are right. SWAP space is connected to RAM. windows uses concept of virtual memory. it randomly allocate a space in Harddisk. Linux create separate partition for this purpose as SWAP.
separate Home partition is beneficail coz all data will be safe even if system crashes. you can increase its size anytime. well ! its ok under root though. nothing to worry right now.



casper

---

### Post by Armand_i on 2006-10-01
Thanks so much! 

I am trying to create the home directory right now (I am reinstalling and starting from scratch). 

I was able to create a new allocated partition for "home", but the computer is calling it "New Partition #1" and I can't figure out how to change the name to "/home" .  Can I change the name later?

Also: should I name it: "dev/home" or just plain old "/home"

---

### Post by Armand_i on 2006-10-01
Hey- I just answered my own question ! I am allowed to rename partitions during the "prepare mount points" stage ! which comes AFTER the prepare partitions stage.

I was confued because I thought you had to name the partitions while you were creating them.

I will add these notes in case any other newbie (like me) has the same problem- this is all for 6.06 (Dapper Drake)

OK- here's what I got 3 partitions:

partition #1 is the so-called root directory where the OS will live. This is simply named "/" This must be reformeted (check reformat box)

partition #2 is my "home" it is named "/home" it need not be reformatted. This is where my files will go.

partition number three is named "swap" without an slashes. I did not have to reformat it. Thanks to devils_casper, I also know this is like virtual memory.

the system is installing even as I type this (yes, I'm typing this on another computer).

cheers !

Armand

---

