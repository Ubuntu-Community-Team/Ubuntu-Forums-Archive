---
title: "[SOLVED] please help me to &amp;quot;kill&amp;quot; my windows."
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by lover_of_sc on 2008-03-11
All,

Must say, finally a OS that actually works!! Never had patients to learn Linux before but I must say I love ubuntu.

Can someone help me, I still have windows vista installed on my computer (on NTFS format) - but I would like to gradually face it out. Can I somehow free up memory from my NTFS part and merge it with my linux drive? 

I would like to keep windows a little while in case I would for some strange reason need it... :-)

I have two 160gig harddrives in my laptop - but I only took 20 gig for my ubuntu installation.

---

### Post by Barrucadu on 2008-03-11
Boot the computer with the Ubuntu LiveCD (or the GParted LiveCD) and resize the Windows and Ubuntu partitions. Windows will run checkdisk when you next boot up, but that's just because Windows is awkward when it comes to partitions.

---

### Post by Oldsoldier2003 on 2008-03-11
> **Barrucadu said:**
> Boot the computer with the Ubuntu LiveCD (or the GParted LiveCD) and resize the Windows and Ubuntu partitions. Windows will run checkdisk when you next boot up, but that's just because Windows is awkward when it comes to partitions.

Best to boot into windows and defrag the windows partitions before resizing them. This makes it less likely that you'll wreck the installation, since the OP wants to keep it around for now.

---

### Post by scrooge_74 on 2008-03-11
second that, defrag first then rezise

---

### Post by Cerny on 2008-03-11
Agreed, last time i tried to re-partition I forgot to defrag... not the best choice to do.

---

### Post by justleen on 2008-03-11
i think the OP doenst want to resize..

Reading carefully, i read he already has Ubuntu installed, and wants to move the data?


I'd say, just keep it as is. Linux can perfectly well read NTFS, and all your data is accisble from linux. If you later decide to remove windows , you can simply copy data to a back up partition, reformat using ext3, copy the data back..

> 
- but I only took 20 gig for my ubuntu installation.


---

### Post by ugm6hr on 2008-03-11
Please note that the OP also mentions **Vista**.  This means that GParted should not be used to resize - it has to be done from within Vista.

@lover_of_sc:
You need to clarify exactly where your HD partitions are in relation to the 2 HDs.  i.e are both Ubuntu and Vista on the same HD?  Are there any other partitions on that HD?  What has the additional HD got to do with this situation?

PS: Perhaps a sensible solution is a separate /home partition?

---

### Post by lover_of_sc on 2008-03-11
I have two hard drives @150G each. 

sda1 - Windows vista (140G)
sda2 - Windows recovery (HP laptop) (10G)

sdb1 - Files etc in NTFS (130G)
sdb2 - Linux (at the end of the hard drive)

I can see the reason not to change it and leave it as I can reach the files in both OP:s now. I really don't use Windows vista for anything now, but it's mostly because I am curious of how it works - ie how to repartition/format in linux.

The long term solution is to move completely into ubuntu - I really don't like vista.

Thx everyone for your help - I hope I am clearer now. :-)

---

### Post by ugm6hr on 2008-03-12
You still haven't said which "Windows" partition you want to reduce and incorporate into Ubuntu, or how much of it.

Assuming you want to leave the Vista HD as is, and give the whole of the other HD to Ubuntu, I would suggest this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This will create a new /home partition (major benefit is you can reinstall without losinf files / settings)

Backup all the "Files" into the Vista partition (or elsewhere).
Use GParted to delete the partition, then create a new partition and format to ext3.
Then use the above tutorial from the "Using the new partition"

---

### Post by lover_of_sc on 2008-03-12
Sounds like a good idea, I shall give that one a try. :-)

Thank you for your help.

/Anders

---

### Post by matherians2 on 2008-03-12
If you want to get rid of windows, you could reinstall Ubuntu.  But this time use the entire hard drive.

---

