---
title: "Triple Boot Installation Steps"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by Sleestack on 2007-09-25
I'm eagerly awaiting the arrival of my Dell Inspiron 531 with a 320GB drive and native Vista Home Premium install. Call me crazy...but I don't trust Vista and also want to use XP and Ubuntu in a triple-boot scenario. 

Since I have an opportunity to configure a brand new, clean machine with triple-boot I want to make sure I start this process right and avoid potential issues others may have experienced. This is what I'm thinking of doing: 

1. Vista: use the native Vista utility to re-size the Vista partition to 100MB. 

2. Use some sort of re-partitioning utility (suggestions, anyone?) and split the remaining 200MB into 100MB each. 

3. Install EasyBCD 

4. Install XP on one remaining partition. 

5. Install Ubuntu on the other remaining partition. 

6. Cross fingers and pray. 


Does this sound like a good step-by-step process? Can anyone recommend a good re-partitioning utility?


RESOLUTION!!!!!!!!!!!!!!!!!!!!!!!

For anyone else wondering, this is easier than I thought and I now successfully triple boot XP-Vista-Ubuntu. 

My machine came with Vista Home Premium edition installed. Total disk size is 320 gig. 

1. Install XP. I made a new partition using the usual XP installation routine and created a 60 gig partition for XP. Once that was done I immediately installed XP service pack 2 (SP2) although that may not be a necessary step. 

2. Install Vista. In the remaining partition I installed Vista using all available disk space. 

3. Install Ubuntu. In the Vista partition I created the partition for Ubuntu using the standard Ubuntu installation routine. Note: I only knew this was in fact the Vista partition due to the size of it; I'm not actually sure Ubuntu recognized the XP partition. 

4. Reboot. The Ubuntu GRUB loader will show only Ubuntu and Vista. Whoa, I'm screwed?! No, boot into Vista, then it will show the option to boot into Vista or XP. Phew! 

As of a few re-boots all seems to be well.

---

### Post by stevebakerj on 2007-09-25
As with all Win dual boots you should install the oldest (XP) first then Vista then *.nix

Gparted for re partitioning or use the *.nix Live CD

---

