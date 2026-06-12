---
title: "Sudo, GKsudo and Partition Numbers"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by Apple 101 on 2006-06-24
Hi all, I'm having some confusion about some commands in Linux, and about the partition numbering system.

1. What is the difference between *sudo* and *gksudo*?  I've always used *sudo*, not *gksudo*.  Which should I use?

2. I do not understand how to work out the partitioning number system in Linux.     When asked which partition is (hd0,1), I'm not sure.  Can anyone give me some advice on how to tell the difference between the Linux partitioning system and the Windows system?

Thanks for your help.  I appreciate it.  :D

---

### Post by ajgreeny on 2006-06-24
As I understand things, strictly it should be gksudo to do something using a gui program, ie *gksudo nautilus* to get a root file manager.  Mind you, it always is written as *sudo gedit* in various instructions on the guides I've seen, and this never appears to give any problems, so perhaps it depends on the program in use.  Perhaps someone else can give us both a proper answer.

As to partitioning numbers, I agree it's confusing, made all the more so by grub which uses a different one again.

Grub always starts at zero (0) for its disks and partitions, so the Windows partition, as far as I can see is on hd0,0 in grub terminology, but on hda1 in linux terms.  Somebody correct me if that's not right, please.

I can't remember how windows does it now as it has been so long since I needed to know.

---

### Post by Apple 101 on 2006-06-24
I read somewhere that Extended partitions also have a strange numbering system.  Hmmm... It's all so confusing...

Thankyou ajgreeny.  Could you also advise me on the differences between (hd#,#) format and the /dev/hda# format?

---

### Post by ajgreeny on 2006-06-24
Sorry, but I think it needs someone with a bit more background knowledge than me to sort out that one, though it may just give you a clue if you look at the file in /boot/grub/devices.map, mine shown here:-

(hd0)	/dev/hda
(hd1)	/dev/hdb

I agree this may make things even more confused as it shows both the grub and linux terminology, but I think this is just to link from grub at bootup to the hard disk grub is referring to where the OS sits.

Anyone else got more definite info on this conundrum.

---

### Post by aysiu on 2006-06-24
If you use *sudo* instead of *gksudo* for graphical applications, one or more of the following could happen:

1. The program just plain won't work
2. You'll screw up your user permissions on configuration files you should be able to modify but now can't
3. You won't be able to type in your *sudo* password unless you're launching it from the terminal
4. Nothing much. It appears to work fine.

As ajgreeny points out, most documentation is poorly written in this respect and will tell you to *sudo gedit* whatever. It's best practice to use *gksudo* (for Gnome) or *kdesu* (for KDE) for graphical applications and *sudo* (for both) for terminal applications.

There are two ways partition numbering appears: (hd0,0) and /dev/hda1

They both mean the same thing, but (hd0,0) is used in the /boot/grub/menu.lst, and /dev/hda1 is used just about everywhere else.

(hd0,0) means /dev/hda1
(hd0,1) means /dev/hda2
(hd1,0) means /dev/hdb1
(hd1,1) means /dev/hdb2
(hd1,2) means /dev/hdb3

As you can see, the parentheses numbering is just a little behind the /dev numbering. And the /dev numbering is basically a (first hard drive), b (second hard drive), c (third hard drive), etc., and 1 (first partition of the drive), 2 (second partition of the drive), and so on.

---

### Post by user1397 on 2006-06-24
so relating grub's system with linux's system, i guess that if you had 3 partitions on one hard drive, and 2 on another, it would be:

(hd0,0) /dev/hda1
(hd0,1) /dev/hda2
(hd0,2) /dev/hda3

(hd1,0) /dev/hdb1
(hd1,1) /dev/hdb2

get it? :)

EDIT: aysiu, you beat me to it once again!

---

### Post by Sye d'Burns on 2006-06-24
[QUOTE=Apple 101]I read somewhere that Extended partitions also have a strange numbering system.  Hmmm... It's all so confusing...

Thankyou ajgreeny.  Could you also advise me on the differences between (hd#,#) format and the /dev/hda# format?[/QUOTE]



There can be up to four primary partitions on a physical drive. Logical partitions don't really have a strange numbering system, they start at five, reguardless of whether you actually have four primary partitions.
Examples:
hda1 = first physical drive, first partition
hda3 = first physical drive, third primary partition
hdb5 = second physical drive, first logical partition 
hdb9 = second physical drive, fourth lgoical partition

As far as differences go - it's really not that difficult once you get your head around it. Here are a couple of examples:
(hd0,0) would be the first physical drive , first partition --- hda1
(hd0,2) would be the first physical drive , third partition --- hda3
(hd1,0) would be the second physical drive , first partition --- hdb1

---

### Post by Sye d'Burns on 2006-06-24
Good gosh, I'm a slow typist today

---

### Post by user1397 on 2006-06-24
[quote=Sye d'Burns]Good gosh, I'm a slow typist today[/quote]don't worry about it!  as far as your info, it was the most detailed one of all!  (you included primary/extended partitions, I had no idea until now!)

---

### Post by aysiu on 2006-06-24
Yeah, I saw that strange behavior, but I didn't realize it always started at 5. Thanks for clearing that up, Sye d'Burns.

---

### Post by Sye d'Burns on 2006-06-24
[QUOTE=aysiu]Yeah, I saw that strange behavior, but I didn't realize it always started at 5. Thanks for clearing that up, Sye d'Burns.[/QUOTE]

 I really should edit that post. (I will) It needs to be clarified that there are four primary partitions. You don't actually write to an extended partition. An extended partition acts as a container that holds logical partitions.

---

### Post by Apple 101 on 2006-06-24
:-D :-D :-D  Thankyou everyone.  That information clears a lot of things up.  I now understand how to work out the differences in numbering systems, and that extend partitions always start at five.

I'm bookmarking this thread for future reference!

---

