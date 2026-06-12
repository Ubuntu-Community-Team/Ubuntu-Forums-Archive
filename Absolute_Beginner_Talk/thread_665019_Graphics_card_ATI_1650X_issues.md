---
title: "Graphics card ATI 1650X issues"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by RonnnL on 2008-01-11
After a bunch of non-working boot-menus and partitioning problems, I finally got Ubuntu installed, but another problem arises:

My ATI 1650X PCI-e graphics card is not recognized properly. After trying out the hints on the stickied topic on ATI-cards, I ended up with a system starting in low-res mode. I tried to revert to the ATI-drivers, re-enabling them, but now Ubuntu starts with a flickering / messed up screen.

I can start Ubuntu in 'safe mode', but since this is my first encounter with Linux, i'm not aware of all the terminal commands. I guess I have two options:

1) Re-install Ubuntu, then fix driver issues. Does the live-cd recognize my newly created main & swap partitions automatically as a basis for install? 
2) Fix the problem -somehow- from the 'safe mode'

System: MSI 945 P Neo 2, Intel Pentium D 2.8, 2.5 GB of Ram, dual booting Ubuntu 7.10 (G.G.) with winXP.

---

### Post by Hospadar on 2008-01-11
you might want to try using the envy scripts to completely remove any ati drivers currently installed and then install and configure the proper version for you.

here's their website:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I also understand that the guy who runs the envy project also has a repository to provide the absolute latest ati drivers, although that may not be necesary.

as for re-installation, you don't generally need to re-partition, if you choose manual mode at the partitioner, you can mount your main partition to root ("/") although this will still completely wipe any data on the drive.  If you have seperate data and home partitions though you can choose to only format the main partition to save data on the home partition.

---

### Post by RonnnL on 2008-01-12
Thanks, re-downloading the official ATI driver and configuring XServer did the trick!

---

