---
title: "New Partition Question"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by Dispatch on 2008-03-02
I decided I was going to Ubuntu on a different computer than I had planned.  The one I am switching too is just a little older.  It has a small, 20GB HDD with about 7GB of free space.  I want to make a 6GB partition for Ubuntu but it won't let me.  On the other computer during installation it let me choose the size of the partition(the recommended way to do it.)  Now the only options I get are to use the entire disk, most continuous free space, or do it manually.  What happened to the other option? :confused:

---

### Post by zetjee on 2008-03-02
It could be that the free space is to small, but i cant imagine. Try to run the LiveCD and start gparted. Maybe it let you there. 

If it lets you, than click the option to use that partition during the install.

---

### Post by neurostu on 2008-03-02
Does the computer with the 20gb HDD already have partitions on it?  Also what are you using to do the partitioning?  I would recommend downloading a GParted live cd and then using that to re-partition your HDD.  The version of GParted on the Ubuntu cd is good but I find the version that you download as a live cd to be much better.  Try that.

---

### Post by Dispatch on 2008-03-02
In gparted it shows my HDD and says it's size, but there are no numbers under used and unused and I still can't create a new partition.  Besides showing the HDD it shows unallocated space but... it's only 8MB.  What else can I try?

P.S. I love the quick answers, much appreciated! :)

EDIT:  Okay, I will try that Neuro.  I just don't get why it worked fine on the other computer I did it on but now I'm having issues.

---

### Post by Happy_Man on 2008-03-02
Hmmmm... could you perhaps take a screenshot of Gparted showing your configuration and post it here? I tend to understand stuff better when it's a picture. Sorry. :)

---

### Post by owbizi on 2008-03-02
It's normal to have 8mb of free space when coming from Windows. I did. :)

However, it means that all space of your HDD (excluding the 8mb one, hah) is for the Windows partition only. If that's not all occuped, you can resize it, and then create a new one for Ubuntu, all using gparted. But don't forget the swap one!

---

### Post by neurostu on 2008-03-02
The first thing you have to first "Resize" the partition, then using that new space create a new partition

---

### Post by Dispatch on 2008-03-02
[http://i63.photobucket.com/albums/h132/j18french/gparted.png](http://i63.photobucket.com/albums/h132/j18french/gparted.png)

That's the link to a screen shot of gparted showing what I was trying to explain.  Hope that helps :)

EDIT:  As of now, I will not let me resize and I know i have 7GB of free space as I checked in My Computer before I booted Ubuntu.

---

### Post by neurostu on 2008-03-02
Right so what you need to do is download the GParted live CD. It is more powerful then the version of GParted that comes with the UBUNTU live cd.  The ubuntu version sometimes struggles with ntfs where as I have never had a problem with the GParted CD working with ntfs (ntfs is the windows files system).

When you get the gparted live cd booted up, select the partition then click resize, then create a new partition with the left over space.

Try that then post back if you encounter any errors.

---

### Post by neurostu on 2008-03-02
You can get the Gparted live cd here:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by Happy_Man on 2008-03-02
Yep, what the other two guys said. First unmount the Windows partition, then go in and resize it so you can use it. I believe your issue is that Ubuntu won't resize partitions during installation if they are mounted/in use. So go to your desktop, right-click the drive icon for Windows, and say "unmount volume". Then run the installer again, and it should work.

---

### Post by Dispatch on 2008-03-02
Okay, I'm going to try out all the suggestions here.  I'm downloading gparted livecd and I will unmount the space.  I'll post back here in a bit if I hit another wall.  Thanks for the quick help!!

---

### Post by Dispatch on 2008-03-02
Ugh, bad news...  I unmounted it but still couldn't resize it.  I booted my gparted cd but it just did the same thing it does in the gparted that comes with Ubuntu... Why can't I make a new partition?! Er.

---

### Post by neurostu on 2008-03-02
I'm sorry, I'm not sure what the problem is...

You might want to google "Can't resize ntfs with gparted" or something similar.

I found this thread, check it out:
[http://ubuntuforums.org/showthread.php?t=124508](http://ubuntuforums.org/showthread.php?t=124508)

---

### Post by Dispatch on 2008-03-02
That's the exact same problem I have so I'm going to read through that thread however, I think I'm just going to buy an external HDD and use it just for ubuntu.

---

### Post by owbizi on 2008-03-02
Strange, I did resize a NFTs partition of 30gb~ with gparted on Ubuntu's live cd. Just had to do it with sudo...

---

### Post by iris-n on 2008-03-02
I successfully did it, more than once actually. One quirk is that windows tend to fragment your filesystem a lot, and gparted can't resize it if it's not tidy clean. Try defraging and running gparted again.

---

