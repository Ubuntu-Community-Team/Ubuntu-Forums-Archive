---
title: "Just finished my first Live CD session, what are my next steps?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by mlyons16 on 2007-09-04
Hello, I just finished downloading and burning an ISO of Ubuntu 7.04. Everything went very seamlessly. Now, what are my next steps. I'm readily contemplating installing (should I let Ubuntu's installer do the partitioning, or should I perform partitioning from within the default OS, Vista?)

Also, is there any maintenance or security procedures I should be following? 

Thanks, and I look forward to taking the next steps in my Linux quest.

---

### Post by WebSiteGuru on 2007-09-04
Run your LiveCD and play around with it. See if there is any problems you might encounter. (This will not do anything to your harddrive, it almost like running in RAM mode in windows)

Once you are comfortable with it you can run install icon on the desktop. :D Welcome and enjoy. You'll see the different. ;)

---

### Post by Steve1961 on 2007-09-04
Welcome to Ubuntu.  If you have vista on your pc I believe you can shrink your vista partition from vista itself - contol panel>administration>disk manager.  Defrag first, then just let the Ubuntu installation take up the free space.

---

### Post by rsambuca on 2007-09-04
> **Steve1961 said:**
> Welcome to Ubuntu.  If you have vista on your pc I believe you can shrink your vista partition from vista itself - contol panel>administration>disk manager.  Defrag first, then just let the Ubuntu installation take up the free space.

Yes, if you are going to resize the Vista partition to make room for ubuntu, it is critical that you use the Vista disk manager to do so.

---

### Post by mckryptyk on 2007-09-04
1) Well you need to make a note of any hardware that was unable to work from the livecd.

2) Make a note of what files you will be backing up if formating, if not then leave windows where it is and install beside it if you have the room.

3) figure out your new partition table like this:

/dev/hda1 windows [leave windows alone]

------LVM-------- (Logical volume manager)
/dev/hda2 boot ( /boot)   [200 - 300 MB is lots]
/dev/hda3 root ( / ) [10 to 20 GB is lots]
/dev/hda4 home (/home) [everything else goes here so all the space]
/dev/hda5 swap (swapspace) [half your ram in GB such as 2 GB RAM = 1 GB Swap]
-----LVM-----------
** try to use filesystems like JFS instead of Ext3 you will get better performance **


4) read the beginners stickies on the forums

5) Install

6) ask any of us for help if you get stuck trying to find the answer here to a question.

Best of luck, I hope it works out for you.

Cheers.

---

### Post by Steve1961 on 2007-09-04
> 3) figure out your new partition table like this:

/dev/hda1 windows [leave windows alone]

------LVM-------- (Logical volume manager)
/dev/hda2 boot ( /boot) [200 - 300 MB is lots]
/dev/hda3 root ( / ) [10 to 20 GB is lots]
/dev/hda4 home (/home) [everything else goes here so all the space]
/dev/hda5 swap (swapspace) [half your ram in GB such as 2 GB RAM = 1 GB Swap]
-----LVM-----------

But if you just shrink your vista partition and then run the ubuntu installer and ask it to install in the free space all your partitions will then be setup automatically.  You really don't need to worry about seperate boot root and home partitions at this stage.  Just keep things as simple as possible.:)

---

### Post by mckryptyk on 2007-09-04
I was just suggesting areas he should look into as he goes since he will end up researching them anyways, and will advoid a whole slew of problems by doing so as he experiments with ubuntu later on..

Everything I mention can be done by the graphical menus on the install screen of the livecd.
Point and Clicky. :)

Cheers.

---

### Post by rsambuca on 2007-09-04
> **mckryptyk said:**
> 1) Well you need to make a note of any hardware that was unable to work from the livecd.

2) Make a note of what files you will be backing up if formating, if not then leave windows where it is and install beside it if you have the room.

3) figure out your new partition table like this:

/dev/hda1 windows [leave windows alone]

------LVM-------- (Logical volume manager)
/dev/hda2 boot ( /boot)   [200 - 300 MB is lots]
/dev/hda3 root ( / ) [10 to 20 GB is lots]
/dev/hda4 home (/home) [everything else goes here so all the space]
/dev/hda5 swap (swapspace) [half your ram in GB such as 2 GB RAM = 1 GB Swap]
-----LVM-----------
** try to use filesystems like JFS instead of Ext3 you will get better performance **


4) read the beginners stickies on the forums

5) Install

6) ask any of us for help if you get stuck trying to find the answer here to a question.

Best of luck, I hope it works out for you.

Cheers.

I think your point 3) is unnecessarily complex.

---

### Post by mckryptyk on 2007-09-05
> **rsambuca said:**
> I think your point 3) is unnecessarily complex.

You are correct, The things I have mentioned in post #3 are not necessary at the moment for him to begin using linux, I say "Just boot it up, play with it, have fun and learn. I was getting ahead of myself."

To the Original Poster: You might want to come back to this post later, when you have seen  more of what Ubuntu has to offer you, as linux is one of those things where "The more you invest in it, the more you will recieve from it." 

Again, best of luck with trying linux/Ubuntu, I hope it fufills your computing needs.
Also, don't be shy about asking for help if you get stuck, this is why we are here at ubuntuforums, to help each other in linux related matters.

Cheers.

---

