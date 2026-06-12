---
title: "Emergency!!!!please Help!"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by noodles12 on 2006-07-31
Ubuntu kept stalling at my mount root filesystem part so i decided to install kubuntu over it. I did the installation and formatting directly over where ubuntu used to be (sda4). This did not fix the problem, but when i restarted windows, my documents partition (sda5) was no longer recognized by windows!!!!!!! how do i get this back it has all my important documents on that!!!

---

### Post by T700 on 2006-07-31
1.  I know you're upset, but a clear, descriptive, subject line will get more eyeballs on your question.

2.  sda5; was this a Windows partition?  Is this a dual boot setup?

3.  Please tell me you backed up your data.  Anytime you start formatting and reinstalling things, you risk the loss of all your data.

Paul

---

### Post by Tomosaur on 2006-07-31
That depends on whether you accidentally installed over the partition or whether you just inadvertantly messed up your MBR :S

If you have a windows recovery CD handy, use that to fix your MBR, and hopefully get your stuff back. If you don't have one, make one from within windows. I can't remember exactly how to personally, but google should be able to help you.

Good luck :S

---

### Post by TripleE on 2006-07-31
> **noodles12 said:**
> Ubuntu kept stalling at my mount root filesystem part so i decided to install kubuntu over it. I did the installation and formatting directly over where ubuntu used to be (sda4). This did not fix the problem, but when i restarted windows, my documents partition (sda5) was no longer recognized by windows!!!!!!! how do i get this back it has all my important documents on that!!!



Is the sda5 partition showing as a drive letter in Windows and what version of windows are you running?

---

### Post by noodles12 on 2006-07-31
Sorry for being unclear i kind of paniced. I ended up loading the knoppix live cd and got some of the files i needed from sda5 so that means the partition wasn't formatted over, it just wasn't recognized by windows anymore. 

sda1  = ntfs windows partition
sda2  = extended file
sda3  = swap file for linux
sda4  = linux partition
sda5  = ntfs document partition for "My Documents"

What happened was that when i went into my computer in windows xp pro sp2, c: was recognized but F: ( my documents) wasn't shown anymore. 

I was wondering how would i go about having windows recognize this ntfs partition again.

---

