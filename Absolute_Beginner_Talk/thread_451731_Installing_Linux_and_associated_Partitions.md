---
title: "Installing Linux and associated Partitions"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by jamesc1979 on 2007-05-22
I think I'm missing a fundamental Linux concept.  I know i need to create these but don't fully know what each is for or how to create them and make it all work.

I want to create 3 partitions:
  - root    10Gig
  - swap    1Gig
  - Home    will take up remaining 40Gigs

I am going to partition all three as EXT2.

I am new to linux so don't fully understand this stuff.

1.  Partition type... Should they be Primary or Logical?  Whats the difference?

2.  what order do they need to be in (Location - Beginning/End)?  Does it make a difference?

3.  as far as the mount points for each... what format do they need to be in?   I know where they need to be entered but not the how and why.

---

### Post by rhysmc on 2007-05-22
Hi James, welcome to linux.

First of all your swap partition must be formatted to the linux-swap format not EXT2. I would also suggest formatting to EXT3 not EXT2 unless you have a specific reason.

A partition is either Primary or Extended. There can be a max of 4 primaries. if you need more than 4 a extended can be set up.

[img]http://img155.imageshack.us/img155/3233/w2u302wy.png[/img]

2. Order does not matter

3. I dont understand what you mean ...

Are you installing on the whole disk?

---

### Post by Scunizi on 2007-05-22
rhysmc has it right.  One other thing to remember.  If you need more than 4 partitions (total including any windows on the same drive) then the 4th primary partition must be designated as the extended partition before adding any more.  Think of the extended partitions as "subdirectories" of the primary (first) extended partition.  The graphic in the last post does justice to the concept.

---

### Post by jamesc1979 on 2007-05-23
Rhysmic,

No, Ubuntu will not be taking the intire drive.  I currently have a 150 G drive w/ a 100g partition for windows.  The remaining 50 will be for Ubuntu.

Back to the question of mount points, the Ubuntu 7.0? install asks for the mount points for the different partitions.  What do I type in the space for each type of partition?  Does it make a difference?  or do i simply

---

### Post by Scunizi on 2007-05-23
You typically have 3 mount points unless you want to get fancy.  The three are "root" defined as "/", swap defined as "swap" and home defined as "home".  Usually on install there is an option to allow the installation program take care of mount points and partiitons by itself.  All you do is tell it to use the "empty" space.  This is typical on the "desktop" cd.  If you are using the alternate cd because you want to resize your HD then you'll have to resize your windows partition and create the other partitions as you mentioned.

---

### Post by jamesc1979 on 2007-05-23
> **Scunizi said:**
> You typically have 3 mount points unless you want to get fancy.  The three are "root" defined as "/", swap defined as "swap" and home defined as "home".  Usually on install there is an option to allow the installation program take care of mount points and partiitons by itself.  All you do is tell it to use the "empty" space.  This is typical on the "desktop" cd.  If you are using the alternate cd because you want to resize your HD then you'll have to resize your windows partition and create the other partitions as you mentioned.

Scunizi,

I've installed Ubuntu that way before.  This time i have an existing partition i want to use.  The reason I'm doing it this way is because I don't want to resize the windows partition.  This has become quite the learning experience for me

Thanks for your help.

james

---

