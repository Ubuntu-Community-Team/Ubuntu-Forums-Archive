---
title: "Ububtu partitioning"
date: 2007-10-07
forum: Apple PPC Users
---

### Post by Mudmanc4 on 2007-10-07
Sorry if this is a redundant question, but searching for a week or so, I just cannot seem to get this right, nor find my answer.

I have a G4 ppc, and ubuntu ppc, My question is, what is the " unknown partition " left by the automated install? As you can see, there is a boot flag on the second primary, but needs to be before any other partiotions to be viable, from my knowledge. 

I have tried repeatedly to manually partition, but cannot seem to get the boot flag on partition #1. The no new world / or apple bootstrap message comes up, and it will not boot from HDD.

 What am I doing wrong? Or , what needs done.

[[IMG]http://i95.photobucket.com/albums/l125/mudmanc4/th_Screenshot.png[/IMG]](http://i95.photobucket.com/albums/l125/mudmanc4/Screenshot.png)

---

### Post by Sef on 2007-10-07
> I have a G4 ppc, and ubuntu ppc, My question is, what is the " unknown partition " left by the automated install? As you can see, there is a boot flag on the second primary, but needs to be before any other partiotions to be viable, from my knowledge.


That is true if you are running Windows.   Not sure about Apple.  


> I have tried repeatedly to manually partition, but cannot seem to get the boot flag on partition #1. The no new world / or apple bootstrap message comes up, and it will not boot from HDD.

If you can boot up, then i d leave it as it is.   It looks like you only are running GNU/Linux.

---

### Post by Mudmanc4 on 2007-10-07
The boot sector must be in the first partition w/ an apple, or so I read, and yes, I am only running Linux, and no , she won't boot.  If I try to maually move the /boot partition to the first spot, the system changes to "/media/hda" .

---

### Post by Mudmanc4 on 2007-10-07
Update:  Installed system, did all updates,   restarted , and the same thing, will not boot to anything, except open firmware. Shows black screen, and will not recognise command / option, to view bootable devices.    Showin no love  : (

 one minute later, after removing power , including battery, she boots .    I don't understand

---

