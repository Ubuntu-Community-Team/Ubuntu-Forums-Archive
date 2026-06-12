---
title: "One last question before I install (dual booting)"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by dt19 on 2008-02-09
Right, I'm pretty sure I want to install Ubuntu now - I've tried out the Live CD and I'm impressed. I'm going to set up a dual boot for now, just whole I get used to it, and there's just one last question I have - if I change my mind after installing Ubuntu, if I want to go back to just windows, can I do that? Will having created partitions be an obstacle to this? 
Fingers crossed!

---

### Post by Paqman on 2008-02-09
Nope, you can delete partitions as easily as you can make them.

However, I suspect you won't delete Ubuntu ;)

---

### Post by Therion on 2008-02-09
Yes you can and no it won't.  You would use your Windows install to CD to recreate the MBR (which would remove GRUB and your option to dual-boot) and then use the Windows partitioning tool to remove the Linux partition/s.  

But trust me... You're going find yourself using Windows less and less.  And pretty soon, aaaaall that space being sucked up by that Windows partition is going to start looking pretty good.

Next thing you know, you're running Windows in Linux using Virtual Box... Then it's a short hop to saying your goodbye's to Windows forever.

---

### Post by Dabblo on 2008-02-09
How do I get rid of the windows partition to make it just one big partition for ubuntu? Any help would be appreciated here guys I'm new to this too, I don't want to take chances
 ;)

---

### Post by Paqman on 2008-02-09
> **Dabblo said:**
> How do I get rid of the windows partition to make it just one big partition for ubuntu? Any help would be appreciated here guys I'm new to this too, I don't want to take chances
 ;)

Open up Gparted and delete the Windows partition, then expand the other partition(s) to take up the space you've just created.

You can edit GRUB afterwards to no longer show Windows as an option, but it's not crucial

---

### Post by bumanie on 2008-02-09
Ubuntu needs a minimum of two partitions. One is for the / (root) file system and the other is for swap. It is also advisable to make a /home partition where everything gets stored, therefore if anything goes wrong with ubuntu (unlikely), you can just restore the file system to / wthout interfering with your saved documents etc.
I make a 19g partition for /. a 2g (double my physical ram) for swap and then as much as I wish for /home. The built in partitioner can do this during the install. Ensure you format the partitions for ubuntu to ext3.

---

### Post by jimmyjean on 2008-02-09
Have you already got ubuntu installed or not? If you haven't, when you come to install it you will be given the option to format your disk which will get rid of windows.

---

### Post by Therion on 2008-02-09
How would you go about *wiping* the Windows partition after you've installed Ubuntu?  Just to want to make sure I understand your question...

If it were me, personally, at that point I'd do a fresh install of Ubuntu and simply choose the option to use the entire drive when prompted about setting up the partitions.  HOWEVER, that's me.  I'm sure you could use gParted or Partition Magic to accomplish the same thing (e.g. reformatting the Windows partition and then merging that new partition with the existing Linux partitions).

Edit:  Assuming I understand your question correctly, **Paqman** pretty much nailed your answer.

---

### Post by mikewhatever on 2008-02-09
Here is a guide in case you decide to revert to Windows only [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm). Please read first, because it is not enough to remove the partition as Paqman wrongly suggested in post #2.

---

