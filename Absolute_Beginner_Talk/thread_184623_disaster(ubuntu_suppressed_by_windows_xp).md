---
title: "disaster(ubuntu suppressed by windows xp)"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-30
](*,) 
      
   hey friends 
                 i need your kind help.i am in biggest trouble of my computer life.plz read the story upto last line
   i was using a dual boot system with windows 2000 and ubuntu 5.10
i'd a window version of matlab 7(a software of engineerin and maths).its requirement was windows xp .so i'd to install windows xp.
saddddddddddddddddd!
   after the installation i can't see the grub boot loader option showing me which system i want to boot.then i tried all means to shut downing ,rebooting etc to see my grub loader but i could'nt.

i have very important data on my pc in ubuntu directory,not only this ubuntu itself is too much important for me .u can see my posts and imagine.

i want to recover every thing.i want to see my grub loader.

however ,i also tried to reinstall my ubuntu by inserting its install cd,but since i am not an expert,i use default installation which i previously used.in guided partition selection ,it does't show me my partitions.it just shows me my entire hard disk and says
   1-erase entire disk
   2-use free space

it also has some other options which fly over my mind.

however both options are acceptable

1-recover preinstalled ubuntu
2-reinstall ubuntu with formatting only the partition in which ubuntu is.

but the second choice is ultimate choise if in any case i can't recover my ubuntu.

i have installed xp today.i have its installer myself.so i can sacrifice xp,if it is required to recover ubuntu.

plz specify full guide to me.i am beginner to linux.

i am online here until i can't get what i want.so u can also try your attempts by sending me your suggestions. plz don't hesitate.


thnx in advance bcoz i believe all of u would try to help me

---

### Post by Rinzwind on 2006-05-30
Do not reformat any partition.
Brb with more (need to find some instructions so you can use Grub again).

EDIT:  same problem here:
[http://www.ubuntuforums.org/showthread.php?t=184390&highlight=REINSTALL+grub](http://www.ubuntuforums.org/showthread.php?t=184390&highlight=REINSTALL+grub)
EDIT2: info about reinstalling Grub here: 
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Here are the steps

   1. Boot your computer with Ubuntu CD.
   2. Go through the install process until you reach "[!!!] Disk Partition."
   3. Select Manualy Partition.
   4. Mount the appropriate linux partions:
      /
      /boot
      swap
      DO NOT FORMAT THEM
   5. Finish the manual partitioning.
   6. Select "Yes" when it asks you to save the changes.
   7. It will give you errors saying that "The system couldn't install ....." after that; ignore them. Proceed with selecting "continue" until you get back to the Ubuntu installation menu.
   8. Jump to "Install GRUB."
   9. Once it is finished, simply restart your computer.

---

### Post by Engnome on 2006-05-30
There are many threads about this here, yours is probably nr. 25 about it. (sigh)
Use the search function.

Just to be nice heres one:
[http://www.ubuntuforums.org/showthread.php?t=183345](http://www.ubuntuforums.org/showthread.php?t=183345)

---

### Post by zapcojake on 2006-05-30
The windows installer doesn't recognoize Linux in any form, when you installed xp it copied its own boot loader to the mbr thus making Ubuntu unbootable.  this will happen everytime you install windows. I suggest getting windows installed just the way you want it before recovering linux.  Also, there are some programs for mounting ext file systwms in windows.  they are a little twitchy but might help some.   Paragon hard disk manager is a decent one.

---

### Post by u04f061 on 2006-05-30
[QUOTE=Rinzwind]Do not reformat any partition.
Brb with more (need to find some instructions so you can use Grub again).

EDIT:  same problem here:
[http://www.ubuntuforums.org/showthread.php?t=184390&highlight=REINSTALL+grub](http://www.ubuntuforums.org/showthread.php?t=184390&highlight=REINSTALL+grub)
EDIT2: info about reinstalling Grub here: 
[http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub)

Here are the steps

   1. Boot your computer with Ubuntu CD.
   2. Go through the install process until you reach "[!!!] Disk Partition."
   3. Select Manualy Partition.
   4. Mount the appropriate linux partions:
      /
      /boot
      swap
      DO NOT FORMAT THEM
   5. Finish the manual partitioning.
   6. Select "Yes" when it asks you to save the changes.
   7. It will give you errors saying that "The system couldn't install ....." after that; ignore them. Proceed with selecting "continue" until you get back to the Ubuntu installation menu.
   8. Jump to "Install GRUB."
   9. Once it is finished, simply restart your computer.[/QUOTE]

as i mentioned in the post that i inserted cd and went to manualy partion but it does not show any partitions.
it just says that erase the entire hard disk or use free space
and also it does not show me how much free space is.it says free space starts  from (0,0,0) to (xxx,xxx,xxx);

---

### Post by Sef on 2006-05-30
Have you followed these directions:

[RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29%7C%28restore%29")

---

### Post by zvezdogled on 2006-05-30
[QUOTE=u04f061]](*,) 

i'd a window version of matlab 7(a software of engineerin and maths).its requirement was windows xp .so i'd to install windows xp.
[/QUOTE]

I used to use matlab a lot (I study physics) until i found out about octave. 
The program is basicly the sam; it supports .m files and the commands are alike. 
Octave is much simpler not graphical (you run it in a terminal) and it usese gnuplot for drawing.

I remembered.
Have you tried a windows program for viewing ext2 and 3 partitions, such as explore2fs?

---

### Post by u04f061 on 2006-05-30
[QUOTE=Sef]Have you followed these directions:

[RecoveringUbuntuAfterInstallingWindows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28grub%29%7C%28restore%29")[/QUOTE]

now i am writing after  doing that thing.let me explain what i did

1-inserted disc
2-typed rescue
2-laguage selection,server,etc
4-it showd me five partitions ,without mentioning their size

i was much shocked to see this that my disc is three parted and what is this.
i think this bcoz widows takes 8mb secure and ubuntu takes 380mb.so three are my main partitions and two are these.

it was difficult to think which partion is root.then i went back in imagination and came to know that 
/dev/discs/disc0/part2 is root

i selected this and it opened somewhat like yhis

sh-3.00# 
i don't know exact but it was something like that.the end character was # i think!
in the top was written 
rescue mood

then i wrote
$grub-install /dev/hda2
 and pressed enter.than it said no file found or something like no directory found

---

