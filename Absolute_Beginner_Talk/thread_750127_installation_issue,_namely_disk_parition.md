---
title: "installation issue, namely disk parition"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by odwyerda on 2008-04-09
ok ive spent the past while looking up previous posts on this and ubuntu wiki but im still at a loss.

I have uninstalled wubi and I now want a dual boot system of XP and ubuntu FF. I have cleaned up my HDD (80gig) to have 40 free of which i want to use 30 for Ubuntu.
I am using the non GUI installation method cause my laptop doesn't like the GUI mode.
Everything goes dandy till I get to the disk partition screen.

I have the usual screen of what do i want to do 
guided partition with all the options like partial partition or full partition with or without vlm encryption ect...
And manual partition.


No from what I have read I should be ok using the guided partition but..... it comes up error saying that there isnt enough disk space to partition  it says tehre is 680mb is the largest free space available ( total 40gig free) 
same for all guided modes.

So I had a gander at manual and to be honest it scares me I dont want to delete everything yet I need the 30gig for xp that  I have.
Help!!

Ps i have an inclination that i may have a badly fragmented drive so thats why i dont have a large enough chunk of free disk space to partition it, so im doing a defrag now. Should that help????

Cheers in advance

Go raibh maith agat
Dabhí

---

### Post by mikeyphi on 2008-04-09
Hi there and welcome!

1. Defrag windows - more than once!!!
2. There is only a small free space because your drive is formatted for windows - you need to resize your windows partition!! If you can't see the resize option during the install process -Run gparted from the LiveCD (or use a windows program) to downsize the windows partition.
3. You will now have a lot of free space - during the install process tell the partition process to use this free space!

A good guide here: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Good luck - ask again if more info needed!

---

### Post by odwyerda on 2008-04-09
ok now things are beginning to make sence !!
thank u very much!!!

is it just me or should this be explained better in the help pages?? or is it just because im using the non GUI boot mode?

---

### Post by mikeyphi on 2008-04-09
It's not just you!!!
There are a lot of help pages - if you wade through the wiki - but the 'normal' LiveCD is generally easier and usually more suitable for the majority. Your laptop falls into the minority!!
Persist - I'm sure you will be happy with Ubuntu!!

---

### Post by odwyerda on 2008-04-09
Hmm I have defragmented my HDD a few times and I foresee a few problems.

As part of my college network we have to use different log ins 
1: my own to directly into my computer
2: into the college network

Im admin on both ( soon to change come Ubuntu :)   ) 
but on my defrag screen I have  the following ( see atached)

Note the green files that the defrag cannot move, this will if I understand what I have been reading up on when I want to defrag I will not have a access to the full30gig partition I plan!

I forsee this as my last problem before Ub is installed

---

### Post by odwyerda on 2008-04-09
ok think i have a solution , sorry about that!

---

### Post by odwyerda on 2008-04-09
ok if anyone else finds this post 
Unmovable files are windows files , Hibernation files and virtual memory.

My Computer- properties- advanced
Turn virtual memory to 0 and turn off hibernation files.

[http://lyratechnicalsystems.com/?p=9](http://lyratechnicalsystems.com/?p=9)

---

