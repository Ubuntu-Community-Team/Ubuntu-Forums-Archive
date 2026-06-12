---
title: "[SOLVED] Partition jungle"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by BurKaBU on 2008-02-24
Long story short, I failed installing Ubuntu on my disk. But while searching for an aswer on how to fix it I came across lots and lots of options on how to partition youre disk when you want to dualboot with XP.
So was hoping I could get an (somewhat) unanomus answer on how many partitions to split my 100gb hd in, where to put /home, swap etc in and what filesystem (I would like to be able to acces movies and .mp3 that I already have on my HD)

My system is a HP nx9420 with 100gb HD, where I intend to dedicate 15gb to Ubuntu while im learning the system.

-Thanks in advance, BurKa

---

### Post by oedha on 2008-02-24
mm......i will do this
ntfs, 20GB for winxp
ntfs, the rest for data
ext3, 15GB for Linux
swap, 1GB (twice of your RAM size)

---

### Post by BurKaBU on 2008-02-24
> **oedha said:**
> mm......i will do this
ntfs, 20GB for winxp
ntfs, the rest for data
ext3, 15GB for Linux
swap, 1GB (twice of your RAM size)

Tnx for fast repply, its just that it brings me to a question I forgot to ask in first post... How do I make a partition ext3, is that something ubuntu does automaticly if I try install it to unpartitioned space?

ps. I have 2gb ram, does that make swap 4gb, seems a little big to me :(

---

### Post by wolfen69 on 2008-02-25
> How do I make a partition ext3, is that something ubuntu does automaticly if I try install it to unpartitioned space?

ps. I have 2gb ram, does that make swap 4gb, seems a little big to me 
yes, ubuntu will automatically make it ext3.

i would make swap 512mb, as your unlikely to use much if any.

---

### Post by oedha on 2008-02-25
you just can make the swap 2gb....
(my friend said that if you have huge RAM...swap will be no need....i am not sure about this)
you can use gparted :==> [http://gparted.sourceforge.net](http://gparted.sourceforge.net)
for managing your partition
before you install ubuntu....i suggest you to defrag your windows 2-3 times

---

### Post by BurKaBU on 2008-02-25
Ok then so if I make 4 partitions:
20gb Windows
65gb Ntfs with movies and mp3 stuff
14gb ext3
1gb ext3 for swapfile

And about defragging windows before this, do i do it before i change partitioning to my disk with partition magic or after?

ps. isnt it just as easy to mount my windows partition with its movies and everything if i keep it 85gb?

---

### Post by oedha on 2008-02-25
before resize the partition
for your ps, yes you can......but if your windows crash..?
basically if you just pull 15Gb for ext3 and swap....no problem at all
since windows partition can be read/write from linux

---

### Post by 10Digits on 2008-02-25
Yes it is perfect for Dual booting with XP ..
But, what if **_i want to install ONLY Ubuntu_**????
How many partitions and how much space do i leave for each of the partition????
I have a 80 gb hard drive..... :)

---

### Post by BurKaBU on 2008-02-25
> **oedha said:**
> before resize the partition
for your ps, yes you can......but if your windows crash..?
basically if you just pull 15Gb for ext3 and swap....no problem at all
since windows partition can be read/write from linux

Well knock on wood but my windows have been real stable the last year :)
So Ill just make the partitions
85gb ntfs For windows and stuff, 15gb ext3 then? =)

---

### Post by oedha on 2008-02-25
> **10Digits said:**
>  what if **_i want to install ONLY Ubuntu_**????
I have a 80 gb hard drive..... :)

hi there......i will...
ext3, 10Gb for linux
ext3, the rest for /home
swap , 1-2 gb

---

### Post by housam on 2008-02-25
- First of all you have to back-up your data - just in case.
- Do defrage your HDD 2-3 times and notice the position of the green sector ( windows file system ) . let say at 40% from the left side.
- This means that you cann't resize windows partition to less than that size of the HDD or you'll damage it.
- Use Gparted tool ( on the live CD ) to do the partitioning task.

---

### Post by oedha on 2008-02-25
> **BurKaBU said:**
> Well knock on wood but my windows have been real stable the last year :)
So Ill just make the partitions
85gb ntfs For windows and stuff, 15gb ext3 then? =)

yes you can do that......for 15 = 14 +1 
dont forget to defrag.....before....:)

---

### Post by 10Digits on 2008-02-25
Thanx a lot Oedha....
I didn't expect a reply within 30 minutes!!!!!

U r the greatest.....

---

### Post by oedha on 2008-02-25
> **10Digits said:**
> Thanx a lot Oedha....
I didn't expect a reply within 30 minutes!!!!!

U r the greatest.....
you're welcome....
really......i just finished my lunch :)

---

