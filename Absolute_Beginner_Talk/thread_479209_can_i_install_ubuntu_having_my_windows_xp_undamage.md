---
title: "can i install ubuntu having my windows xp undamaged?if yes how?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by sonicker on 2007-06-20
can i install ubuntu having my windows xp undamaged?If yes how?How can i make a partion in my hard drive?

---

### Post by gdoermann on 2007-06-20
First it might be nice to know what partitions you already have.

Put the ubuntu disk in the drive and make sure your BIOS is set to boot from that drive first.  Then, when it loads Ubuntu, click the install icon and go through the language setup.  

When it asks about making a partition CHOOSE MANUAL SETUP!  change the  size of the Windows partition and add new partitions for Linux.  

You can also use Partition Magic to setup partitions in Windows (I find the Linux partition programs to be much easier, and complete).

---

### Post by buuntuu! on 2007-06-20
but first...
you need to defrag your xp-partition SEVERAL TIMES, best with JKDefrag, which works better than xp's own tool.
reading up the main info is also wise, try [psychocats]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by gdoermann on 2007-06-20
Oh... and don't forget to BACKUP, BACKUP, BACKUP!  You never know what might go wrong... especially your first time...

---

### Post by molly_001 on 2007-06-20
> **sonicker said:**
> ... sonicker wrote: 

can i install ubuntu having my windows xp undamaged?If yes how?How can i make a partion in my hard drive?



Your installation of Windows XP will not be damaged by installing Ubuntu.

Be sure to use the ***Alternate Install CD for Ubuntu 7.04***, and
follow the instructions here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by swoll1980 on 2007-06-20
You might want to try it out on a virtual machine first see if you want to keep it,s a lot easier to add/remove it that   
way let me know i will post some instuctions for you I did it this way. I liked ubuntu so much I got rid of windows all together but i guess its not for everyone

---

### Post by gdoermann on 2007-06-20
> **swoll1980 said:**
> You might want to try it out on a virtual machine first see if you want to keep it,s a lot easier to add/remove it that   
way let me know i will post some instuctions for you I did it this way. I liked ubuntu so much I got rid of windows all together but i guess its not for everyone

I wish I could just get rid of windows... but I wasn't thinking Linux when I bought some of my hardware (AIO Printer, web cam, etc.)

---

### Post by acowboydave on 2007-06-20
Hello, this is something new. try using Wubi 7.04 with Feisty alternate. to read more on this and to download Wubi go to  [http://www.cutlersoftware.com/ubuntusetup](http://www.cutlersoftware.com/ubuntusetup)  I have been running Ubuntu for 2 weeks with XP. You don't have to partition your hard drive it installs into XP itself it also uninstalls with no problems, at least for me it did. Defrag. your system first before trying.

---

### Post by gdoermann on 2007-06-20
> **acowboydave said:**
> Hello, this is something new. try using Wubi 7.04 with Feisty alternate. to read more on this and to download Wubi go to  [http://www.cutlersoftware.com/ubuntusetup](http://www.cutlersoftware.com/ubuntusetup)  I have been running Ubuntu for 2 weeks with XP. You don't have to partition your hard drive it installs into XP itself it also uninstalls with no problems, at least for me it did. Defrag. your system first before trying.

But then you have to deal with the windows kernel

---

### Post by tact on 2007-06-20
I have installed ubuntu (edgy and fiesty) on several winXP machines using the desktop liveCD.

After clicking the install to HDD icon you reach a point where it asks you where it should install.  Gives you the option to blow away the whole HDD and use that.  Of course this is not the option you'd choose. :)

I think the option you'd best choose is called "guided manual"  (??? if memory serves me correctly.) to make some space on the HDD.

After choosing this option you are then presented with a slider that represents how much of the HDD is freespace.     e.g. if you have an 80GB HDD and just one winXP partition that has used something like 60GB - then this slider represents the free 20GB.     You move the slider to tell ubuntu installer how much of the free 20GB it can have.  

(In a case like above - dont give ALL freespace to ubuntu.  Else you will be in a mess next time you boot winXP cos it will boot and complain there is zero free disk space! and likely lock up.  Leave windows several GB to play with.)

Once you select how much of the HDD ubuntu can take - it will automatically repartition your HDD, shrink the XP partition and make its own partition.

I have done it several times, guided manual, or fully manual (not recommended until you REALLY understand how ubuntu needs partitions allocated) and never have I had a problem with winXP after install.

---

### Post by sonicker on 2007-06-26
THX u people for helping me out.................and i hope to get answers from u later on also........peace.........;):D:o

---

