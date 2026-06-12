---
title: "Installation,Partitioning Question(s)"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by i-m-p on 2006-10-27
Hi, 
 
 I've successfully downloaded new Edgy one and I'd like to install this.
Live CD is working fine.

 My partition make up is ,hda1 for windows, hda2 for ubuntu /home partition, hda3 / partition, hda4 swap partition.

 So step 5 of installation process. I choose "manually edit partition table" then next screen appears indicating my partition make up.

 Should I delete hda3 and hda4 at this stage? I am NOT sure what to do.
Please help

---

### Post by bsussman on 2006-10-27
I do not think you want to delete them - where would you put ubuntu then?

Are you looking to destroy a currently installed version?  If so - just make sure the checkbox is checked for reinitializing.

---

### Post by i-m-p on 2006-10-27
OK,

Then can anyone tell me what to do? 

The "Prepare mount points" screen tells me that my current /home partition as 
 / partition and current root / partition as /media/hda3 partition. Reformat?
box is checked / partition (which actually is a /home partition) and swap partition.

Should I just click the pull down menu and change / partition to /home and /media/hda3 to / . And also change the "Reformat?) box.then proceed a installation process?

Sincerely

---

### Post by justaguynpc on 2006-10-27
I have to ask, do you currently have a linux distro installed?  If so, you will want to reformat your / and /home partitions.

---

### Post by i-m-p on 2006-10-27
> I have to ask, do you currently have a linux distro installed?

Thanks and sorry for not claryfing my current situtation.

I have a dapper currently installed. So I would like to upgrade to Edgy.

However I would think now probably I don't have to do the normal installation 
 process in order to upgrade do I?

So probabaly it was a question I shouldn't have asked.

All I should do is open /etc/apt/sources.list and replace the "dapper" with the new code word and run.
sudo apt-get updates
and
sudo apt-get dist-upgrade
Am I correct?

Plus probably just as the important notice said
I should wait some time until the current servers overload moments to be passed shouldn't I?

Sincerely

---

### Post by bsussman on 2006-10-28
That sounds about right except I am having difficulty finding the word backup anywhere in your proposed procedure.

Depending on your tolerance for running such an aged version as 6.06 ( :mrgreen: ) and your tolerance for major bugs, ya might want to wait like a week - a systems reliability researcher named Murphy postulated that the last major bugs are found by the first major users :twisted:

That being said - I am running both on various systems in my net and not yet seeing any reason to hold off on 6.10 :D

But Murphy left a phone message for me yesterday...

---

### Post by justaguynpc on 2006-10-28
It may just be a quirky preference of mine, but, I always complete a fresh install from version to version.  This will ensure you have no "malingering" scripts hanging around,  a clean install is what I would be doing in your situation.

---

