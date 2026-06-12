---
title: "Partitioning for new install..."
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by ReaderRat on 2006-09-21
I already have windoze on (sda0,0) and would like to set up for dual boot with Ubuntu on (sda0,1). The partitioning part confused me (Mandriva is a little more user-friendly but has i$$ues.) How many partitions would be advisable, and how large should each one be? (I have half of a 320Gig HDD to use for Ubuntu.) Will I get an opportunity to designate what each partition is for, i.e.- /, /usr, /tmp, etc., and what partition designations should I include? I have read the book on partitioning and learned a lot, but I could find nothing specific on Ubuntu's partitioning. I am fearful of trashing my windoze partition which I need for a while (Until I learn Linux better. :-) )

By The Way, what does lol stand for? Lots of Luck? Laugh out Loud?

---

### Post by Metacarpal on 2006-09-21
> **ReaderRat said:**
> I already have windoze on (sda0,0) and would like to set up for dual boot with Ubuntu on (sda0,1). The partitioning part confused me (Mandriva is a little more user-friendly but has i$$ues.) How many partitions would be advisable, and how large should each one be? (I have half of a 320Gig HDD to use for Ubuntu.) Will I get an opportunity to designate what each partition is for, i.e.- /, /usr, /tmp, etc., and what partition designations should I include? I have read the book on partitioning and learned a lot, but I could find nothing specific on Ubuntu's partitioning. I am fearful of trashing my windoze partition which I need for a while (Until I learn Linux better. :-) )

By The Way, what does lol stand for? Lots of Luck? Laugh out Loud?

I use three partitions for Ubuntu - one for /, one for /home, and one swap partition.  If you have room for it, I recommend giving / at least 9-10 GB, so you have plenty of room to install different desktop environments to play around with.  :) 

After you create the partitions, you will be given the choice of where to mount each one.  And lol stands for laughing out loud

---

### Post by b_martinez on 2006-09-21
> **ReaderRat said:**
> I already have windoze on (sda0,0) and would like to set up for dual boot with Ubuntu on (sda0,1). The partitioning part confused me (Mandriva is a little more user-friendly but has i$$ues.) How many partitions would be advisable, and how large should each one be? (I have half of a 320Gig HDD to use for Ubuntu.) Will I get an opportunity to designate what each partition is for, i.e.- /, /usr, /tmp, etc., and what partition designations should I include? I have read the book on partitioning and learned a lot, but I could find nothing specific on Ubuntu's partitioning. I am fearful of trashing my windoze partition which I need for a while (Until I learn Linux better. :-) )

By The Way, what does lol stand for? Lots of Luck? Laugh out Loud?

Yes , you can opt for manual partitioning. As you probably read , you can only have 4 primary partitions, so make the 4th one an extended partition, and you v\can make more on that one. Keep root (/) on a primary. Make a SMALL /var, as this is where logs are kept. Largest should be /home. 
/opt is for optional programs, to keep from cluttering the / partition. /usr is for ???? (I don't know what exactly.

And lol is laughing out loud
hth
Bill

---

### Post by b_martinez on 2006-09-21
beat  me to it, metacarpal. and thanks for the swap reminder.

@ readerrat -->  swap is 'virtual' memory. RAMDISK memory that is
Bill

---

### Post by ReaderRat on 2006-09-21
> **b_martinez said:**
> Yes , you can opt for manual partitioning. As you probably read , you can only have 4 primary partitions, so make the 4th one an extended partition, and you **[COLOR="DarkOrange"]v\can make more[/COLOR]** on that one. Keep root (/) on a primary. Make a SMALL /var, as this is where logs are kept. Largest should be /home. 
/opt is for optional programs, to keep from cluttering the / partition. /usr is for ???? (I don't know what exactly.

And lol is laughing out loud
hth
Bill

What is the above: "v\can make more"? Is it used in Terminal mode?

---

### Post by karamba_kid on 2006-09-21
Use Logical Volume Management (LVM).  That way you can change the size of a partition if needed and you won't even need to reboot.  The LVM option is located on the alternative install disc.

---

