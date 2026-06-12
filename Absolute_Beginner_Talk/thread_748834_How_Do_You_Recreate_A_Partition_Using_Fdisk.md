---
title: "How Do You Recreate A Partition Using Fdisk?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by curtissthompson on 2008-04-07
**_Okay, before I go explaining my problem..._**

I did search Google and this forum among others to find a post that might have an identical problem, but came up short.  And I'm a noob when it comes to Fdisk on Linux.  My only Linux experience has been using Ubuntu for the past few months for a PHP and MySQL class I'm taking.  So I have basic understanding of using Ubuntu and a limited understanding of the Terminal in Ubuntu.

**_Now, my problem..._**

**What happened:**  I was chatting with a friend on my Windows XP laptop when my hand accidentally brushed over my laptop's mouse pad and switched the program focus from the instant message window to the My Computer window that I had open to the side.  I didn't notice this had happened until a couple seconds had pasted, so I continued typing while the program focus was on the My Computer window when I thought it was still on the instant message window.  Apparently my typing must've triggered a windows key command that messed with my partition.  When I caught myself and stopped typing, it brought up a prompt window telling me my drive was not formatted and then asking me if I wanted to format the disk.  I clicked cancel on that prompt.  Whatever happened, happened instantly, which has made me and a couple of my friends who I discussed this with think that it didn't delete the partition or anything, but instead messed up the partition table.

This is an external 500 GB hard drive that has important data I need to recover.  (Yes, I did have backups of the data, but I temporarily deleted them a couple weeks ago because I needed space on my laptop's hard drive for an application install and had planned on buying another hard drive in the near future anyways.)

A friend said that I could recreate/rebuild the partition using software tools, when I asked for a recommended tool to use to solve this problem my friend highly recommended using Fdisk under a Linux Live CD.

**_Here's where I need help..._**

My friend told me to use Fdisk on a Linux Live CD to see what's in the partition table in order to see what's there and what's missing, and to go from there about rebuilding the partition.

Can someone explain to me first how you use Fdisk to see what's on a partition table, and secondly how I go about fixing (rebuilding) the partition using Fdisk?

Any help would be greatly appreciated!  If you need more details than what was provided, let me know and I'll provide any more detail that I can.

---

### Post by Moop on 2008-04-07
Testdisk is what you need. It shouldn't be hard to recover your partition. 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

