---
title: "Absolute Beginner, Crashed Laptop and Recovery CD doesnt work, Turning to Linux..."
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by b-rose on 2007-10-01
Hello all. So here is the story. Hopefully someone can help me out with this as my computer is far to young to buy a new one. Oh.... and I am an absolute beginner when it comes to linux, but I do have some general computer knowledge.

I have had an Acer 5672wmli laptop that I have loved for almost 2 years. It started running really slow so I tried rebooting with the factory restore disk. Aparently there was something wrong with the disk as 1.5 minutes in it said it was missing a file needed and shut down. Everything had been erased and I was left with no operating system on my computer. Not thrilled.

So I turned to Ubuntu, loaded up the live CD and played around with it. I liked it and it was free, so I decided to try installing it through the live CD. Didnt work. Something about failure to partition section 5 swap. I rebooted and now it wont let me run the Live CD as all, it runs through numerious I/O errors.

I downloaded the Alternate CD to see if I would have better luck there. I go through install and when I get to partitioning it always fails on the ext3 partition.

I tried nukeing the drive and starting over with a sysres cd that was recommended in a past post to start over and it finished with non-fatal errors, but I think it got most of the way through.

I am at work right now so I cant play with it and get some exact errors for you guys, but I wanted to get the ideas flowing right now and when I get home I can get some more specific info for you.

I appreciate any assistance anyone can offer. It's gonna be a long journey and I will be greatful to anyone willing to jump aboard!!!

Brett

---

### Post by mivo on 2007-10-01
Hmm, sounds almost as if the hard disk may be physically damaged.

---

### Post by b-rose on 2007-10-01
Ohhhh.... thats something I dont want to hear!!!](*,) ;)

If it becomes consensus that the harddrive is the problem, what are we looking at price wise for a new harddrive for a computer like this? Similar size and everything?

---

### Post by quinnten83 on 2007-10-01
Yup, that would be my diagnosis :)

---

### Post by b-rose on 2007-10-01
It is a 120 GB SATA hard drive by the way.

---

### Post by quinnten83 on 2007-10-01
> **b-rose said:**
> Ohhhh.... thats something I dont want to hear!!!](*,) ;)

If it becomes consensus that the harddrive is the problem, what are we looking at price wise for a new harddrive for a computer like this? Similar size and everything?

Depends where you live.
In most of europe you pay around  €1 for 1 Gb .

---

### Post by mivo on 2007-10-01
Little bit cheaper here in Germany, but definitely much cheaper in the US. I don't know much about notebooks, though, so I can't say how easy it is to replace a disk in a mobile system. Newegg.com has 120 GB SATA disks for under $70. See [here]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822149065").

---

### Post by b-rose on 2007-10-01
You guys are awesome, thanks so much for the help. Acer is only interested in selling me new reboot CD's for $40 bucks even though it was their system CD that was faulty. Needless to say I am very disenchanted with windows and acer right now so I am very interested in moving forward and learning something about linux. Has anyone replaced the hard drive in a laptop. What are we talking about on a difficulty scale compared to doing a desktop replacement?

---

### Post by cubeist on 2007-10-01
Can you re-format the whole drive? As in, do you have data that you haven't backed up on the drive?  If you can re-format, you might want to try a gparted live cd (gparted.sf.net) and manually partition your hard drive.  Linux needs two partitions to run.  The main partition should be an ext3 of any size you want, and a swap partition, usually around 2GB.

Just remember that partitioning from a gparted live cd will erase ALL YOUR DATA!

---

### Post by b-rose on 2007-10-01
I have tried nuking the entire disk and partitioning with ubuntu and tried partitioning with the partition manager off of the sysres live cd. (I think its called ranish or something like that) I tell it to write the partitions and save and it says it does. I then reinstall the Ubuntu alternate install disk and it says that no partitions have been written.

---

### Post by cubeist on 2007-10-01
> **b-rose said:**
> I have tried nuking the entire disk and partitioning with ubuntu and tried partitioning with the partition manager off of the sysres live cd. (I think its called ranish or something like that) I tell it to write the partitions and save and it says it does. I then reinstall the Ubuntu alternate install disk and it says that no partitions have been written.

My thinking is that if you can successfully partition via a gparted live cd, then you can bypass the partition part of the install cd (which seems to be causing the errors)... you can just select which partition to write to...

It's probably worth a try before buying a new hd...

---

### Post by ajgreeny on 2007-10-01
Worth trying what cubeist suggests.  The gparted live CD is an awesome piece of software that does tricks that have helped me out a few times in the past with partition management.  Give it a go; delete any partitions it finds first than make two new ones, a linux swap formatted one of about 1GB and the rest formatted as ext3 for the system.  At this stage I wouldn't worry about separate /home at this stage as you can deal with that once you are sure the disk is usable.

If that works and you can then install OK on these new partitions, you could make a separate /home partition if you wanted, but perhaps worth finding out the joys of using linux first and then dealing with other less important details later.

---

### Post by Henry Rayker on 2007-10-01
I haven't replaced a hd in my laptop, but I've removed it so that I could dust underneath it...it's incredibly simple...at least on my laptop.

I just had to open the proper panel on the bottom of the machine, lift the side of the drive furthest from the pins up and pull out. The pins on my laptop are sort of hinged, so that you can lift the drive, but don't lift too far...you may break them. I just lifted far enough that pulling straight out would clear the rest of the case.

Hope that helps.

---

### Post by b-rose on 2007-10-01
You guys are absolutly awesome!!!!!

Thanks so much to everyone for their suggestions. I will try the gpartition live cd tonight when I get home and keep everyone updated. If anyone else has any ideas or advice for someone like me switching over cold turkey keep it coming!

---

### Post by b-rose on 2007-10-01
OK guys, I tried to run gparted and I got tons of I/O errors and it wouldnt let me load up the graphical interface. So I ran a test disk, it said there were two partitions, tested the swap and it checked out. Tested the ext3 and it went psycho with a million i/o errors. Does this sound like a Hard drive error. If so, I am looking at two hard drives. a seagate with Ultra ATA or a Western Digital with SATA. Which would you recommend for ubuntu?

---

### Post by Fixman on 2007-10-01
Dude, here we have to pay 300$ for 80GB of disk!

---

### Post by midnightracer on 2007-10-01
> **b-rose said:**
> OK guys, I tried to run gparted and I got tons of I/O errors and it wouldnt let me load up the graphical interface. So I ran a test disk, it said there were two partitions, tested the swap and it checked out. Tested the ext3 and it went psycho with a million i/o errors. Does this sound like a Hard drive error. If so, I am looking at two hard drives. a seagate with Ultra ATA or a Western Digital with SATA. Which would you recommend for ubuntu?

I would personally go with a hitachi laptop hard drive because they are really durable. BUT, whatever company you do choose, be sure that it fits your computer. Is your hd now a SATA? BTW- I have been using ubuntu now for about a year as a dual boot with windows. Last week I threw windows out the door and am using only ubuntu. Once you get to know linux, you WILL love it.

---

### Post by cubeist on 2007-10-01
> **b-rose said:**
> OK guys, I tried to run gparted and I got tons of I/O errors and it wouldnt let me load up the graphical interface. So I ran a test disk, it said there were two partitions, tested the swap and it checked out. Tested the ext3 and it went psycho with a million i/o errors. Does this sound like a Hard drive error. If so, I am looking at two hard drives. a seagate with Ultra ATA or a Western Digital with SATA. Which would you recommend for ubuntu?

Gee, that's too bad.  It definitely sounds fried.  I am sure there is a way to fix it but it is well beyond my ability.  As for a new hd, for my desktops I use seagate because they come with cache that really helps speed up the drive and they make barely a whisper of noise.  However, these days I think most major brands are comparable... Just stay away from a noname made in China drive!

---

