---
title: "Quick question"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by Cairna on 2006-11-20
I recently got the Ubuntu CD and I'm planning on making 1 section of hard drive for ubuntu and one for windows. 

I believe ubuntu 6.06 LTS comes with a partitioner?

The default installation deletes everything and I want to make sure that doesn't happen.

So to clarify,  do I just run the cd upon startup, pick the first option and let it install itself? No options seem to appear.

What do I do if I want it to create partitions?

---

### Post by bulldog on 2006-11-20
Better to use the gparted live cd.
Download it here [aprox. 25MB]

[http://sourceforge.net/projects/gparted/](http://sourceforge.net/projects/gparted/)

And burn it on a cd,boot from it and create your free space for Ubuntu.

Just defragment your windows several times before you resize this partition.

Create a free space for about 10-15GB and create a swap 1GB and an ext3 partition from the rest of the space.

When you boot the live cd and come to the partitioner,choose manual and mount swap as swap and the ext3 as your /  [root].
That's it.

---

### Post by speeddemon8803 on 2006-11-20
> **Cairna said:**
> I recently got the Ubuntu CD and I'm planning on making 1 section of hard drive for ubuntu and one for windows. 

I believe ubuntu 6.06 LTS comes with a partitioner?

The default installation deletes everything and I want to make sure that doesn't happen.

So to clarify,  do I just run the cd upon startup, pick the first option and let it install itself? No options seem to appear.

What do I do if I want it to create partitions?

yes ubuntu comes with partitioner if you wish to create partions please read up on this site..the guys done an awesome job..he's helped me and i am positive he will help you

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

Happy installing! (doesnt take long i promise!) Need any more help either private message me or come back to this forum! I and everyone else here will be HAPPY to help you in any way we can!

---

### Post by emarkay on 2006-11-20
It only deletes if you tell it to.

I have a dual boot that works fine and used nothing but the Ubuntu CD.  I have my "D" drive accessable in Linux and the other 5 volumes hidden and used only for Windows 989SE. 

Take it slow, and post specifics - There are a few posts here with specific instructions on new install and dual booting, and even a video or two on an initial install. 

Also confirm that the CD is OK - there's a filechecker there.

---

### Post by Cairna on 2006-11-20
Now, I'm far from being an expert so before I try this...

"Create a free space for about 10-15GB and create a swap 1GB and an ext3 partition from the rest of the space."

What's a swap and what is it for?

What format do I create the 10-15gb free space in and what will it be used for.

ext3 partition: Will it be used for the windows OS?

I've got 70gb free so I want to use a good 65gb for Ubuntu...

---

### Post by bulldog on 2006-11-20
Nope just create a total of 10-15Gb or more of course free space.
From this space you create a 1GB swap file which is used if your fysical memory runs out.

From the rest of the free space you make a partition and format it ext3 file system.

Nothing to do with your windows at all,this is to be used to install Ubuntu on.
Just be sure you leave your windows on the first partitions!!

---

### Post by Cairna on 2006-11-20
I tried the automatic partitionner that came one live cd, but it hard an error when I tried to resize the main partition for windows.

So I burnt the gpartition to cd, but could not booth from it.
](*,)

---

