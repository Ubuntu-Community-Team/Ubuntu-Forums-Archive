---
title: "OS will not boot after failed partitioning of HDD, really need help"
date: 2008-04-11
forum: Absolute Beginner Talk
---

### Post by quanta4135 on 2008-04-11
Hi - A few months ago I purchased a new laptop for school with Vista preinstalled. I wanted to try Ubuntu, but keep Vista for my games, so I decided to partition the drive. I started gparted and went off to work for a few hours, but apparently forgot to plug in my laptop. Ubuntu suspended sometime during that time, so when I opened my laptop there were error messages on the screen. Apparently the process did not finish, and that turned out to have bad results since I could no longer boot Vista in any mode. After the loading bar, my monitor will only display a black screen with a movable cursor. I could still access my files on the HDD from starting up the Ubuntu CD, so I moved my important files onto a USB drive. After running some of Window's diagnostic tools, Ubuntu can no longer mount the drive. I know this is not really a Ubuntu problem, but the people at Microsoft were not entirely helpful and I am desperate for help. Thanks

---

### Post by bt224 on 2008-04-11
You might want to do a clean install of Vista. Sounds nasty.

---

### Post by Jon Monreal on 2008-04-11
> **quanta4135 said:**
> Hi - A few months ago I purchased a new laptop for school with Vista preinstalled. I wanted to try Ubuntu, but keep Vista for my games, so I decided to partition the drive. I started gparted and went off to work for a few hours, but apparently forgot to plug in my laptop. Ubuntu suspended sometime during that time, so when I opened my laptop there were error messages on the screen. Apparently the process did not finish, and that turned out to have bad results since I could no longer boot Vista in any mode. After the loading bar, my monitor will only display a black screen with a movable cursor. I could still access my files on the HDD from starting up the Ubuntu CD, so I moved my important files onto a USB drive. After running some of Window's diagnostic tools, Ubuntu can no longer mount the drive. I know this is not really a Ubuntu problem, but the people at Microsoft were not entirely helpful and I am desperate for help. Thanks
You should take a look at this [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm).

One user posted there the following comment:
> If you are having problems after installing Ubuntu booting into Vista (if you get the Vista progress bar and then a black screen)..

this is because Ubuntu messed up the NTFS tables. This is easy to fix!

Check this out
[http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122)

I did it and I booted into Vista again..whoo hoo!

I didn't even loose any data


I would check [http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122) first. It would seem that it contains at least one possible solution. Be careful, however, to make sure that the solution does not further complicate the problem.

If you are still having problems with your installation, just say so.

Hope this helps you.

---

### Post by 19bab79 on 2008-04-12
you could possibly put in your vista recovery disc and repair the boot record. you might even have to repair the whole vista install.

---

### Post by quanta4135 on 2008-04-30
Thank you, that worked great! I didn't lose any of my data, and thanks for that link to APC, I used the guide that guide to insall Gusty on my brothers laptop. However, when I got to the step 4, and selected to use the largest continous unallocated space I got the message "No root file system is defined." Ugh, can anyone help me out with this one, I really don't want to seriously mess around with his computer.

---

### Post by bumanie on 2008-04-30
Sounds as though you have vista working, due to a repair of the mbr. As far as things go at present, you should do a chkdisk with vista to ensure the hard drive doesn't have any bad sectors. Also before installing ubuntu (if chkdisk is clear), it is best to defrag vista before continuing with an ubuntu install. You could partition the disc prior to installing ubuntu. With vista it is best to use the vista disk manager to shrink your vista partition and then use gparted to format the rest of the hard drive to ext3. (There have been issues reported with gparted and vista, but gparted works fine with xp though). 
If I were you, I would try to use manual at the partitioning stage. You can then have the mandatory / and swap partitions as well as make an extra /home partition. This way if ubuntu's file system mucks up, you only have to reinstall to / and all your data in /home is safe. Size / to 6-8gb, swap 1-2gb and /home as large as you like.

---

