---
title: "How to:Partition for dual boot under mac and linux."
date: 2005-08-10
forum: Apple PPC Users
---

### Post by leverknight1 on 2005-08-10
This guide was created to guide new linux users that still want to run mac on thier powerpc machine and want to dual boot 

I wrote this using an iMac a Mac OS9 cd, an OSX cd just to install, and a new Ubnubtu linux 5.04 cd.

First i did this on a machine that was capable of booting from os9 because it was easier that way once i find a machine i can mess around with that cant boot from 9 then i guess i will do this guide for that point of view, but for now all i can say is if you are one of those people then i cant realy help sorry :neutral: :-?

Now to start the procedure boot off the 9 disk and open the utilities folder and start the drive setup utility. After it starts then click the initialize button once it brings up the screen to select the drive click custom and in the uppermost drop-down menu in the window click on the linuxppc format scheme this will make a mac and a linux partition along with multiple others click on the linux section and drag the top tab so that the mac portion expands on it is expanded click on it and make it hfs+ and make the size whatever is equal or at least enough to install 9 and/or 10. 

Once done with that click initialize again this will write the changes to disk and wipe all data on that disk MAKE A BACKUP IF NEEDED.  After the drive mounts on the desktop of your mac then go ahead and install os9 after that is done if you prefer to use 10 then boot off the 10 disk and go through the installer as normal.

After the mac side is all done with then install your linux by booting as normal and using the regular install. 
i ran into some trouble with the expert but that might have just been me. Once it is setup and you are at the drive partitioner DO NOT select erase entire disk at (your directory)  go to the edit partition table manually.
Once at the table go to all the ones that don't say apple or macintosh at the far right.   Only the ones that don't and delete those partitions by highlighting and hitting enter on your keyboard then selecting delete this partion at the bottom of the list that shows up.
This will create a large free space at the bottom of the list now once that is done go up to the guided partition section and select the instal in largest free space option and then after a window comes up select the instal all in one partition (for beginners). This will create a few directories where there was free space before now proceed with the install as normal and it should all auto configure around the mac side and even the boot-loader will show that there is a mac partition on the disk (if you did it right).

This hasn't been tested by anyone but me while i was writing it unless posted otherwise. please private message me if you encounter a problem that isn't related to just your system and i will try to help to the best of my ability.  Also as stated above i haven't done this booting off of an os 10 disk if you have tried please post results.

---

