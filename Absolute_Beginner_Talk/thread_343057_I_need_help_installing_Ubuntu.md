---
title: "I need help installing Ubuntu"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Douglas B. on 2007-01-20
Hi everyone
        This is my first post; I just joined the Fourms a few min. ago. So if I'm not doing this right please let me know.  I have Ubuntu 6.06 installed as the only opperating system on an older computer. What I want to do is install Ubuntu on my laptop. It's a new Acer with a 160 GB hard drive. It is already partitioned into two equal C and D drives. It is using the D drive to store my backup files as the computer didn't come with any discs. 
         My problem is,,,,,,,,,,,,,,,If I put in the Ubuntu disc and tell it to install , [ I want to save my Windows XP ]. what will it do. Will it leave the C and D partitions alone:p  and make a new third partition? 


        I really don't want to have to reinstall Windows.
                                                                        Thanks guys
                                                                               Doug

---

### Post by zekopeko on 2007-01-20
by default it will install a boot loader (GRUB) so that you can choose between the OSes.

ubuntu also has it's partition editor so you can partition it during the install.

your 160GB drive has C: and D: partition right? Ubuntu will shrink the partition you say.
i guess that win is on C: so you will want to partition D: (or which ever is the larger one)

i gave a 120GB drive also with C and D partitions. C: is 15GB for win and D: (50GB win partition) is for games,video,music. Before D was 100GB but with ubuntu installer i partitioned it to 50GB.

first you should defragment the partition you are going to resize a couple of times.
after that put the ubuntu liveCD and let it boot.
run the installer on the desktop and follow instructions.
when you get to the part with partitioning you should resize the partition to size you want to give it. that way you will have XX GB of free space to install ubuntu.


choose to MANUALLY edit the partition table. be careful with this part so that you don't delete win partition by accident. 
first you resize the free space and then mount(give the partitions their 'use' like root, swap, personal(HOME)) the partition.
i suggest 10 GB for '/' (root - this is where all you program will go and system stuff) and XX GB for '/home' and 1GB for swap.


here is a link with pictures : [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Shatrat on 2007-01-20
It gives several options on disk formatting, youll want to resize your windows partition I believe.
I think it will offer to do this automatically but I use the manual resizing tool.  You could also use Gparted which is in the System of the Live CD to resize the windows partition and then install to the empty space you create.

This might help you know what to expect.  Your options on the partitioning section will be different because of your partitions.
[http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html](http://www.debianadmin.com/ubuntu-edgy-eft-desktop-installation-with-screenshots.html)

---

### Post by Douglas B. on 2007-01-22
Thanks for the help guys. It almost seems to easy. I'l take the first option and let it do everything,,ha  ha
                                                    Thanks again
                                                               Doug

---

