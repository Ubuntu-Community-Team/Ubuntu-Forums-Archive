---
title: "Hi everyone"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by jimrz on 2005-12-10
I am brand new to ubuntu / linux, only having fooled around with "live cd's" a bit. For the past few weeks I have been watching these forums and think they are great. I want to thank all of the participants for all the tips that I was able to pick up. Today I installed ubuntu (dual boot w/ xp). After the 1st run I got the dreaded "error 17" when grub tried to load  but, using a couple of trips through the install and the live cd, was able to get past this (WHEW...thought I was really hosed there for a bit) and now have a nice / clean / updated  and functional install up and running. I still have lots of work and a HUGE learning curve ahead, but it seems a good begining and I'm looking forward to the fun (?) (challenge...definitely). Imagine I'll be back here with plenty of questions, and will also be watching to see if anybody has something that I can help with. Thanks, again.

---

### Post by Arc Owner on 2005-12-11
congratulations, and welcome to the forums!;) :p

---

### Post by arpunk on 2005-12-11
Welcome indeed ;)

---

### Post by ubuntu27 on 2005-12-11
Hi jimrz. WElcome to the forums and also welcome to ubuntu Linux.

Glad to know that everything is ok. :) 
you may occasionally find yourself in some kind of trouble, but remember that you will always can ask for a help here.

Ubuntu Breezy Guide: [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

---

### Post by jimrz on 2005-12-11
Thanks you all...glad to be here and nice to be welcomed

---

### Post by DiscoKiller on 2005-12-11
hey jimrz, i was in your shoes about two months ago. it really doesnt take that long to get your head around things especially when u have these forums to refer to! i have to say that i have had loads of fun learning about linux and now i have an OS that brings me great joy (and stability) although i`ve had a few corking errors i`ve managed to get a pretty much customized system with all the progs i need on it. hope you have as much fun as i did, and i`d also like to thank the gurus for their help....welcome aboard!!

---

### Post by JoshHendo on 2005-12-11
[QUOTE=jimrz]I am brand new to ubuntu / linux, only having fooled around with "live cd's" a bit. For the past few weeks I have been watching these forums and think they are great. I want to thank all of the participants for all the tips that I was able to pick up. Today I installed ubuntu (dual boot w/ xp). After the 1st run I got the dreaded "error 17" when grub tried to load  but, using a couple of trips through the install and the live cd, was able to get past this (WHEW...thought I was really hosed there for a bit) and now have a nice / clean / updated  and functional install up and running. I still have lots of work and a HUGE learning curve ahead, but it seems a good begining and I'm looking forward to the fun (?) (challenge...definitely). Imagine I'll be back here with plenty of questions, and will also be watching to see if anybody has something that I can help with. Thanks, again.[/QUOTE]
Welcome to the forums :D

I am glad you fixed your grub error :)
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

I got error 25 in my installation =p, so I was in the same boat as you :P. It just turned out to be really simple solution. Never install a OS on a slave HDD =p

-Josh :)

---

### Post by Rackerz on 2005-12-11
Welcome to the forums! I was in your shoes about 2-3 weeks ago, but I'm still here and learning and im loving it! You'll definately not want to go back too just XP once you've tried Ubuntu. I only use XP for gaming until i can get Cedega working.

---

### Post by jimrz on 2005-12-11
[QUOTE=JoshHendo]Welcome to the forums :D

I am glad you fixed your grub error :)
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

I got error 25 in my installation =p, so I was in the same boat as you :P. It just turned out to be really simple solution. Never install a OS on a slave HDD =p

-Josh :)[/QUOTE]

Surprisingly, I got the GRUB "error 17" when trying to install on the master. Might have been a partitioning error or something to do with boot being beyd sector 1024 [saw that somewhere here in the forums], not certain which. Anyway, was able to fix by using the install cd to blow away all the ubuntu partitions I had made on the master, aborting then using gparted on live cd to make sure changes took, then back to the intall cd and setup ubuntu on slave drive which install ran perfectly and is still chugging happily along. Having lotsa  fun now playing with new toy and trying to learn how to use it.

---

