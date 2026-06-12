---
title: "[SOLVED] Feisty -&amp;gt; Gutsy"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2007-11-06
I have installed Gutsy on my laptop and LOVE it! My question now is, I want to upgrade my Desktop (which has Feisty) to Gutsy. But I want to do a clean install AND save the three profiles on it currently. How can I do this? Do I just need to copy the /home directory to a thumb drive and copy it back? or what?

---

### Post by dpar on 2007-11-06
I'm not too sure about your question, but someone will know, for sure.
I just thought I'd mention that when you do the install, maybe make a seperate home partition. It will make clean installs a lot easier next time.:)

---

### Post by logos34 on 2007-11-06
I agree with dpar--[transfer your /home to a separate partition]("http://www.psychocats.net/ubuntu/separatehome").  Then do your fresh gutsy install over the old root.  Mount your separate home partition at '/home' but DO NOT FORMAT.

---

### Post by pizzipie on 2007-11-06
I recently updated my Dapper to Feisty ( four months ago ). To my amazement I didn't have to repartition the hard drive and go through the tedium of installing all my software again. In fact when it upgraded it put my old /home in a seperate partition. NOW I want to upgrade from Feisty to Gutsy. Since I don't know what happened last time I am afraid I will have to re-partition and lose everything I have. This seems to happen right in the middle of the install with no way back. Can anyone tell me what is going on and how to save all my software, settings etc. and still have an installation which gets rid of any "bad stuff" that has happened over time? 

Thanks R.

---

### Post by rudeboyskunk on 2007-11-06
One important thing to do before you try any of this is to back up your data!  USB flash drives, burned dvds, even floppy disks.  I can't tell you how many posts there are on this forum from people who attempted to do something like this without backing up their data, only to lose it all.

---

### Post by slughappy1 on 2007-11-06
What is the easiest way to backup my data?

---

### Post by rudeboyskunk on 2007-11-06
The part where I said "USB flash drives, burned dvds, even floppy disks" would be a good start.

Or you can make a separate partition and dump all of your personal stuff into that.  But be careful, as this might get overwritten in the install process.  Believe me, I know, it's happened to me.  I backup all my stuff on USB flash drives now.

---

### Post by crjackson on 2007-11-06
> **slughappy1 said:**
> What is the easiest way to backup my data?

A seperate hard drive is great.

---

### Post by pizzipie on 2007-11-06
What do you advise to backup.? I have a hard drive I can backup to.

---

### Post by slughappy1 on 2007-11-07
I guess I should actually ask what I meant to ask. What I meant to ask was if I copy my /home directory to some other media (DVD-R, flash drive, hdd, etc) and then make a new installation with the /home on a separate partition. Can I just copy the old /home to the new /home and all preferences will be the same? I'm just not sure since it is a newer OS and the information is from an older OS

---

