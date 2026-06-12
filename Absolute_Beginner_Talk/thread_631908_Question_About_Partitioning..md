---
title: "Question About Partitioning."
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Keilious on 2007-12-04
After a block of research, I think I finally understand how to install Kubuntu on my system (RAID causing trouble). I'm deciding how to slice up my disk space for a dual boot with Windows XP.
I found the partitioning guide psychocats.net to be a great help, but I'm still not 100% sure of the best way to do this.
I've got ~300GB total to work with, so I'm looking at:

[LIST]
[*]4GB swap (Due to 2GB RAM)
[*]10GB ext3 for root
[*]70GB ntfs for Windows
[*]~216GB ext3 for home
[/LIST]

I hear that if you've got lots of space to work with its a good idea to create more partitions for other things. Should I go about figuring these other partitions out on my first linux install? If so, what are these other partitions I should add?

Are the current sizes looking right? I see that 5-10GB for root is often suggested... Should I bump it up? Its where the OS and all your programs go, right? It just seems kinda small coming from the monstrous program sizes of windows (but I guess most of the space there is taken by games).

---

### Post by m0biu5 on 2007-12-04
I doubt you will need to follow the 2 * RAM rule when you get past 1GB. I have 768Mb of ram, and I never run into swap. You could probably keep that down to a gig and be fine.

For root, you might as well bump it up a little. Anything not in /home/yourusername will be under / , so it can't hurt to have a bit more there (unless you have 100's of gigs of files for your home directory, say music, or movies).

I think another popular thing to do with dual booting is to make a partition that is to be shared between both operating systems. Thats up to you. You might also want to look more into LVM, as this will allow you some more fluidity with your partitioning.

Best of luck to you!

---

### Post by daimaru on 2007-12-04
most of the stuff you will use ( download etc) is going to reside in your /home partition, so 10 gb for root will be enough far all the programs you'll install.

but you have to remember that the /tmp folder is also under root. so if you do a lot of video editing, ripping or audio editing conversion stuff you have to either define your /home partition to be used as a temp folder or just give your root partition a bit more space. i gave mine 20gb because i can spare it and i do rip  a few dvd's or use audio software to record stuff so i sometimes need the space. 

as for the multiple partitions  (home swap and root partitions) i would not recommed using them as a linux beginner. there are loads of ways to partition your system using extra partitions for log files or the boot sector, but the way your going right now is really good, and sufficient enought for anyone starting out. having /home on a different partition than your root directory is the most important thing, because it lets you keep all your data if you decide to reinstall or switch to a different version of linux in the future.

---

### Post by Paqman on 2007-12-04
4GB for swap is a bit big. With 2GB of RAM it's likely that you'll never even dip into swap space. I'd say 1-2GB maximum.

10GB for root is good, the only time you might possibly need more is if you were doing anything that created stupidly large temp files, such as copying DVDs. Linux has a much lighter footprint on your drive than Windows, to be sure.

Overall i'd say your partitioning plan looks excellent!

---

### Post by Keilious on 2007-12-04
I do lots of 3D rendering and video editing, so I'll bump up the root partition, but leave the SWAP at 2GB then... just in case (I have previously run into using virtual memory in photoshop in WinXP, and two GB won't be the end of the world if I never end up using it).

As for swapping files between the two OS's, I think I'll go with that driver thing that lets Windows read/write ext3.

Thanks guys! :D
This community here is mighty helpful. *goes to mark as resolved* Edit: Oh, apparantly you can't do that in this subforum. :P

---

### Post by bodhi.zazen on 2007-12-04
4 gb is too big for swap. Typical is 1 Gb max, unless you are on a loptop in which case 2 Gb.

/ = 10 Gb is fine. with your large hard drive you could go higher, but it is not needed.

I would suggest a /data partition rather then such a large /home

Mount it in /media , give it a nice name like /media/music

/home 1 Gb

If you would like more ideas, see here :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

