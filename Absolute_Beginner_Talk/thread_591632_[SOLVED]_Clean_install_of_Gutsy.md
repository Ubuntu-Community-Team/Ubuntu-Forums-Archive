---
title: "[SOLVED] Clean install of Gutsy"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by dndrich on 2007-10-25
OK, I currently have Feisty installed on a laptop dual booting to windows XP.  So, I have 4 partitions:

1 tiny fat 16 for some kind of Dell recovery, 1 large NTFS for windows, 1 ext3 for Ubuntu, and 1 small swap.  Now, I ran the live CD, and have gone to manual partitioning.  I simply want to replace the Feisty install for the Gutsy install clean, and leave everything else.  What choices to I make under gparted?  I am afraid to mess up the windows partition, so I aborted the install.  Do I delete the partition, and then choose it to be "/"?

---

### Post by Pumalite on 2007-10-25
Post:
sudo fdisk -lu
To make sure we know what partition you are supposed to install to.

---

### Post by jpittack on 2007-10-25
I too have a dell.  I set up my ubuntu / in a logical partition inside of an extended partition, along with the swap and /home on its own partition.  I have two recovery partitions from dell, so another fat32 partition I use to save files between the two os' is inside of the same extended partition, but you could choose to give it its own partition.

This is the way I have found most useful.

---

### Post by dndrich on 2007-10-25
I know which partition is the one.  It is the ext3 partition.  I just need to know the steps in gparted when it asks me during manual install.  Do I erase the partition, and then make it "/"?  I don't need to run fdisk -l...I know which partition it is.

---

### Post by Incense on 2007-10-25
When you are running the installer, just select manual from the partition section, and set the 7.04 part to / and check the format box. It will delete everything from that part (data and all ) and do a clean install leaving your other partitions in tact. Wouldn't hurt to back up your windows install first though JIC.

---

### Post by dndrich on 2007-10-25
OK, that is the answer I was looking for.  I'll try it.  Thanks!

---

### Post by Happy_Man on 2007-10-25
K, here's what you do. Don't use the installer. Go to System --> Administration --> Gparted/GNOME Partition Editor. 

Right-click on your big ext3 partition. Delete it. 
Right-click your swap partition. Delete it. 
Right-click on the now empty area. Select to create an extended partition. Have it use the entire space. 
Right-click inside the new extended partition. Create a 512 MB swap partition. 
Right-click in the empty space next to the new swap partition. Make a new 7 GB partition. Make it ext3.
Right-click in the remaining empty space. Create a new partition that uses the rest of the space. Make it ext3.

Apply the changes. Then exit GParted.


Now open up the installer and run through it until you get to the partition screen. Choose Manual. 

Now, right-click the 10 GB partition, and set it as / .
Right-click the other ext3 partition, and set it as /home .
Now go ahead and let it install.

If you ever need to reinstall, *only format the 10 GB partition*. This is because the /home folder (which has all your files) is now on a separate partition from the rest of the OS. On the upside, though, you won't need to backup every time you reinstall. :)

Hope this helps!

---

### Post by Incense on 2007-10-25
Good call on the separate /home. Didn't think about that.

---

