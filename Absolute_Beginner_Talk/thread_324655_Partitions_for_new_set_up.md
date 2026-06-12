---
title: "Partitions for new set up"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2006-12-24
I have used Windows since 3.1 and currently XPPro.

Now is the time to look elsewhere, and I have been reading a book entitled Beginning Ubuntu Linux by Keir Thomas.

I have 2 questions, but I've started another thread for the other.

I would prefer to install my new Ubuntu Linux on a new HD. I have a new SATA Drive ready, as yet unpartitioned, and I have 2 other HDs (one IDE and one SATA).  Both of these HDs and fully partitioned (mostly NTFS) although one partition (28G) is virtually empty.

When I start the install will I be given the choice to put the Linux entirely on the new unpartitioned drive, or will it try to reduce the 28G nearly empty partition and try to install there first?

Do I need to do anything with the new HD first?

Thanks for any help,
David

---

### Post by spockrock on 2006-12-24
no just leave the new hd as is, and in the install process it will see the sata drive, and if you want just tell it to delete that drive, and install, on that drive (either through the automated or the manual way), make sure you know, what each drive is, ie by model number as harddrive and partition labeling is different then windows.

---

### Post by housam on 2006-12-24
I prefer to manage your partitions before installing. i.e. to install ubuntu you need 3 partitions: ' / ' , 'swap' and '/home'. Create them first ( prefer using Gparted partitioning tool)and during installation you can asign them manualy when it comes to partitioning.

---

### Post by spockrock on 2006-12-24
> **housam said:**
> I prefer to manage your partitions before installing. i.e. to install ubuntu you need 3 partitions: ' / ' , 'swap' and '/home'. Create them first ( prefer using Gparted partitioning tool)and during installation you can asign them manualy when it comes to partitioning.

the /home isn't necessary but I would say its one of those things I would never dream of not doing.

---

### Post by peterj on 2006-12-24
Ah but for the beginners out there...! I tried a few partition set-ups after doing a lot of reading up and in the end I resorted to / and /swap.. anything else just caused me problems. I haven't noticed the difference either!

---

### Post by Malta paul on 2006-12-24
Hi, May I suggest that you first check that your BIOS detects all your SATA & IDE HD's,
Then follow the advice from Spockrock. Good luck :)

---

### Post by housam on 2006-12-24
You just need to creat /home to put your files away from the root partition. or you have to make it big as much as you can. working with media files need a lot of space and you don't want to throtle your system.

---

### Post by louieb on 2006-12-24
Fedora 5 was the first Linux I installed. That was in April, 2006. I was so paranoid about messing up my widows install that I backed up what I thought was important on the data drive and unplugged  the windows    drive. I to have used Win3.1 and have learned what to do and not to do by trying stuff just to see what works and what doesn't.  
The Ubuntu Live CD installer works well but you need to choose the manual partitioning option if you want something other that the basic two partition (/ and swap) scheme. The good thing about it is you can see just what it will do before and where it will do it before anything is written to disk.  
I used my old P3 to try different Linux distributions so I partitioned its 40 gig drive into a bunch of 5 gig partitions and that works well for that. 
But to answer your question the installer should give you the option to install on your new 160 gig sata drive.   Just try it and see what happens.

---

### Post by David Floyd on 2006-12-24
Thank you very much for all of your replies.

I am going to be busy with Family Christmas matters for a few days, but I will attempt my new Ubuntu install in the new year.

Thanks
David

---

