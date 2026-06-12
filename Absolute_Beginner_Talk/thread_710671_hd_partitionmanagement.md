---
title: "hd partition/management"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by manicmailman on 2008-02-28
hey, im new... although i suppose thats a prerequisite for this section of the forum...

i recently installed ubuntu... during the install it used a section of one of my partitions (i have a 200g-ish hd)... initially that was fine because i xp dual booted... but i am enjoying ubuntu and am looking to put my music on from my external (thereby completing the conversion)... but because of the fact that it only used a section of a section of my hd... i dont know if i will have enough space... so the question is:

can somebody help or give me an overview of hd management in ubuntu, i still have not grasped the architecture of ubuntu compared to windows... this is literally the first time in my life that i have not used windows (which i know very well) and im only two days in... theres too much to learn!

second question: is there a guide around that would be like linux/ubuntu for dummies? for people like me who are 'still in the box' new.. i have checked out the install guide but that wasnt comprehensive beyond the install process...

---

### Post by Scunizi on 2008-02-28
there are some good book on Ubuntu at Barnes & Nobel and others.  "Beginning Ubuntu Linux" by Thomas on Apress I got a lot out of.  As for the directory structure... it's in the book and too much to go over here.. That being said let me point a few things out.

If you are going to eliminate windows completely you might be better off with a fresh install to make use of the entire drive.  If not, the below still applies.

1> When partitioning it is good to put your /home partition by itself (it makes reinstall or upgrading much easier)
2> The "root" or / directory really only needs between 8-15 gigs.. depending.  Root  has numerous directories a couple of which you MIGHT want to seperate. /var could be one if you get into developing or serving your own website(s).  Another is /usr (not really sure on this one.  Just a tickle at the back of my mind as to the benefit of seperating it. 
3> Although I haven't done this, using the Alternate CD for install will give you access to LVM or Logical Volumn Management.  This allows you to create partitions as needed on the fly, or add a harddrive and use it's space as an invisable attachment to another partition you might have... There's much more to it so read up some..

Another great resource for information in real time is on IRC.  Download and install xchat from Synaptic Package manager or Add/Remove and log into the irc.freenode.net server.. once logged in type /join #ubuntu and you will be in a room with roughly 1100 other people of varying degrees of skill that are there to help answer and ask questions.  When you're really stuck or find someone there that just likes to talk proceedure it's a great resource.  It's also a great place to give back to the community with your growing knowledge base.

Welcome!

---

### Post by manicmailman on 2008-02-28
wow thanks...

---

### Post by Omnios on 2008-02-28
Hi bud. Good to hear you are enjoying Ubuntu. 
 
 As for books there are some preetty good ebooks online. Main things to learn are shell commands and installing tarballs as I think they are the most confusing at first.
 
 As for the partitions This all counts on the size of your drives and what you want to do with them. If dual booting you do not need a lot of space for windows unless you want to play a very arge game on them. I had Never Winter Nights a while ago before I got rid of it and it took up about 9gigs in windows for the hole game expantions and all. "Gave up on RPG's" Anyways as for windows you can use a really small partition for a dual boo. 
 
 Now as for Linux counting on how much core stuff you are planning (root files) you would not need more that say about 30gig or so, I jest set up my rebuild install XP/Ubuntu with 40G so I will never run out of root space. Now the problem with music etc is that it will be in you home directory which is in the main (root) file system so that would be 30giigs plus the space you need for your personel files. 
 
 My last set up had XP, Ubuntu, and a fat32 documents partision that was shared between XP and Ubuntu. This was on a 120G and a 40G drive. This proved to be a pain to use so
 after getting a 80G drive from my dad I redid my old tower and made a small partition for windows about 30gig. and used about 40gig for my Ubuntu partition. The realy big change was instead of mounting the /home in the install partition I game it its own partion 120Gigs in all. The /home can be set up in the partition section during the install and think it can also be changed without reinstalling. 
 
 The big point here is that the seperate /home is seperate from root directory. You can also use a win program to mount ext3 n windows and possibly use the /home as the My documents mount point in XP.
 
 Generally speaking mounting /home as a seperate partition fixed all my space headaches. 
 
 Please post the hard drive and partition sized and exaclly what you are trying to accomplish.

---

### Post by redrocket on 2008-02-28
have you tried actually playing with partition editor on ubuntu?
in terminal: sudo apt-get install gparted
then System -> Administration -> Parition editor
I found the easiest way to learn about modifying paritions, mounting paritions, and fixing grub/mbr is to start playing around with the hard drive. the live cd is a wonderfull tool for booting back up and using google to fix any problems you create :P

you could mount your xp drive in ubuntu, and use this for storage?? I used to have (used to dual boot, not anymore ;) ) this setup

---

