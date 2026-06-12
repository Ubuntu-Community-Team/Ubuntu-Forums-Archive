---
title: "Installing Ubuntu 7.10"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by jnestorr on 2008-01-08
Okay, I need your assistance here. I have gone thru a lot of trouble trying to install this 7.10 on my old machine. I have partitioned my disk prior to the installation (using a symantec magic- something) so now when i get to step 4 of 7 for installation, I see both of the disk spaces partiotioned earlier (Linux and Swap). The problem however, each time i select them or one of them i get the following ERROR(S). 

No root file system
No root file system is defined.
Please correct this from the partitioning menu.
and it gives me the option to "Continue" or "Go Back" both of which just continuously loop through this error

Any ideas as to the cause and what I should do?

Please advise

---

### Post by kebes on 2008-01-08
It sounds like at the partitioning phase you selected the "manual mode" because you wanted to make sure to pick the right partitions (and not erase any other partitions). That's good, but in the manual mode, you have to manually assign the partition mountpoints.

So when you are assigning the partitions, you have to make sure you set one of them as "type: swap", and one of them as "type: ext3" (or ext2, etc. if you prefer), and make sure it is set with "**mount point: /**".

If you want a separate /home/ partition (or whatever) you have to set that manually, also. For a nice tutorial with screenshots, check out:
[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)

Hope that helps!

---

### Post by dark_phantom on 2008-01-08
I agree with kebes.  Select the partition you created for / and edit it.  It should be something like /dev/sda3 or similar.  Select to mount / and click ok.  That should be all that you need to not get that error again.

---

### Post by jnestorr on 2008-01-08
> **dark_phantom said:**
> I agree with kebes.  Select the partition you created for / and edit it.  It should be something like /dev/sda3 or similar.  Select to mount / and click ok.  That should be all that you need to not get that error again.

Okay....so i should pretty much right click the disk partitioned---select edit and then switch from ext2(default, BTW) to something like "/"

I believe the swap portion does not have any option.

---

### Post by jnestorr on 2008-01-08
> **kebes said:**
> It sounds like at the partitioning phase you selected the "manual mode" because you wanted to make sure to pick the right partitions (and not erase any other partitions). That's good, but in the manual mode, you have to manually assign the partition mountpoints.

So when you are assigning the partitions, you have to make sure you set one of them as "type: swap", and one of them as "type: ext3" (or ext2, etc. if you prefer), and make sure it is set with "**mount point: /**".

If you want a separate /home/ partition (or whatever) you have to set that manually, also. For a nice tutorial with screenshots, check out:
[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)

Hope that helps!


Actually one of them is already set as ext2 and the other as swap. So all i have to do is right click the "ext2" and select /" ?...........bleave it or not i don't know anything about mounting.

---

### Post by dark_phantom on 2008-01-08
You should leave the type as ext2 and just mount it to "/".  For swap there is no way to mount it from the edit window, but that's okay.  From the beginning it should be something like this:

partition type mounted at
/dev/sda2 ext2 /dev/sda2 <- change this to "/" via the edit button.

I hope this clarifies it better.  I'm going by memory so it may be a little off.

---

### Post by dark_phantom on 2008-01-08
I forgot to say that you need to click on format as well.  Look at this image below to see what I was talking about.  Select the root partition and click on the edit button.

[http://img216.imageshack.us/my.php?image=feistydual12tj0.png](http://img216.imageshack.us/my.php?image=feistydual12tj0.png)

---

