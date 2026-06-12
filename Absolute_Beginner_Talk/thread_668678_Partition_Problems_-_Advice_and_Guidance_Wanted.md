---
title: "Partition Problems - Advice and Guidance Wanted"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by poetmayhem43 on 2008-01-15
Hi all,

I've messed up my Ubuntu installation and want to wipe it and start again.  

Initially I started with 7.04 as a dual boot with XP.  Then I broke Ubuntu.  :oops: 
Rather than fix the problem I then installed 7.10 which the somehow ended up as a triple boot between windows, the broken 7.04 and 7.10.  

To make matters a bit more interesting I then fiddled with the partitions as hda7 where 7.10 installed was too small for me.  This is where the madness stopped as the hda7 wouldn't get any bigger & I stopped my XP partition working in the process (boohoo)

Anyway... sob story over.  What I want to do is put a clean install of 7.10, I don't want to lose my users or documents & settings.    

Can someone give me clear (*read idiotproof) instructions on how to copy the settings to an external drive and then import them back in once the fresh installation is complete.  
I'd also like to set the users, docs & settings on a separate /home partition for the future, but am a bit unclear how to do this (especially after the mess I caused with my last tinkering).  

Thanks all,

---

### Post by logos34 on 2008-01-15
you should try to transfer home to a separate partition first, then reinstall:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by crjackson on 2008-01-15
Here's what I try, but it's not 100% guarantee.

Copy the /home folder to a different drive.  This should save all your documents and settings.

Download and burn to CD PartEd (Partition Editor) ISO - You can google it.

Boot the PartEd CD.  Blow away (delete) all partitions except your Win-NTFS partition.  Leave everything else un-partitioned & un-formatted.

Shut down and reboot to the Gutsy 7.10 Live CD.  Then do the normal install process.  When you get to the partition section, select Guided - "Largest Free Space"

Once install is complete, copy the Backed-up Home folder to the freshly installed /home folder.

---

### Post by poetmayhem43 on 2008-01-15
Thanks, I'll have a good read of psychocat's instructions and then start hitting buttons.  

Before I do it how do I backup my installation to my external drive?  
I'd imagine it would just be copy it over, but not sure on the terminal commands to get it to do so.  (Drag & drop just tells me I don't have permission to copy some files even when running as root).  

If I have any questions over how various terminal commands work & why is it alright if I post them up and ask?

---

