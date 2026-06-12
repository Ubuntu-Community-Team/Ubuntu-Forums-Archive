---
title: "Moving OS from one disk to another"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by thefoolisme on 2007-04-10
So, I have my dual-boot system up and running.  I've got XP one one partition and Ubuntu on the other half of the disk.  The other morning I booted up my system and received a warning from the S.M.A.R.T. drive application that my hard drive is failing.  I've ordered a new one, and will be installing it this week.  

Is there an easy way to copy the entire hard drive (all partitions with both OSs) to the new disk when it arrives?  I really don't want to have to spend days reinstalling XP and Ubuntu, and all the apps I have installed, especially since I seemed to have worked out the little kinks in Ubuntu.  For example, if I use Norton Ghost, will it ghost everything?  Or is there a better solution out there?  What's the best way to go about this?  

I will be moving it from one IDE HDD (80gb) to another IDE HDD (160GB).  Details in procedure are helpful.  :-)  Thanks in advance.

---

### Post by wpshooter on 2007-04-10
My first question would be exactly how do you know your drive was bad ? 

I would NOT trust S.M.A.R.T. as an absolute indication of a drive problem.

Did you get the hard drive manufacturer's diagnostic software and check to see if there was **REALLY** a mechanical and not software problem with your drive ?

---

### Post by Patrick-Ruff on 2007-04-10
I don't understand why people don't answer others questions from the get go and THEN start asking them stupid pointless questions that essentially don't help them (especially since this dude already bought another hard drive . . .) 

I'm pretty sure partition magic can do something like this.  if not, you can search for software like Norton Ghost.

---

### Post by thefoolisme on 2007-04-10
Yes, I've run various diagnostic software, including Western Digitals Tools, chkdsk, etc. Gparted also hiccupped the last time I installed Ubuntu, taking forever to read the disk info.  Now I know the reason why.  There are several bad sectors, and the drive is reading very slowly.  It's also about 4 years old and been worked like a dog, so it's not too surprising to me.  I've been through plenty of bad drives before.  This one is just going slowly for a change.

---

### Post by tombott on 2007-04-10
> **thefoolisme said:**
> So, I have my dual-boot system up and running.  I've got XP one one partition and Ubuntu on the other half of the disk.  The other morning I booted up my system and received a warning from the S.M.A.R.T. drive application that my hard drive is failing.  I've ordered a new one, and will be installing it this week.  

Is there an easy way to copy the entire hard drive (all partitions with both OSs) to the new disk when it arrives?  I really don't want to have to spend days reinstalling XP and Ubuntu, and all the apps I have installed, especially since I seemed to have worked out the little kinks in Ubuntu.  For example, if I use Norton Ghost, will it ghost everything?  Or is there a better solution out there?  What's the best way to go about this?  

I will be moving it from one IDE HDD (80gb) to another IDE HDD (160GB).  Details in procedure are helpful.  :-)  Thanks in advance.

To answer your question yes! Norton Ghost will do this for you
Once you have cloned your old HD to your New HD you may want to resize the partitions using Partion Manager.
Let me know if you need any help etc, I can recommend Hiren Boot CD for this task!

---

### Post by wpshooter on 2007-04-10
> **Patrick-Ruff said:**
> I don't understand why people don't answer others questions from the get go and THEN start asking them stupid pointless questions that essentially don't help them (especially since this dude already bought another hard drive . . .) 


Because he did not say and I don't know unless I ask.

---

### Post by thefoolisme on 2007-04-10
SO, if I use a program like Norton Ghost, and clone the hard drive, once that's done, I can take out the old hard drive, and it will boot up?  Or would I need a disk like the Norton boot disk, or some other to change HDD values/names?  It may sound like a silly question, but in the past, I've just reinstalled everything.  I just don't feel like doing that again.  

Thanks for your help.

---

### Post by tombott on 2007-04-10
> **thefoolisme said:**
> SO, if I use a program like Norton Ghost, and clone the hard drive, once that's done, I can take out the old hard drive, and it will boot up?  Or would I need a disk like the Norton boot disk, or some other to change HDD values/names?  It may sound like a silly question, but in the past, I've just reinstalled everything.  I just don't feel like doing that again.  

Thanks for your help.

Your Current HD is Prb set to MASTER, this is usually done with Jumpers on the HD itself or by the IDE cable.

When you install your 2nd HD set it to Slave and use a spare IDE connector on the IDE cable used by the CD-ROM if possible.

Once you have cloned your HD using Ghost remove your old HD and put your new HD in it's place and make sure the HD jumpers are set to MASTER

I hope that helps

---

### Post by thefoolisme on 2007-04-10
OK, so it is that easy.  Excellent!  I knew about the jumpers, etc. but thanks for the reminder.  I've just never ghosted before, other than backups for my "important PC", which fortunately I haven't had to restore yet.  I always like to try all the new stuff (like Ubuntu) on my "training PC", which is why it tends to get quite a workout.  :-)

---

