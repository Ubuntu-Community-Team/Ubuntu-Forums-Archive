---
title: "can i install ubuntu on a fat 32 partition?"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by cpu_medic on 2008-03-03
ok heres the issue. i have tried for 3 days to install ubuntu on my desktop. i have gotten very frustrated. i have decided to reformat the ubuntu drive to be fat 32 because windows will see it. that way i can install ubuntu; put the damn envy package in the drive from windows, and then run it in a console. if i have calculated all that correctly... i will be able to see the damn gui. and my video card will have no more problems. if this works im going to buy a cigar, (even though i dont smoke) so i can celibrate! does anyone see anything wrong with my reasonings? if so please tell me before i install ubuntu and get burnt...again

---

### Post by iSplicer on 2008-03-03
Last time I checked, Ubuntu can read and write to NTFS partitions so you could transfer files that way.

And I think Linux always uses ext3, not FAT32

---

### Post by jrusso2 on 2008-03-03
No you can't install it on a fat 32 partition as this is not a Linux filesystem.  You can use it to store files on a fat 32 partition if that is what you want to do.

The title of your post seems different then the text of you post so not sure exactly what you mean

---

### Post by incen on 2008-03-03
I sort of had this idea before: to install Ubuntu on Fat32 (of course, the filesystem). But then I did not since I didn't think it might work. :p

---

### Post by mikewhatever on 2008-03-03
> **cpu_medic said:**
> ok heres the issue. i have tried for 3 days to install ubuntu on my desktop. i have gotten very frustrated. i have decided to reformat the ubuntu drive to be fat 32 because windows will see it. that way i can install ubuntu; put the damn envy package in the drive from windows, and then run it in a console. if i have calculated all that correctly... i will be able to see the damn gui. and my video card will have no more problems. if this works im going to buy a cigar, (even though i dont smoke) so i can celibrate! does anyone see anything wrong with my reasonings? if so please tell me before i install ubuntu and get burnt...again

Yes, your damn reasoning is damn wrong.
1. You can't install Ubuntu on FAT32.
2. Windows can read and write ext3 with fs-driver [http://www.fs-driver.org/](http://www.fs-driver.org/).
3. Envy will have quite a few dependencies, so you'll need internet connection to download them.
4. Once installed, envy can be used to download and install ati/nvidia graphics driver, but it would be useless without internet connection.

---

