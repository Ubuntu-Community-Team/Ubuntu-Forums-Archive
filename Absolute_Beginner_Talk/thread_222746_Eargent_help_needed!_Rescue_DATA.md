---
title: "Eargent help needed! Rescue DATA"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by vasurg on 2006-07-25
Now I have problems need eargent help. I lost my DATA.
I installed a 2nd HD before I try to install Ubuntu. I made 4 partitions (1NTSF, 3 Fat 32)on it and transfered (from the old HD with winXP on it)my data of work to one partition(NTSF) and personal data to another(FAT 32). After that, I deleted one partition from the old HD by partition magic (it had 3, 1 is made by DELL, 2nd one is NTFS with winXP, 3rd one is the one I used to store my DATA, So I deleted the 3rd one). Then, I run the Ubuntu 6.06 LTS (BTW, is this the same one as Daper people taling about?) live CD and try to install on the old HD. However, it was not succesful. I assigned 2 partitions for Ubuntu (one ext3, one for wrap). It give me erra when trying to format ext3 partition I guess. 
Anyway, my real problem now is after doing that, I lost my personal data on Fat 32 partition, HD2. Do you know is there any way I can get them back? It's very very important to me. And, where did i do wrong?
Thanks a lot!

---

### Post by x64Jimbo on 2006-07-25
It's not really apparent from what you've said exactly what went wrong, so let's try to figure it out. How did you do the copying? How did you do the partitioning? What were the error messages you've seen so far? Are the partitions gone, or just the data?

---

### Post by vasurg on 2006-07-25
I used Ctrl X and Ctrl V to move my files. And, I checked after I moved them. They were fine.
I partitioned the drive during i installing Ubuntu. I choosed "manually edit partition table" option. After I set the table (37gb for ext3, 3gb for linux-swab" then I went to next page, set the mounting place (for /; swab; and I think I choose the drive my data  lost as /home), and next, It showed me ready to install screan. I hit install. Then it stoped at the middle of " creating ext3 file...", about 15% of the process. A erro message poped up, I can't remember what it says though. 
The partition where I had my dat is still there and I can access it under windows XP.
thanks,

---

### Post by x64Jimbo on 2006-07-25
Yeah, that was the problem. by specifying that you wanted your /home partition to be the one where you saved your data, the installer reformatted the partiton that you stored your data on. This is what happens when you install any OS, Linux included. You may still be able to rescue some of your data. Look into the systemrescuecd.
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by vasurg on 2006-07-25
I had looked that web page before i posted here. But i can't figure out how to do the rescue. thanks, anyway. ](*,)

---

### Post by x64Jimbo on 2006-07-25
You need to download the ISO and then burn it to a CD the same way you did with your Ubuntu disc. Then boot it and follow their manuals.

---

### Post by vasurg on 2006-07-25
Ok, I will try that. One more question, If i want mount a partition but don't want it be formatted (that's what I wanted to do for that partition), what should I do?

---

### Post by kinematic on 2006-07-25
you can't mount a partition without formatting it...there has to be a filesystem on it in order for an operating sytem to recognize it(or else it's not even a partition)....otherwise it's just free space not being used.

---

### Post by vasurg on 2006-07-25
After reading the manuals of Sysresccd, I still have no idea how to find my lost data. Is there anyone can give detailed steps I can follow?

---

