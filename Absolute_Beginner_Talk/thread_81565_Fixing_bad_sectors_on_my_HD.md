---
title: "Fixing bad sectors on my HD"
date: 2005-10-24
forum: Absolute Beginner Talk
---

### Post by AmboyGuy on 2005-10-24
I've been reading and searching the forums, I need to do an equivalent to windows 'Scandisk' function.
I've been plagued since I started trying to install Ubuntu 5.04, 8 days ago, by bad sectors on my hard drive. ( I think it failed the 2nd story drop test at some point in it's life ). 
I know the command 'fsck' is what I want to use but I can't get it to work on the swap partition and I also found out ( the hard way ) that executing on the root partion can cause major problems.
Can anyone help me with the steps to map/repair 'all' the bad sectors in all the partitions on this demonically possessed hard drive?

Do I need to use the 'Live CD' ?

---

### Post by poptones on 2005-10-24
What kind of hard drive do you have? If it is still under warranty you need to look into getting it fixed the proper way. Many hard drives made a couple years back were plagued by bad sectors developing; seems it had something to do with platter production in china and one supplier not being particularly good at it.

Anyway, you really cannot fix those bad sectors with an fsck. What you need to do is make the drive remap those sectors, and that will mean working more low level. You CAN do it the geeky way (possibly) but it's fairly tedious and if your drive is failing it will be only a temporary fix. Here's what I suggest you do: go to the manufacturer's website and download their diagnostic tool. Seagate has one and Maxtor has one called "gwscan" or something. You can download it as a bootable iso- burn it to a cd, reboot, and run an extended test. It's likely to find errors and if it can it will offer to remap them. Let it do its thing and then reload your system. 

The better suggestion I will give you is to proceed with the "repair or replace" option, though. Hard drives are too cheap nowdays to pull your hair out over something like this.  I have lost three maxtors in the last couple of years all due to this stuff. The only upside is after sending in 160GB drives for repair they returned to me 250GB drives.

---

