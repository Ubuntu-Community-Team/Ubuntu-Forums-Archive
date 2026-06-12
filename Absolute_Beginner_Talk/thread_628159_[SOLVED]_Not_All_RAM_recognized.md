---
title: "[SOLVED] Not All RAM recognized"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by lentomies on 2007-11-30
Hello,

I have a machine that started out with 2GB RAM. I bought 2 sticks of G Skill and since they worked perfectly I added another 2 sticks.


The BIOS sees all 4 GB BUT both Windows XP SP2 AND Ubuntu 7.10 see only 3.2 GB...

Why is this?

Thank you!

---

### Post by Fred_E _krugar on 2007-11-30
if you are running the 32bit system that is all the OS can physically use.

Due to the bus width

---

### Post by tnseditor on 2007-11-30
32 bit of any operating system including Windows and Linux will not recognize the full amount of RAM.  If you have a 64 bit processor and motherboard, etc., then try the 64 bit edition of Ubuntu.  It should recognize all of it.

---

### Post by lentomies on 2007-11-30
I have an Intel Core 2 Duo E4500 and motherboard is Intel DQ965GF.

How would I tell if they support 64 Bit?

---

### Post by PmDematagoda on 2007-11-30
Your system should be able to support 64 bit, my 2 year old Prescott P4 processor does, so the Dual Core systems should work with 64 bit.

---

### Post by tnseditor on 2007-11-30
All Core 2s are 64 bit.  You will be fine with 64 bit.

---

### Post by lentomies on 2007-11-30
Thanks for the confirmation all but how about the motherboard. ???? is the Intel DQ965GF ok?

---

### Post by PmDematagoda on 2007-11-30
Your motherboard should also be all right with it.

---

### Post by jcsteele on 2007-11-30
since your CPU's are 64bit, yes...go ahead and download the 64 bit version and give it a whirl.

//jcs

---

### Post by lentomies on 2007-12-01
Thank you everyone for your help and answers to my questions.

If / When I upgrade...... Will the 64 bit version then save all my settings from the 32 bit version?
I'm talking about email and book marks etc......

Also, do I need to reformat my Hard disk drive? Does something here need to be done...

Thanks once again!

---

### Post by jcsteele on 2007-12-01
You would be advised to make some backups...your bookmarks can easily be saved through firefox's "export" feature in the  bookmarks page.  I would make a backup of everything you can that you REALLY need.....

If you use the guided partitioning (recommended) your hard drive will indeed be erased.

//jcs

---

### Post by Paulmd on 2007-12-01
> **lentomies said:**
> Hello,

I have a machine that started out with 2GB RAM. I bought 2 sticks of G Skill and since they worked perfectly I added another 2 sticks.


The BIOS sees all 4 GB BUT both Windows XP SP2 AND Ubuntu 7.10 see only 3.2 GB...

Why is this?

Thank you!

Others have told you the correct answer, But there's a better description here: (it also applies to win2k and XP, and Ubuntu as well)

[http://support.microsoft.com/kb/929605](http://support.microsoft.com/kb/929605)

To overcome the limit, you can install the 64-bit versions of the respective OSes. Although... It would be preferable ti Install 64 bit Vista instead of 64 bit XP, as the 64 bit version of XP is much less supported than 64 bit Vista.

---

### Post by jcsteele on 2007-12-01
Actually, it would preferable to install 64 bit ubuntu and NOT another bloated microsoft product that took 6 years to develop and still has many design flaws and bugs.  :-)

//jcs

---

### Post by Paulmd on 2007-12-01
> **jcsteele said:**
> Actually, it would preferable to install 64 bit ubuntu and NOT another bloated microsoft product that took 6 years to develop and still has many design flaws and bugs.  :-)

//jcs

Well, he's dual booting. There's usually a good reason for that. He needs windows for something. 

Im just suggesting that the setup would be better with 64bit vista/64bit Ubuntu as opposed to 64bit xp/64 bit Ubuntu. 64bit XP is... a bit of a problem child.

And don't pretend Ubuntu is bug free and perfectly designed either. :)

---

### Post by jcsteele on 2007-12-01
I was just being silly...

No, I dont pretend Ubuntu is bug free - and honestly I prefer to use a clean windows system in the short term for essential tasks like word processing, web browsing, etc.

However - 4-6 weeks after a clean windows installation everyone knows what happens - the file system starts slowing down, and problems ensue from everywhere

The ubuntu machine at 6 months is still the same way it was when it was first installed :)

Glad this problem is solved, if you feel it is, mark the thread as "SOLVED" in the thread tools.

//jcs

---

### Post by MozartlovesUbun2 on 2007-12-01
> **lentomies said:**
> I have an Intel Core 2 Duo E4500 and motherboard is Intel DQ965GF.

How would I tell if they support 64 Bit?

I didn't know it supported 64bit.

---

### Post by lentomies on 2007-12-01
Thanks once again for all the great insight.

Just to clarify..... I'm running 3 operating systems....

1. Ubuntu 7.10
2. Windows XP SP 2
3. Windows 2000 SP 4


Each OS is installed in it's own private mobile rack and needs a key in order to be turned on....

To date, this has been the ideal situation for me......

---

### Post by Paulmd on 2007-12-02
> **lentomies said:**
> Thanks once again for all the great insight.

Just to clarify..... I'm running 3 operating systems....

1. Ubuntu 7.10
2. Windows XP SP 2
3. Windows 2000 SP 4


Each OS is installed in it's own private mobile rack and needs a key in order to be turned on....

To date, this has been the ideal situation for me......

Out of curiosity, how much RAM does win2k say you have?

There aren't any workarounds for this situation beyond changing the OSes. (there is no 64 bit win2k, but the Advanced Sever version has support for 8GB RAM  anyhow)


[http://support.microsoft.com/kb/304297](http://support.microsoft.com/kb/304297)

---

### Post by lentomies on 2007-12-03
Hey PaulMD,

Windows 2000 Pro says I have 3,397,056 KB RAM.

---

