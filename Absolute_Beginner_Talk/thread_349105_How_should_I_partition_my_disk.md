---
title: "How should I partition my disk?"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by ninepound on 2007-01-29
Okay. After considerable trouble with dual-booting with Ubuntu (it wasn't Ubuntu's fault, it was my own) and 2 replacement Windows CDs setting me back $60 (thank god Ubuntu is free), I've finally decided to swallow my pride and ask someone.


How should I partition my disk?

I'm currently wanting to dual-boot with XP and Ubuntu on my laptop. It's got a 30GB hard drive, and after multiple size configurations I'm still unhappy. I'm not planning on using it for serious gaming or work, just a leisure computer to browse the interwebs and mess with Physics demos. Any ideas?

---

### Post by mhl12 on 2007-01-29
this walkthrough really helped me out: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

They use the alternate install cd but the instructions should basically be the same.

If you want to divide you drive in half, just enter 15 GB (assuming you have that much space free)

---

### Post by ComplexNumber on 2007-01-29
> **ninepound said:**
> Okay. After considerable trouble with dual-booting with Ubuntu (it wasn't Ubuntu's fault, it was my own) and 2 replacement Windows CDs setting me back $60 (thank god Ubuntu is free), I've finally decided to swallow my pride and ask someone.


How should I partition my disk?

I'm currently wanting to dual-boot with XP and Ubuntu on my laptop. It's got a 30GB hard drive, and after multiple size configurations I'm still unhappy. I'm not planning on using it for serious gaming or work, just a leisure computer to browse the interwebs and mess with Physics demos. Any ideas?
you say that you have a 30GB HD. how much are you going to set aside for linux?


i would suggest that you assign about 10GB(this is more than enough for what you need. i have the whole of office and visual studio on mine, and they are hefty packages. i'm still only using 4.7 GB)  to windows and 20GB to linux. then that 20GB can be partitioned into the following:

----10 GB for your /home directory. this can then act as a permanent storage area that wont be touched if you ever have to reinstall windows or linux. you can keep all you docs and mp3 there etc..
----9GB for your root partition (ie '/'). i have everything that i need installed, and that takes up 7GB. i doubt that you will ever need more than 9GB
-----1GB for swap space.

---

### Post by ninepound on 2007-01-29
> **mhl12 said:**
> this walkthrough really helped me out: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

They use the alternate install cd but the instructions should basically be the same.

If you want to divide you drive in half, just enter 15 GB (assuming you have that much space free)

I think I should reword my question. I know how *to* partition my disk, I just want to know how I *should* partition my disk. AKA How much space I should devote to each system. Thanks and sorry for the confusion.

---

### Post by ninepound on 2007-01-29
> **ComplexNumber said:**
> you say that you have a 30GB HD. how much are you going to set aside for linux?


i would suggest that you assign about 10GB(this is more than enough for what you need. i have the whole of office and visual studio on mine, and they are hefty packages. i'm still only using 4.7 GB)  to windows and 20GB to linux. then that 20GB can be partitioned into the following:

----10 GB for your /home directory. this can then act as a permanent storage area that wont be touched if you ever have to reinstall windows or linux. you can keep all you docs and mp3 there etc..
----9GB for your root partition (ie '/'). i have everything that i need installed, and that takes up 7GB. i doubt that you will ever need more than 9GB
-----1GB for swap space.

Ah. Thanks very much. I'll try that out.

Will the /home directory be accessible by Windows? AKA Is that where I should store my windows application data (program files, etc.) or should all that be stored in the 10 GB windows partition?

---

### Post by ComplexNumber on 2007-01-29
> **ninepound said:**
> Ah. Thanks very much. I'll try that out.

Will the /home directory be accessible by Windows? AKA Is that where I should store my windows application data (program files, etc.) or should all that be stored in the 10 GB windows partition?
apparently, there is some 3rd party software that will allow the user to access linux from windows, but i don't know much about it.
i suggest that you install all your data and docs in your linux /home partition.  it works out MUCH more convenient that way. if you store your docs on windows, there is always the chance that your docs will be lost if windows messes up severely (of course, you can just boot into linux and retrieve your docs from windows that way, but still).

---

### Post by ninepound on 2007-01-29
> **ComplexNumber said:**
> apparently, there is some 3rd party software that will allow the user to access linux from windows, but i don't know much about it.
i suggest that you install all your data and docs in your linux /home partition.  it works out MUCH more convenient that way. if you store your docs on windows, there is always the chance that your docs will be lost if windows messes up severely (of course, you can just boot into linux and retrieve your docs from windows that way, but still).

Okay. And just one last question.

What file system should all of these be? Obviously the Windows 10GB is NTFS, and I believe the 9GB for Linux is FAT32, but i'm not sure.

---

### Post by ComplexNumber on 2007-01-29
> **ninepound said:**
> Okay. And just one last question.

What file system should all of these be? Obviously the Windows 10GB is NTFS, and I believe the 9GB for Linux is FAT32, but i'm not sure.
make it ext3 for root and /home, and swap for swap space. FAT is a microsoft filesystem.

---

### Post by ninepound on 2007-01-29
> **ComplexNumber said:**
> make it ext3 for root and /home, and swap for swap space. FAT is a microsoft filesystem.

Home, root, and swap are all ext3? And I assume ext3 is something done with the gnome partition editor?

---

### Post by Happy_Man on 2007-01-29
What about [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)? That's a really good site for the "how" part. As for the driver to access windows from linux, ntfs-3g is great. Just search for it here on the forums. Hope this helps!

---

### Post by Buck2348 on 2007-01-29
> **ninepound said:**
> Will the /home directory be accessible by Windows? AKA Is that where I should store my windows application data (program files, etc.) or should all that be stored in the 10 GB windows partition?
A small piece of software for Windows called FS-Driver can make your Linux partitions accessible from Windows.  I think you already see that that  would not be a good place to put Windows programs.  /home, as has been said, is the place to put your personal and data files, so that if necessary you can reinstall the system without disturbing them.

Buck

---

