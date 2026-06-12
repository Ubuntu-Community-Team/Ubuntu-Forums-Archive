---
title: "Installation choices --bootable flag?"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by editrix on 2005-10-08
Hello all:

I'm trying to install Ubuntu 5.04 on a pre-partitioned hard drive. The first partition is Win98, the second has not been formatted at all.

I've gotten as far as [!} Partition disks where the partition settings for the unformatted partition read:

Use as: do not use
Bootable flag: off
Size 4.6GB

I assume the "Use as" should be changed to Ext3, but I have no idea what's meant by bootable flag.

Also, I'd like to know what happens past this stage. Will there be more choices I won't understand? I've seen the websites with screenshots, but they're either for XP or for a non-dual boot install.

Thanks.

---

### Post by Zelut on 2005-10-08
You will want that to be bootable, yes.  That'll make that partition bootable as well as your win98 partition.  If you dont set it as bootable it wont be able to startup.

Don't worry, the partitioner is the hardest part of the installation.  Everything else is a Breeze

---

### Post by editrix on 2005-10-08
Thanks, kuyaedz. Of course, I now have another question. I got as far as the actual partitioning, and was told:

*************
If you continue, the changes listed below will be written to the disks.

The partition tables of the following devices are changed:

IDE1 master (hda)

The following partitions are going to be formatted:

partition #2 of IDE master (hda) as ext3
*************
I do have a smiley and a lightning bolt of #2 partition--which I assume is good. But

1) I never got a screen that asked me about swap space.  Don't I need it? and 
2) I'm not sure how this is going to affect my Windows partition. Is the Win partition going to change? 

Is there a forum for pre-absolute beginners? :confused:

---

### Post by Zelut on 2005-10-08
lol I think we're in the forum for the newbies :)

If your win partition is on partition #1 then it shouldn't change, and the next option should give you the setup for swap space.

NOTE: without seeing the exact options I can't guarantee the accuracy but this is my best assumption from what I have.  If it does something please don't blame me :)

---

### Post by editrix on 2005-10-08
Thanks for the quick reply. I'm on dialup, so there's only so much time to get online for answers.

>If your win partition is on partition #1 then it shouldn't change, and the next option should give you the setup for swap space.

From what I can see, the next option is "If you continue, the changes listed below will be written to the disk." You mean the swap space comes after that? You partition the partition?

Sorry to be a pain, but paranoid people usually are.

---

### Post by Mustard on 2005-10-08
Did you choose default install at the start or expert install?

I'm pretty sure, you can choose to have Ubuntu automatically handle the partitioning in the default install.  It seems like you might require that option as your not sure of what options to choose atm.

---

### Post by editrix on 2005-10-08
Hi Mustard:

>Did you choose default install at the start or expert install?

Um, I thought default install wiped the entire HD. In fact, I don't recall anything that said "expert installl." Just "manually edit partition tables."

(Sorry, I know this quote is awkward. Still figuring out how this forum thingy works.)

---

