---
title: "Installing Ubutu"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by apanda02 on 2007-12-19
I have finally decided to give Linux a try and am having blast learning so much!

After hours of research yesterday to setup a **dual boot (Ubuntu/XP)** on my **Inspiron 1520** I have come up with the following questions.

1. What size of **swap partition** would I need if I have** 2GB RAM**? Many forums say 2x and yet many disagree saying that if you have more than 1GB RAM you should limit yourself. I will be using Ubuntu mostly for surfing, watching, listening, **downloading**, word processing and** programming**. All the heavy-duty work (**Matlab, Photoshop**) I will be doing on XP.

2. I have an **80 GB HD** and I need as much space as possible for my documents. So how much space would be enough? I am thinking of leaving **20GB for XP and 10GB for Ubuntu**? You guys think this will be enough?

3. What **partition type** is best for document partitions? I was thinking of using **NTFS** (since it gives best diskspace economy) and just installing the reverse engineered drivers on Ubuntu to access it?

4. Do you guys think I should first test out **32 Bit** before jumping to **64 Bit**, since I am a new user and all? Or should I jump directly to 64 Bit?

5. Does anyone with the **Media Direct** feature find it useful. I can only think of the quick boot time and longer battery life on the go? But its all useless unless it can play** AVI** files...has anyone gotten it to do that? Still debating if its worth 2.5 GB of my precious HD space. 

I am a new user and apologize if I am asking repetitive question. Would really appreciate some answers!

---

### Post by saj0577 on 2007-12-19
Hey,
Im going to try and answer some of your questions for you.

1. Just give yourself around 2gb of swap and that should be more then enough and room to move.

2. I would go for a little more then 10gb, if you are storing your personal files on a different partition which i believe you are i would give myself around 15 gb just so you have plenty of room to move, (it is possible to resize partitions later but you might as well be prepared. You may also start to like Ubuntu and wish to try out more program so give yourself the extra room to move.

3. I would use FAT32 for documents (and that is not due to NTFS needing extra drivers because this is no longer a problem in 7.10 i believe).

4. Just go straight for 64-bit but try not to be put off, you should not get any problems but if you get any major problems you may have to swap to 32-bit but at least you have tried it and their should not be any problems.


5. Never used or tried it so could not comment.


Saj Hope it helps

---

### Post by Blutack on 2007-12-19
1)  I have 1gb of ram and a 512 swap partition.  After a somewhat dumb error I managed the remove the swap partition.  I didn't notice for around a month until I tried to hibernate the machine.  512 of swap will probably be fine, esp with 2 gb of ram.  I have never run out of ram whilst using ubuntu, and I do lots of heavy-duty matlab/Gimp/video editing.

2)  Depends on what apps you want to install.  The dangerous thing about Ubuntu is the sheer number of fun apps to get.  For a base install 5gb is more than enough, but if you want to start adding a lot of packages 10gb should be fine.  You can resize partitions later on if required.

3)  If you are going to be sharing documents with Windows, NTFS is probably the way to go.  The drivers are built into Gutsy and seem rock solid.

4)  For general desktop use 64bit is not a huge difference over 32.  Especially if all you are doing is browsing etc.  Whilst 99% of apps are both 32 and 64 bit some important things, like Flash, are not so well supported.  There are ways and means but get comfortable with 32bit first.  The speed will probably be a hefty improvement on XP anyway...

5)  Don't have it.  Gutsy will boot in ~30 seconds on my laptop and plays avi's.

(Oops, opposite of apanda :-)
I've had nasty experiences with documents on fat32 drives before, it's an old fashion legacy file system with horrific error recovery.)

---

### Post by saj0577 on 2007-12-19
Its all different personal experiences :lolflag:

What ever you decide to do the community is here if you get any problems along the way so just shout up.

Saj

---

### Post by apanda on 2007-12-19
Thanks a lot for responding guys. I think I will stick to 512 swap since I need the extra space.

Just a few followup question-

So Ubuntu can read and write into NTFS w/o problems? How stable and reliable is it? If so, Saj, why did u recommend FAT32?

I guess I will change my partition scheme to 15GB, 15GB for each operating system.

And what filesystem do you guys recommend for the Ubuntu partition? Also do I need to create a separate boot partition or is it autocreated?

Any other comments on the usefulness of the media direct feature will be appretiated!

Thanks for all your help guys!

Panda

---

### Post by apanda02 on 2007-12-19
Also is there a need for a program to block certain programs from unnecessarily acessing the internet? If so, which one?

---

### Post by saj0577 on 2007-12-20
As for firewalls and restarting programs that is not needed for every day use in linux most people dont use any virus/spyware protection or anything of that sort.

Yeah 7.10 can read and write to NTFS without problems.


As for the partitions and the type you should use, The primary partition will be bootable.

(main partition)
Primary
Beginning (Location of partition)
15 GB
ext3

(swap)
Logical
Beginning (Location of partition)
512 MB
swap

Saj
Let me know if it does not make sense and you want a step-by-step, it should make sense when your on the install screens.

---

### Post by jbt on 2007-12-20
> **apanda02 said:**
> I have finally decided to give Linux a try and am having blast learning so much!

After hours of research yesterday to setup a **dual boot (Ubuntu/XP)** on my **Inspiron 1520** I have come up with the following questions.

1. What size of **swap partition** would I need if I have** 2GB RAM**? Many forums say 2x and yet many disagree saying that if you have more than 1GB RAM you should limit yourself. I will be using Ubuntu mostly for surfing, watching, listening, **downloading**, word processing and** programming**. All the heavy-duty work (**Matlab, Photoshop**) I will be doing on XP.


I think 1 GB would be ample.
I have 1 GB memory, and I don't think I have ever seen it use swap yet.

> **apanda02 said:**
> 
2. I have an **80 GB HD** and I need as much space as possible for my documents. So how much space would be enough? I am thinking of leaving **20GB for XP and 10GB for Ubuntu**? You guys think this will be enough?


Depends what you want to do with it.
I'm currently using about 7GB, but I have kde AND gnome installed, plus loads of apps as I've been trying everything out.

> **apanda02 said:**
> 
3. What **partition type** is best for document partitions? I was thinking of using **NTFS** (since it gives best diskspace economy) and just installing the reverse engineered drivers on Ubuntu to access it?

NTFS support now seems to work out of the box for Gutsy, so that sounds like a good choice.


Regards
JohnT

---

### Post by apanda02 on 2007-12-21
Thanks a lot guys. Dell actually just sent me a 160 GB HD so space is no longer a issue.

Time for the installation!

Panda

---

