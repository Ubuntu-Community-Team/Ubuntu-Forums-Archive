---
title: "[SOLVED] Starting fresh...advise needed"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by mramsey on 2007-10-17
With the release of Gutsy tomorrow and my decision to finally let go of windows completly, I want to set my computer up the correct way.

I want to reformat and wipe out 100% of the hard drive. What is best to use for this process, Gparted?

Along with Gutsy I want to create a separate home partition, so for that I need 3 partitions correct? /root  /swap /home?

I have a 160GB HDD so I also want to create some additional partitions for other linux distros. would it be advisable to do this now while I am formatting?

I figure I should use 40GB for root, 4GB swap, 16GB Home leaving 100GB for other distros. What do you think?:)

---

### Post by LowSky on 2007-10-17
Sounds great, however you can only have 4 partitions to a hard drive.
And You dont need you root partition to be that big, and you should make your home partition larger, most likely all your document, music and video will go in here
here some info on making partitions
[http://en.wikipedia.org/wiki/Partition_(computing)](http://en.wikipedia.org/wiki/Partition_(computing))

heres my suggestion

/root = 20GB
/home = 38GB
swap= 2GB
Extended partition=100GB

---

### Post by rsambuca on 2007-10-17
Personally, I would just create a large Extended Partition for all of your linux distros.  If you give each of them about 15GB they can all share the same swap.  Then you can have one large /home partition to share between distros.  Just use a different user name for each distro so things don't get messed up.  I have attached a screenshot of my Linux HD.  It has 5 partitions + swap all inside of one extended partition, and a common shared media partition.  It has served me very well.  Whatever method you choose, I strongly recommend partitioning everything beforehand, so you don't create any errors from partitioning after a distro has been installed.

EDIT:  Oh, and unless you are doing something rather out of the ordinary, 4GB of swap is overkill!  1 or 2 should be plenty.

---

### Post by oilchangeguy on 2007-10-17
> **mramsey said:**
> With the release of Gutsy tomorrow and my decision to finally let go of windows completly, I want to set my computer up the correct way.

I want to reformat and wipe out 100% of the hard drive. What is best to use for this process, Gparted?

Along with Gutsy I want to create a separate home partition, so for that I need 3 partitions correct? /root  /swap /home?

I have a 160GB HDD so I also want to create some additional partitions for other linux distros. would it be advisable to do this now while I am formatting?

I figure I should use 40GB for root, 4GB swap, 16GB Home leaving 100GB for other distros. What do you think?:)

why would you need a 4gb swap file? i'd suggest just allowing ubuntu to use the entire drive, and set it's own partitions. there is no need to manually partition the drive.

---

### Post by rsambuca on 2007-10-17
> **oilchangeguy said:**
> why would you need a 4gb swap file? i'd suggest just allowing ubuntu to use the entire drive, and set it's own partitions. there is no need to manually partition the drive.

If you read his post, he said he wants to install other distros.

---

### Post by LowSky on 2007-10-17
/home partition is helpfull if your OS goes bad, you can just format the root and save all your data that was kept in the /home partition

---

### Post by oilchangeguy on 2007-10-17
> **rsambuca said:**
> If you read his post, he said he wants to install other distros.

ok, but still no need for a 4gb swap file. 512mb-1gb max. and give the other distro's access to it.

---

### Post by Duck2006 on 2007-10-17
1Gb swap and the other distro's access it

---

### Post by mramsey on 2007-10-17
OK...ny bad on the swap. I thought I read somewhere to set swap to 2 times your RAM.

I like the idea of the extended partition. that sounds like what I am after. can you ellaborate on how to accomplish this?

---

### Post by Duck2006 on 2007-10-17
> I thought I read somewhere to set swap to 2 times your RAM

Yes it sould be, but any ram larger than 512Mb, then the swap partition may not be used, so 1Gb is quit enouth.

---

### Post by mramsey on 2007-10-17
> **Duck2006 said:**
> Yes it sould be, but any ram larger than 512Mb, then the swap partition may not be used, so 1Gb is quit enouth.

ahhh...duely noted

---

### Post by jc_madden on 2007-10-17
I'm doing the same thing as the OP.  I have a related question:  I'm getting a DELL laptop with vista already on it.  Can I just pop in the GG cd and let it format the drive or do I need to format it first myself?  Sorry if that is a noob question.

---

### Post by qpieus on 2007-10-17
> **jc_madden said:**
> I'm doing the same thing as the OP.  I have a related question:  I'm getting a DELL laptop with vista already on it.  Can I just pop in the GG cd and let it format the drive or do I need to format it first myself?  Sorry if that is a noob question.

The setup program will ask you want you want to do with the partitions, so there is no need to format it first - it can partition and format your drive then.

---

### Post by Duck2006 on 2007-10-17
> **jc_madden said:**
> I'm doing the same thing as the OP.  I have a related question:  I'm getting a DELL laptop with vista already on it.  Can I just pop in the GG cd and let it format the drive or do I need to format it first myself?  Sorry if that is a noob question.

Partition the hard drive from with in vista, the run the 7.10 install and it will work a lot better.

---

### Post by jc_madden on 2007-10-17
> **Duck2006 said:**
> Partition the hard drive from with in vista, the run the 7.10 install and it will work a lot better.

I am not interested in doing a dual boot if that matters.

---

### Post by Duck2006 on 2007-10-17
Then partition it from the install cd then, it will do it all for you.

---

### Post by mramsey on 2007-10-19
Well I totally screwed up but thats ok, I wanted to start fresh anyway. I am trying to format my hdd like shown [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=578729") in post #3.  I want to be able to install multiple distros and share the same swap and home. I have gparted up and await further instructions:).

---

### Post by Hobo Joe on 2007-10-19
Run the Ubuntu installer, when it gets to the part about partitioning, select manual.

Partition the hard drive so you have about 5- 10 GB for '/', then about 2GB for swap. Then the rest for home. If you ever want to add another distro, you can just add another partition.

---

### Post by bodhi.zazen on 2007-10-19
Well, my 2c is that if you install multiple distros you should use a /media/data partition rather then a /home partition. This is because some of the config files (. files) in /home can conflict. Conflicts are rare, but if they occur it is a pain ...

And, please try to refrain from starting multiple threads on what seems to be the same topic ...

---

### Post by mramsey on 2007-10-19
> **bodhi.zazen said:**
> Well, my 2c is that if you install multiple distros you should use a /media/data partition rather then a /home partition. This is because some of the config files (. files) in /home can conflict. Conflicts are rare, but if they occur it is a pain ...

And, please try to refrain from starting multiple threads on what seems to be the same topic ...

Sorry for the extra post....

I am installing Gutsy now....we'll see what happens! :)

---

