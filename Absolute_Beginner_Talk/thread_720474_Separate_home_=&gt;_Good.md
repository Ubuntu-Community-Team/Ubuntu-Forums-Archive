---
title: "Separate /home =&gt; Good?"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by sayakb on 2008-03-10
Hello, I have an internal and an external HDD for my laptop (see specs below).
While installing Gutsy, I didn't make separate partitions for any of /etc or /home.. It automatically set up a / partition and a 4.8GB Swap. Would there be any performance improvements if I had separate partitions for them?

---

### Post by NightwishFan on 2008-03-10
I suppose only if the files on them fit the criteria for another filesystem. Otherwise I would think no.

I believe it is reiserfs that is good for moving multitudes of small files at a good rate, as an example.

---

### Post by sayakb on 2008-03-10
> **NightwishFan said:**
> I suppose only if the files on them fit the criteria for another filesystem. Otherwise I would think no.

I believe it is reiserfs that is good for moving multitudes of small files at a good rate, as an example.

So there might be no actual requirement of reformatting my hard-drive and create separate partitions.
Also, I agree that any file transfer on my internal HDD is instant, no matter how big is the file.. and that wouldn't happen on separate partitions..

---

### Post by NightwishFan on 2008-03-10
I am no expert but partitioning for speed only makes sense (as far as I know) for fragmentation or utilizing an advantageous file system for the situation. So I would assume you are correct. Please feel free to say something mean if someone more experienced comes along and proves me wrong. :)

---

### Post by sayakb on 2008-03-10
> **NightwishFan said:**
> I am no expert but partitioning for speed only makes sense (as far as I know) for fragmentation or utilizing an advantageous file system for the situation. So I would assume you are correct. Please feel free to say something mean if someone more experienced comes along and proves me wrong. :)

Right. Thanks. Looks like I don't have to worry about downloading my packages again (I somehow deleted all of the existing ones from /var/cache/apt/archives)

---

### Post by Oldsoldier2003 on 2008-03-10
> **LinuxIsInnovation said:**
> Hello, I have an internal and an external HDD for my laptop (see specs below).
While installing Gutsy, I didn't make separate partitions for any of /etc or /home.. It automatically set up a / partition and a 4.8GB Swap. Would there be any performance improvements if I had separate partitions for them?

having a separate /home partition is mainly a very nice way to do a clean install of the OS without losing your existing data and preferences.

---

### Post by sayakb on 2008-03-10
> **Oldsoldier2003 said:**
> having a separate /home partition is mainly a very nice way to do a clean install of the OS without losing your existing data and preferences.

Well, thats true. But I do have the external HDD for that reason :D
My /home has nothing significant other than some Movies.. :)

---

### Post by wolfen69 on 2008-03-10
> Well, thats true. But I do have the external HDD for that reason 
as do i. the best policy is to have data kept on a seperate hard drive, in my opinion.

---

### Post by sayakb on 2008-03-10
> **wolfen69 said:**
> as do i. the best policy is to have data kept on a seperate hard drive, in my opinion.

So how do I proceed with that? Can I do that w/o formatting? Or do I have to start w/ a clean install?

---

### Post by Oldsoldier2003 on 2008-03-10
> **wolfen69 said:**
> as do i. the best policy is to have data kept on a seperate hard drive, in my opinion.
agreed. my /home resides on a separate drive just for that reason. of course if that hdd fails i'll still have to resort to restoring a backup but hey thats all part of the game :)

---

### Post by forrestcupp on 2008-03-10
As stated earlier, the main reason for a separate /home partition is so you can keep all of your settings and files when you reinstall the OS.  That is one extra partition that is good to have, but if you didn't do it, it's not that big of a deal.

As for performance issues, the only way it would boost performance is if it is actually on a separate hard drive.  If it is a different partition on the same hard drive, it won't affect performance at all.  But the point is if you have it on a totally separate hard drive, you have two separate read/write heads accessing data instead of just one head having to move back and forth over the whole platter.

---

### Post by sayakb on 2008-03-10
> **forrestcupp said:**
> As stated earlier, the main reason for a separate /home partition is so you can keep all of your settings and files when you reinstall the OS.  That is one extra partition that is good to have, but if you didn't do it, it's not that big of a deal.

As for performance issues, the only way it would boost performance is if it is actually on a separate hard drive.  If it is a different partition on the same hard drive, it won't affect performance at all.  But the point is if you have it on a totally separate hard drive, you have two separate read/write heads accessing data instead of just one head having to move back and forth over the whole platter.

I don't really know the picture with ext3, but with ntfs, a file transfer across partitions or disks were slower than on the same partition. So no matter if I moved them over partitions and/or disks, they were slow. Is that a special offer NTFS provides ;) or is it the same with ext3?

---

### Post by NightwishFan on 2008-03-10
A new feature in hardy is when you transfer files it will give you the rate of transfer. If i ever write between partitions ill see if its as fast as same disk. I would assume the difference would be marginal.

---

