---
title: "How to setup partition as /home/"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by pastorjay on 2006-10-31
Hey all, quick question.   I haqve some unused HDD space that is already partitioned in ext3.  How do I mount that as my /home/ drive?

Thanks!
Jason

---

### Post by bsussman on 2006-10-31
1. So as to make sure you are not changing things while trying to move to the new partition, you probably  want to log in as root and not use sudo.

2.  copy all of /home to the partition, wherever it is mounted.

3. compare them and make sure they are identical, including hidden directories and files.

4.  change /etc/fstab so that your partition is mounted at mountpoint /home.

5.  test it.

6. If it is ok, you can log in as root, umount it and clear out the old home, but not before testing.  And make darn sure the new partition is unmounted before clearing out the old home directory.

7. If you have a problem and have not cleared out the old home directory, you can reverse this whole thing by simply umounting and changing fstab.

Go slow - especially if you have anything valuable in /home

---

### Post by steve.horsley on 2006-10-31
> **bsussman said:**
> 
2.  copy all of /home to the partition, wherever it is mounted.

Assuming you temporarily mount your new home partition at /media/hda99, use this command:
**cp -a /home/* /media/hda99**

---

### Post by pastorjay on 2006-10-31
Sorry, I should have been more specific.  I did not have a /home/ at all before I just resized the partition.  I just want to get it named/set properly now.  I have 4 partitions on the drive, one windows, one / one that I want to be home, and the other is swap

---

### Post by bsussman on 2006-10-31
it is an ubuntu system.  

you have a /home - honest.  

It is currently a directory...

If you do not believe me, try going into nautilus and looking for /home.  I promise it is there.

---

### Post by pbaehr on 2006-10-31
I don't think that a straight copy of your home directory will do the job properly.

Here is the guide I used and frequently recommend to people who are trying to set this up.

And you regardless of whether or not you put personal files into your home directory, you still want to move it as it holds all your settings. Even if they are still default, you'll want to take them with you to avoid breakage.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by pastorjay on 2006-10-31
ok, gotcha... and I believe you.  I had installed ubuntu before, and I had specifically labled a drive as /home/.  I did not do that this time, as it was giving me fits with dual booting.  Now that both OS are installed, I just resized the / partition to 10gb, and was label the other as home.  SO, now I have about 15gb worth of space that is unmounted and not useable...  what should I do with it?

---

### Post by pastorjay on 2006-10-31
> **pbaehr said:**
> I don't think that a straight copy of your home directory will do the job properly.

Here is the guide I used and frequently recommend to people who are trying to set this up.

And you regardless of whether or not you put personal files into your home directory, you still want to move it as it holds all your settings. Even if they are still default, you'll want to take them with you to avoid breakage.

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)


Thanks

---

### Post by bsussman on 2006-10-31
depends on how you manage your space.

for some, a separate home is a good idea, for others, a separate usr or var

there are standards for what goes where - see [http://www.pathname.com/fhs/](http://www.pathname.com/fhs/) for more info if you like.

---

### Post by bsussman on 2006-10-31
> **pbaehr said:**
> I don't think that a straight copy of your home directory will do the job properly.


Please explain what a "straight" copy is and whether cp -a fits your definition.  certainly without the -a, more work would be needed to create a workable copy.  And certain metadata would be impossible to recreate (like date stamps) which might matter in certain cases.

**cp -a** preserves all metadata and copies everything.  This is what is needed when moving home elsewhere in the case of a desktop.  There are other techniques that should be employed in very large or busy systems.

---

### Post by aysiu on 2006-10-31
> **pbaehr said:**
> 
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) This tutorial is great. I've also created one based on that, but with screenshots included:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bsussman on 2006-10-31
> **aysiu said:**
> This tutorial is great. I've also created one based on that, but with screenshots included:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

That is a good tutorial - I can use it for answering questions about simply creating/mounting/installing generic new partitions.

---

### Post by aysiu on 2006-10-31
> **bsussman said:**
> That is a good tutorial - I can use it for answering questions about simply creating/mounting/installing generic new partitions.
Actually, for mounting, I'd use this instead:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by pbaehr on 2006-10-31
> **bsussman said:**
> Please explain what a "straight" copy is and whether cp -a fits your definition.  certainly without the -a, more work would be needed to create a workable copy.  And certain metadata would be impossible to recreate (like date stamps) which might matter in certain cases.

**cp -a** preserves all metadata and copies everything.  This is what is needed when moving home elsewhere in the case of a desktop.  There are other techniques that should be employed in very large or busy systems.

I am not sure how cp -a treats linked files. I know the method I used (but did not come up with on my own) has an intricate command to make sure everything is preserved, including links.

cp -a may very well do the job, as well, though. I'm not sure.

Also, nice tutorial, aysiu. Very comprehensive. I'll definitely link to that next time someone asks.

---

### Post by pastorjay on 2006-10-31
Thanks for the great guides!  All is done and working fine!  Now, if I could just get my Broadcom wireless running!  That is next!

---

