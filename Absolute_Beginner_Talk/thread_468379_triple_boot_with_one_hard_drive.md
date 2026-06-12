---
title: "triple boot with one hard drive"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by linex on 2007-06-08
hi
is it possible to have xp, vista, and linux on one hard drive? i've googled and found a couple guides on doing this with two hard drives but none that did it with one.
if yes, how do i do so?

thanks

---

### Post by overdrank on 2007-06-08
> **linex said:**
> hi
is it possible to have xp, vista, and linux on one hard drive? i've googled and found a couple guides on doing this with two hard drives but none that did it with one.
if yes, how do i do so?

thanks

Hi and yes you can have up to four partitions on one drive unless you make one partition a extended as I understand it, Good luck and I have four partition on one drive. :)

---

### Post by Bohlio on 2007-06-08
Yes it is, but i dont know the details. I guess you just have to add the third OS's partition, If it is XP or Vista, Make it NTFS, If it is Linux, You need an ext3 and a swap Partition that is about double your RAM. I dont know the specifics about installing Windows, so i dont quite know if it allows you to choose the partition or what not, I have always got my Windows OS's preinstalled when i bought the computer. Funny thing is, After being with Ubuntu for a few weeks, Im probably never going to want WIndows again. I may be loosing my games, But SNES and NES roms will have to do for my entertainment. Mario Rocks!! :-)
Is there a specific reason why you want all three Operating systems on the same computer?

Edit: Im pretty sure you can have more than 4 partitions, Mabye it depends on the drive, because i have a Dell System tools, Recovery, XP, EXT3, and Swap, and i think one more... :-)

---

### Post by linex on 2007-06-08
how many partitions do i need for linux?

---

### Post by koshari on 2007-06-08
2, os(ext2,ext3,reiser ect) and swap

---

### Post by gn2 on 2007-06-08
> **linex said:**
> how many partitions do i need for linux?


Minimum 2, Swap partition and / partition.

You can only have four Primary partitions on one drive, but lots of logical partitions.

Vista XP and Linux can all co-exist on one hard drive. [http://forums.computeractive.co.uk/thread.jspa?threadID=111630&tstart=0](http://forums.computeractive.co.uk/thread.jspa?threadID=111630&tstart=0)

Not much info on how he did it though.....

---

### Post by Bohlio on 2007-06-08
> **gn2 said:**
> 
You can only have four Primary partitions on one drive, but lots of logical partitions.


Ahh, thats it!, Can you quickly explain the difference if you don't mind?

Oh and Linex, How are you starting out, Do you already have Vista, XP, or Ubuntu installed? or a mix? any info will help us help you :-)

---

### Post by linex on 2007-06-08
I think i've figured out how i'm going to do this. I have a gateway laptop that came with a xp restore disk. A vista home premium disk and ubuntu.

I'm going to format my 120gb hard drive using QTparted. I'm first going to use the restore disk and install xp. Next i'm going to use qtparted to shrink xp down to 50gb. The rest 70 i'm going to make vista 30gb. Now i have 40gb left; i'll make two more partitions. Ext2 will be 35gb and 5gb for swap.

That way i'll have 4 partitions and 3 operating systems. Anyone see any flaws in this setup? I only want vista so i can say i have vista. I'm going to be using xp for everything.;)

---

### Post by bone43 on 2007-06-08
> **Bohlio said:**
> Ahh, thats it!, Can you quickly explain the difference if you don't mind?

Oh and Linex, How are you starting out, Do you already have Vista, XP, or Ubuntu installed? or a mix? any info will help us help you :-)

You could try this one..

[http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php](http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php)

There are a lot of Ubuntu, Vista, Xp boot guides on google, you might want to read a few first and find one that works for you before you take the plung:D

---

### Post by gn2 on 2007-06-09
> **Bohlio said:**
>  Can you quickly explain the difference if you don't mind?



Certainly: [http://en.wikipedia.org/wiki/Primary_partition](http://en.wikipedia.org/wiki/Primary_partition)

---

### Post by sgtbob on 2007-06-09
Could someone explain how to change  boot setup? I have Win XP, Ubuntu 7.04 and Fedora Core 6 on one PC.  When I installed Ubuntu, I no longer have FC6 as a choice and Win XP is not the default.  What are the procedures to change the boot order to any one I choose?

---

### Post by gn2 on 2007-06-10
> **sgtbob said:**
> Could someone explain how to change  boot setup? 

It's all here: [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by sgtbob on 2007-06-11
Thanks - after spending 6 hours trying to decipher the 53 page 'how-to', I was able to move my Win XP to the top of the package in menu.lst and it works as I hoped.  Fedora is a bit less complicated, but then I'm still learning Ubuntu.

Bob.

---

