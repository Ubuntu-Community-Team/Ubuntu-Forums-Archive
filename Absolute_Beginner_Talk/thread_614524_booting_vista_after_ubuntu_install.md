---
title: "booting vista after ubuntu install"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by GeneticFlea on 2007-11-16
ok so im trying to dual boot Vista (which came with my shiny new thinkpad t61p) and ubuntu. Ive done everything fine so far, resized vista partition using gparted, made home directory, swap and root, installed ubuntu, it works great! now though im trying to boot back into vista...and i get the message that vista is damaged and needs me to put in my vista cd to repair it.... ok, but seeing as this was preinstalled by lenovo, all i have are recovery discs, so i put in the recovery disc....and it wipes the whole hard drive including ubuntu. So now im sitting here waiting for it to do a complete restore of vista and im wondering, how can i do this again, but getting vista and ubuntu to work? Ive gotten xp and ubuntu to work just fine on my other comp without needing to repair xp after the ubuntu installation. Should i just throw vista out the window and somehow downgrade to xp? Im totally willing to do that if it would be easier than the vista option and if someone could show me how to do this..


sorry for all the trouble, ive searched for hours online to find a solution and nothing seems to fit my problem.

Im very very determined to use ubuntu. I just need windows for gaming and for work(cs 3 have to have it)


thanks!!!!! i love this community, second week of ubuntu and im never going back

---

### Post by rsambuca on 2007-11-16
You have to use the Vista Disk Manager to "shrink" the vista partition.  Then install Ubuntu into the free space.  For some reason, Vista doesn't like the gParted partitioner.

---

### Post by Inxsible on 2007-11-16
i have successfully dual booted with vista and ubuntu. so its definitely doable.

maybe the last time you installed, you installed over your vista partition or something. Next time you install ubuntu have a look at this [link]("http://www.psychocats.net/ubuntu/installing") and follow the instruction there

---

### Post by Inxsible on 2007-11-16
> **rsambuca said:**
> You have to use the Vista Disk Manager to "shrink" the vista partition.  Then install Ubuntu into the free space.  For some reason, Vista doesn't like the gParted partitioner.
I have heard mixed reports on that issue. There have been a few people who had no problems using Gparted to resize their Vista partitions.

But I guess, its better to be safe and do it using the Vista partitioner like rsambuca suggests.

Also defrag the drive atleast 4-5 times before you do anything (even if its just installed)

---

### Post by rsambuca on 2007-11-16
> **Inxsible said:**
> **I have heard mixed reports on that issue. There have been a few people who had no problems using Gparted to resize their Vista partitions.**


Yes, but we know it definitely can cause problems, so it is best to be avoided.

---

### Post by GeneticFlea on 2007-11-16
i tried the vista partitioner at first but it only allowed me to shrink the windows partition by like 70 gigs. I currently have a 180 gb hd, windows takes up like 12 of that, so ideally i want to shrink my windows partition to 20 or so gb and have the rest for ubuntu, mainly for my /home drive because i love to packrat media. perhaps there is a way to make it do what i want instead of selecting a preset that i cannot change?

Im fairly familiar now with gparted and ubuntus installation. I usually set up the home root and swap in gparted and then use manual in the installation of ubuntu. i know i didnt install over my vista parition because i left it in ntfs and it was still available under boot options on the grub menu. I think it was just pissed because i resized it.


thanks again for all the quick responses!

---

### Post by rsambuca on 2007-11-16
> **GeneticFlea said:**
> i tried the vista partitioner at first but it only allowed me to shrink the windows partition by like 70 gigs. I currently have a 180 gb hd, windows takes up like 12 of that, so ideally i want to shrink my windows partition to 20 or so gb and have the rest for ubuntu, mainly for my /home drive because i love to packrat media. perhaps there is a way to make it do what i want instead of selecting a preset that i cannot change?

Im fairly familiar now with gparted and ubuntus installation. I usually set up the home root and swap in gparted and then use manual in the installation of ubuntu. i know i didnt install over my vista parition because i left it in ntfs and it was still available under boot options on the grub menu. I think it was just pissed because i resized it.


thanks again for all the quick responses!

Defrag, and if that doesn't work, you may have to temporarily disable pagefiling, and turn of your system restore.  Then try again.

---

### Post by dichtbijzee on 2007-11-16
The key is multiple defrags in vista, i did 4 before i installed ubuntu.

---

### Post by Inxsible on 2007-11-16
> **rsambuca said:**
> Defrag, and if that doesn't work, you may have to temporarily disable pagefiling, and turn of your system restore.  Then try again.

> **dichtbijzee said:**
> The key is multiple defrags in vista, i did 4 before i installed ubuntu.+ 1 on defraggin.

I had a brand new OEM installed Vista and even then I defragged at least 6-8 times

---

### Post by GeneticFlea on 2007-11-16
what is pagefiling, and how do i turn it off?

---

### Post by GeneticFlea on 2007-11-16
ok so i woke up this morning to the freshly installed os....to find that lenovo in their wisdom sent me the recovery cds for xp not for vista...oh well, i got ubuntu and xp installed now, both are working in dual boot mode, so although i didnt get vista working, xp is fine with me and it will do the trick. ill save vista for down the road if microsoft ever makes it worth my time (not likely).

thanks for all the help!

---

### Post by Inxsible on 2007-11-16
> **GeneticFlea said:**
> ok so i woke up this morning to the freshly installed os....to find that lenovo in their wisdom sent me the recovery cds for xp not for vista...oh well, i got ubuntu and xp installed now, both are working in dual boot mode, so although i didnt get vista working, xp is fine with me and it will do the trick. ill save vista for down the road if microsoft ever makes it worth my time (not likely).

thanks for all the help!You are the lucky one !!

If the choice was between XP and Vista only, I would take XP any day.

Vista is just plain annoying !!

---

### Post by StephUb on 2007-11-16
> **GeneticFlea said:**
> Should i just throw vista out the window and somehow _downgrade_ to xp? 

Well going from vista to XP is NOT a downgrade.... lol

---

