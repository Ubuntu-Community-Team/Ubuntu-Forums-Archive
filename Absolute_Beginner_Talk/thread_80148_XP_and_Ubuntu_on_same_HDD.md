---
title: "XP and Ubuntu on same HDD"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by kallumama on 2005-10-21
Hello guys,

I have a laptp and was going to install a new HDD on it this weekend. I need to have XP on it since i want to run some apps that Ubuntu cannot run, but i also wanna run Ubuntu on the laptop since i wanna try it out. 

Is there a way i can have them both on the same HDD? 

Thanks,
KalluMama

---

### Post by rykel on 2005-10-21
yes, you have to partition your HDD to accomodate the 2 OSes.

i suggest tat u allocate abt 10GB each to both XP (NTFS) and Ubuntu (ReiserFS - assign it to be "root"), another 10-20GB for Ubuntu "Home" with the balance HDD for data (FAT32 or VFAT).

using the scheme above will save u a lot of time in future when u change distro or need to transfer files to and fro XP/Ubuntu.

next, install XP FIRST into the NTFS partition, and then Ubuntu linux. let ubuntu do the rest of the Dual Boot screen setup etc.

u will have to mount your XP and Data partitions manually in a linux file called /etc/fstab. this will automatically load the 2 partitions as 2 icons on ur ubuntu desktop in future.

i do hope tat the next version of ubuntu can catch up with SUSE, MEPIS or Knoppix in this respect - tat is, automount all other partitions so tat we do not have to edit fstab!!

a great place to start learning more about ubuntu is [Unofficial Ubuntu Guide]("http://www.ubuntuguide.org").

pls, anybody, correct me if i am wrong.

---

### Post by kallumama on 2005-10-21
Thanks rykel!! That's some great suggestions!! I iwll go to the guide and read up more on this issue!!


Thanks again

---

### Post by patrick295767 on 2005-10-21
[QUOTE=kallumama]Hello guys,

I have a laptp and was going to install a new HDD on it this weekend. I need to have XP on it since i want to run some apps that Ubuntu cannot run, but i also wanna run Ubuntu on the laptop since i wanna try it out. 

Is there a way i can have them both on the same HDD? 

Thanks,
KalluMama[/QUOTE]


Hi, 

I installed ubuntu  ... thinking same as u : I cannot run my windows apps' ... 
Now, after using ubuntu since some time, i am thinking to remove my windows partitions 
and being still using my windows applications !
 
Yes, yes, I can use all my windows (the ones I need) via Ubuntu by using either the wine program or the crossover program (office works damn well and damn fast).
I installed my other programs and I didnt suffer of any bugs.
I am fine with it 'cos linux is great !!
  
Concerning Microcal Origin, big bug annoys me, but that's the only one !!!

Enjoy Ubuntu !!

best regards, 

patrick

---

### Post by gpw797 on 2005-10-21
How in the heck do you get XP on a 10 gig partition? I have a VERY BASIC XP  installation on one hard drive and it takes up as lot more space than 10 gigs.

---

### Post by invalid on 2005-10-21
> How in the heck do you get XP on a 10 gig partition? I have a VERY BASIC XP installation on one hard drive and it takes up as lot more space than 10 gigs.

Um.. no.. it is very possible

Cheers,
Cb

---

### Post by atom14x7 on 2005-10-22
My WINDOWS folder (on XP) only takes up just under 3 gig... i'm working very happily off a 10 gig win partition, have been doing so for the past 2 years....
Admitably, if you're into storing a lot of information, then you'll need more space than that

I dont know how on earth you managed to get a WinXP installation to take up more than 10 gigs :S

---

