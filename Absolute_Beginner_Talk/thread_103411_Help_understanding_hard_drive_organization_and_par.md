---
title: "Help understanding hard drive organization and partitioning"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by CanadaGradeEh on 2005-12-14
I know this may be in the wrong forum, but I decided to post here anyway considering I may have a few Linux/Ubuntu related questions that could stem from a little question and answer, so here I go:

Now I know what a partition is: a space on your hard drive saved for a particular function - an example would be this very operating system. I've set aside so-and-so ammount to be used only for one purpose, and anything done on that partition will be limited to it's given ammount of space. What I'm confused about is how I could go about monitoring all my partitions, the space they take up, and how I can alter and create more partitions for what I need. Also, I don't know the difference between partition types such as fat32, NFTS, and ext3. I'm not even sure how much space is set aside for the Ubuntu partition I made, or what kind of partition it is!

I've heard of programs that can help monitoring or creating partitions, like Partition Magic, but I'd just like to make sure I know what is what before I jump into something.

Thank you for your help if you decide to post!

---

### Post by darth_vector on 2005-12-14
there are probably nicer ways of finding out this information, but doing a

cat /proc/mounts

will tell you what partitions you have, what size they are and what filesystem they use.

the fat32, ntfs, ext3 and so on are different filesystems. have a read of this: [http://en.wikipedia.org/wiki/Filesystem](http://en.wikipedia.org/wiki/Filesystem)

---

### Post by linbetwin on 2005-12-14
You can see all your partitions in System -> Administration -> Disks.

FAT12, FAT16, FAT32 and NTFS are Windows filesystems, NTFS being the newest and safest. Linux systems can write to or delete files from FAT partitions, but they cannot do that safely on NTFS partitions (but it's safe to read from them).

ext2, ext3, reiserfs... etc. are Linux filesystems. If you did a standard installation of Ubuntu, you have an ext3 filesystem.

---

### Post by CanadaGradeEh on 2005-12-14
Thanks for the help, lin. I'm guessing that for most stuff that I might want to do with Linux in the future I should use ext3?

Anyway, like I asked before, is there a program that I could use to maybe monitor and observe my partitions with more detail? I'd like to be able to adjust the size of my partitions if possible, and also would like to know how I can use my swap space. If I'm correct the swap space is a partition that you can use to transfer data from one OS to the other? It makes sense, but I really have no idea.

---

### Post by linbetwin on 2005-12-14
No, no, no! Swap is virtual memory. You can't use it, your computer does. When you run out of RAM, your computer uses the swap partition as virtual RAM. In Windows it's called pagefile.sys and it's a hidden file on the partition where Windows is installed. It's not a separate partition as in Linux, although some people think it's better to move pagefile.sys to a different partition.

---

### Post by CanadaGradeEh on 2005-12-14
Ah, ok! Thank you very much. So I'm always up for info on that program... :p

But anyway, another question then: I'm guessing not - but is there anyway I could access files that are on my Windows partition from my Ubuntu partition? 
Is there a way I could make a partition for files I wanted to share between the two OS's and just plop them in there?

I'm also wondering about this other hard drive. My smaller hard drive still has windows XP installed on it so I was wondering how I can format it. I can't access it using my current motherboard. Atleast I don't know how.

---

### Post by alamba on 2005-12-14
Easiest way I figured of doing what you're asking is by keeping all my files in a 3rd partition that is FAT32 formatted. Windoze can read and write to it and so can ubuntu. You will need to mount it though.

Akshay

---

### Post by BatsotO on 2005-12-14
[QUOTE=CanadaGradeEh]
I'm also wondering about this other hard drive. My smaller hard drive still has windows XP installed on it so I was wondering how I can format it. I can't access it using my current motherboard. Atleast I don't know how.[/QUOTE]

was it even detected by bios?

---

### Post by CanadaGradeEh on 2005-12-14
BatsotO - I don't think it was, so that's why I was wondering how I can format it.

alamba - So do you mean like, one partition I'll have all my system files for Ubuntu, one partition I'll have all my system files for Windows, and then I'll have a third partition (lets just say in the middle) where I would have all my music, videos, pictures, documents, and games that I would want to share between the two operating systems? If so, then I'll ask more after an answer.

---

