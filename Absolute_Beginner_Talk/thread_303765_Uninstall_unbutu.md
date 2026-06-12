---
title: "Uninstall unbutu"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by rickskye on 2006-11-20
I have installed Umbutu Linux onto a disk with win xp on it.
The grub thingy has been installed so that a list of startup options apear at start up. How do I uninstall and return disk to win xp only.

---

### Post by xpod on 2006-11-20
Just go into your disk administrater thingy in windows and delete the partition if you really must.:confused: 
You`ll need to fix your xps bootrecord as well with your xp cd and fixmbr or if you aint got an xp cd you can use a 98 bootdisk or similar with fdisk...

Thats how i do it.......used to should i say.

The prospect makes me shudder now:D 

Nothing wrong with ubuntu in general i hope?
You did give it a proper chance after all i suppose

---

### Post by LLRNR on 2006-11-20
The little startup thingy is called GRUB and it's a bootloader. 

If you really want to get rid of Ubuntu and stick with XP...

1. insert your XP install disk and boot from it ;

2. choose 'R' (recovery console) ;

3. type **fixmbr** (this way you won't see the little GRUB thingy at boot time, this command will just restore your HDD's MBR to its original state) ;

4. type (within the recovery console too) **diskpart** it's a partitioner... so you should locate your "unknown filesystem" (or something like this) partition, assign it a drive letter (it will assign the letter automatically) ;

5. exit diskpart and type **format x:** where x is the letter assigned to your ex-ext3 partition.

Happy windows-ing. (BTW what's wrong with Ubuntu?!?!)

---

### Post by bodhi.zazen on 2006-11-20
> **rickskye said:**
> I have installed Umbutu Linux onto a disk with win xp on it.
The grub thingy has been installed so that a list of startup options apear at start up. How do I uninstall and return disk to win xp only.

See if this helps:
[How to restore the MBR](http://www.eddieoneverything.com/windows-xp/uninstalling-the-ubuntu-linux-boot-manager.php)

---

### Post by deanlinkous on 2006-11-20
boot from a win98 bootdisk or similar and use the command
 **fdisk /mbr**

---

### Post by rickskye on 2006-11-20
Thanks for quick responses.
I did not realise it overwrote XPs mbr, I thought it had got in before it. So no worries about that and I am ok with recovery console and partition magic.
Sorted.

PS
You are all so protective. 
For info, I am evaluating Linux for my company so that we can get rid of the yoke of MS. One of the things I have to look at is ease of installation and uninstallation, hence my post.
Once agian thanks, and I am sure you will see many more posts from me in the future. I might even be able to answer some one day.

---

### Post by bodhi.zazen on 2006-11-20
> **rickskye said:**
> PS
You are all so protective. 
For info, I am evaluating Linux for my company so that we can get rid of the yoke of MS. One of the things I have to look at is ease of installation and uninstallation, hence my post.
Once agian thanks, and I am sure you will see many more posts from me in the future. I might even be able to answer some one day.

Friends don't let friends drive....
[indent][indent]Microsoft ! :p [/indent][/indent]

---

### Post by 56phil on 2006-11-20
Thanks for trying Ubuntu. I hope you come back.

---

