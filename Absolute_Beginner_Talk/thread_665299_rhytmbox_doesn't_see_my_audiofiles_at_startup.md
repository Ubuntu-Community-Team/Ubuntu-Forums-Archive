---
title: "rhytmbox doesn't see my audiofiles at startup"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by project4 on 2008-01-12
Hi.
I have my audio files on a second drive which when I start up my laptop is unmounted.

When I start my rhytmbox it doesn't see my music. Only when I mount the drive manually, it starts to see the music again.

Also if before starting rhtymbox, I mounted the second drive there are no problems.

It is annoying that I have to mount the second drive everytime manually.

How can this be solved??

----
Note 1: the reason why i moved my music from ext3 to this second drive is because there was no space on ext3 anymore. 
Note 2: I dont know how many physical harddrives there are in this laptop. Its an Acer that I bought with Windows XP. There was a C and D drive...
Note 3: If the second drive is a partition... is there a way that I can remove this partition, increase ext3 and put all my music on ext3?
-----

Please help. Thanks!

---

### Post by dcstar on 2008-01-12
> **project4 said:**
> Hi.
I have my audio files on a second drive which when I start up my laptop is unmounted.

When I start my rhytmbox it doesn't see my music. Only when I mount the drive manually, it starts to see the music again.

Also if before starting rhtymbox, I mounted the second drive there are no problems.

It is annoying that I have to mount the second drive everytime manually.

How can this be solved??

----
Note 1: the reason why i moved my music from ext3 to this second drive is because there was no space on ext3 anymore. 
Note 2: I dont know how many physical harddrives there are in this laptop. Its an Acer that I bought with Windows XP. There was a C and D drive...
Note 3: If the second drive is a partition... is there a way that I can remove this partition, increase ext3 and put all my music on ext3?
-----

Please help. Thanks!

Install the **pysdm** package and use System-Administration-Storage Device Manager to mount the drive automatically.

---

### Post by project4 on 2008-01-12
> **dcstar said:**
> Install the **pysdm** package and use System-Administration-Storage Device Manager to mount the drive automatically.

Thanks dcstar! I just installed the pysdm.
I can see in the partition list sda1, sda3, sda5 and sda6. I checked with partition editor (gparted) which is which... by looking at the capacity. 

sda1 is where my music is. 
I see a general config tab, and dynamic config rules tab.
Where can I have the drive to mount automatically at start up. 
What is the code or commands to type in?

Thanks! :-)

---

### Post by project4 on 2008-01-12
dcstar, I did it. I went to the config page, selected assistance. and then checked the mount at boot-option, and the any user-option.

Now it starts up wonderfully, and rhytmbox is not loosing songs at startup.

Now If i can only get rid of the icon of the filesystem on my desktop... :)

---

