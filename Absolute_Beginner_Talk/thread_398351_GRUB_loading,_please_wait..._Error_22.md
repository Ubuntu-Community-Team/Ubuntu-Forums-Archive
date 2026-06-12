---
title: "GRUB loading, please wait... Error 22"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by hush on 2007-03-31
I installed Ubuntu Linux on my dual boot WinXP MCE laptop, it worked smoothly for a few months. I decided to remove Ubuntu from my laptop and put it on my desktop recently. I was using WinXP on my laptop and deleted the Ubuntu partition thinking that would erase it from my HDD and free up the space for my WinXP partition to use again. I guess I was wrong. Now, when I boot up my laptop I get this...

> GRUB Loading stage1.5.


GRUB loading, please wait. . . 
Error 22

I really hope I haven't ruined my WinXP partition, please tell me I haven't... I have way too much information on it that I can't afford to lose at this point in the semester. I will have lost all of my papers and computer programs/notes from all of my classes. :confused: 
Please help, any assistance you can give me will be greatly appreciated!

Thanks,
- hush

---

### Post by TonKi on 2007-03-31
Boot from your windows Cd into the recovery console and run fixmbr (afair)

The error is because grub is still written into your mbr but can't find the files/partition its looking for - so you need to write a new mbr

---

### Post by hush on 2007-04-02
Thank you so much! I was worried I had lost everything. 
Got it back up and running again.

Thanks again,
- hush

---

