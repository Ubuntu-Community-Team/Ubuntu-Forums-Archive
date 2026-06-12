---
title: "More help with installation"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by japc126 on 2006-11-17
Now that I started to install Ubuntu, I have some problems. The setup is asking me to install some "mount points"

I tried to tell it to install them all in the partition I had assigned for Ubuntu, because I want to keep my copy of XP.

By the way, my hard drive has four partitions: one with xp, one with (I hope soon) Ubuntu (the two have ntfs), and two others that apparenty came with my machine, that have fat16 and fat32 filesystems, and I honestly don't know why they are there or what do they do but I do not dare to remove them. (my machine is a dell dimension 8400, just in case)

So, could somebody tell me what to do?

---

### Post by Bachstelze on 2006-11-17
Hi and welcome to Ubuntu :)

You cannot install Ubuntu (or pretty much anything else than an NT-based Windows) on NTFS. You'll need to format the partition using a Linux filesystem (usually ext3).

About your FATs, I guess they're used by the recovery system if you want to get your system back to 'factory settings'.

---

### Post by japc126 on 2006-11-17
Okay, now after I reformat the partition into ext3, what do I select for mount points?

---

### Post by taurus on 2006-11-17
> **japc126 said:**
> Okay, now after I reformat the partition into ext3, what do I select for mount points?
Mount it as /.

---

### Post by japc126 on 2006-11-17
The setup is telling me to install a mount point in my xp partition. Won't that conflict with xp

Actually what it's telling me is this:

Mount point --  Size --  Partition  -- Reformat?
/media/sda1 -- 55Mb -- *** sda1      -- no
/media/sda3 --  4 GB -- *** sda3     --  no
/   --------------------  15Gb -- *** sda4     --  Yes
/media/sda2 --  55Gb -- *** sda2      -- no

sda2 is where xp is installed, sda4 is where I want Ubuntu installed, and sda1 and sda3 are the "mystery partitions"

*** is a lot of letters that I'm too lazy to write down

If I click forward with this options, will Ubuntu install correctly?

(I'm sorry I have to ask so much, but this is my family computer and my fathers would kill me if something bad happened)

---

### Post by Bachstelze on 2006-11-17
Yes, it will install fine. You might want to change /media/sda2 to /media/windows if you want to have a more informative mountopint (it will be the place you will use when/if you want to access your Windows files from ubuntu).

---

### Post by japc126 on 2006-11-17
I can't thank you enough:D :D :D :D

---

### Post by japc126 on 2006-11-17
It said it found an error in fat16. Should I continue and leave it "as is" or correct the problem?

---

### Post by japc126 on 2006-11-17
Its asking me to add some 'swap" what do I do?

---

### Post by Bachstelze on 2006-11-17
You need to make your root partition a bit smaller and create another one for swar (~512 MiB).

---

### Post by japc126 on 2006-11-17
But it won't let me have more than four partitions!?

---

### Post by Bachstelze on 2006-11-17
Yes it will, if you create your Linux partitions as Logical, not Primary.

---

### Post by japc126 on 2006-11-17
The logical partition option is grey

---

### Post by japc126 on 2006-11-17
nevermind, I have finally done it

---

