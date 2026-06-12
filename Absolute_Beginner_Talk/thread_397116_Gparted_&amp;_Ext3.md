---
title: "Gparted &amp; Ext3"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-03-30
I am preparing a new computer with 2 new hard drives. In anticipation of installing Feisty next month, I decided to get a head start and partition the drives using the gparted Live CD. 

The first issue was which type of disklabel, but after doing a little research it seems selecting msdos would be most practical. Eeven though it will be a pure Linux machine I don't see any advantage to the gpt disklabel on a desktop computer.

When I booted the CD and began the gparted partitioning, it seems that only ext2 partitioning/formatting was available. I want ext3 formatting but couldn't find a way to select that. I've decided to wait until Feisty comes out and starting over with the installation disk. I expect that disk will give me the option to partition the disk and will also allow me to format it in ext3.  

Am I missing something on the gparted live CD and do my actions (inaction) make sense?

---

### Post by laidback on 2007-03-30
I'm sure somthing's up because you should find that various types are available including ext3, which is what I use. Did you :-
select an unused area of the hdd to be partitioned (click on it within the diagram) then
click Partition>New, then
Click Filesystem drop down   where you will see a whole list of formatting options.

It's also possible that you are selecting an area that's already formatted. Delete it first, then try again.

The partition you wish to reformat must be **unmounted** first, in Linux you cannot format a mounted partition.
Gparted documentation here:-
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

---

### Post by drs305 on 2007-03-30
I am trying to use the gparted live cd on two brand new hard drives. I don't even know if they are formatted. There aren't any partitions on the drives as yet and they sholudn't be mounted as there is no system (linux, Windows, etc) on the drives.

What you describe is what I've seen when installing Edgy on an older machine when the installation gets to the partitioning section.

---

### Post by zvacet on 2007-03-30
If I understand you correctly you have two new HDD with no partitions on them.How do you expet from Gparted to see something that doesn´t exist?If this is truth you don´t need Gparted because as you said Ubuntu will partition your drives as you wish.

---

### Post by drs305 on 2007-03-30
> **zvacet said:**
> If I understand you correctly you have two new HDD with no partitions on them.How do you expet from Gparted to see something that doesn´t exist?If this is truth you don´t need Gparted because as you said Ubuntu will partition your drives as you wish.

I didn't expect gparted to find partitions, I expected it to make them. Can't gparted set the partitions? I thought that is the program I've used in the past to set and/or resize partitions on hard drives already in use. In any case, I'll wait until installing Feisty and then just do it all at once.

SOLVED:
OK, problem solved. I didn't have a mouse enabled and had to have everything input via the keyboard. I believe I hadn't tabbed through the options and highlighted a section of the harddrive. So for anyone else as clueless as I, without a mouse you will use a combination of tabs to move about the lower menus, space key to change an option (ext2, ext3, ...) once the you've tabbed to the appropriate button. To access the top menu, hit the F10 button and then left/right keys to move laterally.

---

