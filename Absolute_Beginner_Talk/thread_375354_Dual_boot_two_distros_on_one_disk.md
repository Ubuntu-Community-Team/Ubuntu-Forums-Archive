---
title: "Dual boot two distros on one disk"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by nick24 on 2007-03-03
Hi everyone :) 

Why is it that when you try to install a second distro, the new distro makes your old distro vanish? I have Ubuntu installed on a primary HD and was trying to install a second distro, now I cant get Ubuntu to boot. The new distro boots fine.  How do I fix this ? Thanks

---

### Post by rsambuca on 2007-03-03
The grub loader of some distros just doesn't seem to detect other OS's sometimes.  I have found that the ubuntu loader is pretty decent at finding others though.  Just edit your menu.lst to add the other distros after installing them.  I have six OS's on my rig right now.

---

### Post by nick24 on 2007-03-03
Thanks for the reply

yes I heard about editing the menu list in the boot file. I've been reading a lot about it on diffrent sites, problem is they are either too complicated or they dont pertain to my issue. Could you explain it to me how to do that? You can send me a link of any website that you might think would be helpful. Thanks

---

### Post by Amenemhet on 2007-03-03
Have you actually looked at grub.conf?? Erm, sorry, it is called menu.lst in Ubuntu, and it can be found in the /etc directory. The first time I looked at it I was impressed by the amount of comments in it to explain things. Have a read first.

---

### Post by louieb on 2007-03-03
> **Amenemhet said:**
> Have you actually looked at grub.conf?? ... called menu.lst in Ubuntu, and it can be found in the .... The first time I looked at it I was impressed by the amount of comments in it to explain things. Have a read first.
In a Ubuntu installation the file he is referring to is /boot/grub/menu.lst. 

I can think of 2 reasons the first distro vanished.

1. It actually did vanish. If you installed the second distro in the same partition then bye bye first distro.

2. As the other were saying the GRUB installer did not pick it up on the fact there is another Linux distro. In my experience its about a 60% chance that the first distro is detected.  

What is the second distro? 
Anyway open a terminal window and type ```
sudo fdisk -l
```  (as in little) and post the output here. And myself or someone will be able to tell if you have one or two Linux distros installed.

Or look at the Dual Boot link in my signature. Anything you want to know about Dual Booting can probably be found there.

---

### Post by Amenemhet on 2007-03-03
Oooops, very very sorry....I gotta watch what question i am replying to...a million pardons...
louieb is correct, the menu.lst is in /boot/grub
If you look at menu.lst in this dir you should see if you have both distros still

---

### Post by rsambuca on 2007-03-03
If you let us know what distro's you are trying to load, and how your drive(s) are partitioned, I am sure we can get it straightened out for you.

---

