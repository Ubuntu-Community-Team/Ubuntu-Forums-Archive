---
title: "Help needed on type of dual boot"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by veganrailpunk on 2006-11-22
Hello there, i am completely new to linux but keen to learn. I have been looking through the forums to and see there are a few different ways of setting up a dual boot system. 

I am wanting to install a dual boot on 2 hard drives with dapper on my master and XP on my slave (both IDE hard drives). I also wanna be able to move files between the hard drives (is this possible?) cuz i have loads of files i need to keep and would like to use on both systems. Also is it possible to get a selection screen at boot up to chose which OS to use?

Any help would be great, cheers

Pete
xx

---

### Post by Henry Rayker on 2006-11-22
I may be wrong (and please correct me if I am) but won't Windows refuse to boot from a slave drive?

---

### Post by gentlemanmasher on 2006-11-22
On one of my spare computers I have media center on my slave and XP pro on my master.  Of course I never use windows or that computer but it will boot off of slave.

---

### Post by veganrailpunk on 2006-11-22
yeah it appears that it is posible to boot windows as a slave (sounds like a good position for it to be in!!)

---

### Post by FatalFungus on 2006-11-22
I took the plunge on Monday and installed 6.06. I ended up with exactly what you are looking to do. I've got 6.06 on my master drive and I have XP on my slave. XP will easily boot as a slave. It took me a little bit of searching to find out how to get it to boot, but I got it working. [This thread]("http://ubuntuforums.org/showthread.php?p=677880#post677880") will help to guide you. GRUB will give you the OS selection that you are looking for, and it is installed when you install Ubuntu.

As for moving files between drives, I do not know. I've been an Ubuntu user for all of 3 days.

---

### Post by veganrailpunk on 2006-11-22
Cool thanx for the replies. I'm gonna go for it and see what happens! Looks like it can do what I want it to do. Good luck FatalFungus as we embark on the same journey (ish). :D

---

### Post by FatalFungus on 2006-11-22
Good luck to you as well. I hope your install and first few days have gone as relatively smooth as mine have.

---

### Post by gn2 on 2006-11-22
> **veganrailpunk said:**
> Hello there, i am completely new to linux but keen to learn. I have been looking through the forums to and see there are a few different ways of setting up a dual boot system. 

I am wanting to install a dual boot on 2 hard drives with dapper on my master and XP on my slave (both IDE hard drives). I also wanna be able to move files between the hard drives (is this possible?) cuz i have loads of files i need to keep and would like to use on both systems. Also is it possible to get a selection screen at boot up to chose which OS to use?

Any help would be great, cheers

Pete
xx


This may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by Ocxic on 2006-11-22
it doesn't matter what drive has what on it, my dad is triple booting ubunttu and windows with my bro and sis. just be sure that you install windows XP first, b4 ubuntu, and yes you can share files, but you'll have to setup a fat32 partiton to do that, as it's risky to write to an NTFS drive (NTFS is the filesystem windows uses, fat32 is another filesystem type)

---

