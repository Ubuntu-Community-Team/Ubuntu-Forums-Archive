---
title: "Home Server Planning"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-06-27
I have been thinking round a home server for a while.   The more I think the more I sink.  Any ideas please .....

I want the server to do the usual .... email, proxy browser, data backup, audio and video media management and similar.  Nothing shattering.

Here is the problem ....  I have four 500 GB SATA HDD's.  Three are 100% full with movies, music and graphics.  The last is on the way to being full ....    I want to use these HDD's on the server as a raid without loss of data in setting it up.  Can I just drop them in place? Can this be done or does it not work like that?

I anticipate using raid 5.   Does this seem inappropriate?

It seems that I have a number of choices – buy a motherboard with raid 5 built in.   Buy a controller card and plug that in or use a software solution.   I read that replacing controller cards in the event of failure (and the same for motherboards) can mean some very fundamental problems in getting the drives to run again without data loss.  Is the software solution the solution of choice or what?

Given that I do not need to access most of the drive content most of the time, would be be better to install the drives as some form of network storage which is only powered on when it is likely to be needed.  This will no doubt save in energy consumption as well as making it easier to set up.

Perhaps I should focus on getting a server up and running first (since the scripts can be a pain to get right) and then think about a raid ...

If you have any observations / ideas / links to look at .....  I would appreciate if you would share ...

---

### Post by tim.n9puz on 2007-06-27
If you have nearly 4 drives full of data I don't think you have enough storage space for any sort of RAID array. Different types of RAID (0-6) utilize multiple disks in different ways to more safely store your data so it is recoverable if there is a drive failure. I have not used RAID 5, my systems use RAID 1, but you would end up having total usable storage of 500GB with a RAID 5 system having four drives.

In general if you are new to servers and RAID I think it would be a good idea to get another drive of some sort and learn to setup the various server functions you mention to learn all the ins and outs without risking your data. Once things are sorted out you can use the notes you make along the way and the server configuration files to configure and build what you want for "production". Everyone is different but in my experience attempting too many things new to you all at once vastly increases the chances of having problems.

TM

---

### Post by expatCM on 2007-06-27
Thanks for your reply.   I do not disagree with your comments .....  setting up the individual programs and getting them to work is going to be something close to a headache.....  and perhaps best addressed first.

One of your comments I find interesting though ......you indicated that you thought that I would end up with usable storage of about 500GB (presumably per drive).  This is very interesting ....   I format the drives at present to FAT32 and the formatted volume is about 465GB.  Do I interpret your comment correctly in that you are suggesting that the available storage for each volume would fundamentally increase using raid?  I think you are not suggesting 75% redundancy ....    If I am able to save about 35GB per drive then this gives me quite a lot of cumulative extra space...

---

### Post by bigken on 2007-06-27
take a look [here ]("http://www.trustedreviews.com/storage/review/2005/10/21/The-Rules-of-RAID/p1")

---

### Post by skirkpatrick on 2007-06-27
Basically (if I remember correctly), using RAID5 your total storage is (n-1) * drive_size.  So 4 500GB drives would give you 1500GB of storage, not the 2000GB you'd think.

Also remember that drive sizes are typically shown where 1GB = 1,000,000,000 instead of the 1,073,741,824 that is calculated by your OS, which is why your OS reports that a 500GB drive has 465GB of space (this is assuming that there are no bad blocks on your drive and there always are).

---

### Post by Pinger05 on 2007-06-27
By your description you have nearly 2Tb of data.  In order to get 2Tb of data storage out of a server you will have to use RAID 0 (No raid) or get 5 or 6 2Tb drives as RAID 5 just to meet your present needs.  

My advice is to either use RAID 0 or go through your data and remove the unnecessary stuff.  But that is just my advice.

---

### Post by expatCM on 2007-06-27
I seem to be reading a common message in this thread from all you helpful people .........  It seems to be that I should keep the server and the storage as separate vehicles; and not having too high expectations about what I am going to get out of raid storage.

Just to comment on the responses - 

bigken - great link, lots of information there.  Pity they do not have a print version but hey ..  it is good material.

skirkpatrick - oops ... so I am going to need to buy even more storage to simply stand still.  The one advantage I see though is that if (when) a drive fails, recovery is not an impossible event.

Pinger05 - I had no idea that they make 2TB drives.  I suspect that I will not like the price though.   There is no data to remove, it is all good.

I asked for advice and ...  wow I am getting it :)    There is something called NAS which I guess I will also need to research since my understanding is that this will make the storage available as a network device.  It is all starting to sound a bit expensive though....

---

### Post by bigken on 2007-06-27
im sure if you do a bit of googling and keep asking here you will get your answers

---

### Post by Limpan on 2007-06-27
> **expatCM said:**
> 
Pinger05 - I had no idea that they make 2TB drives.  I suspect that I will not like the price though.   There is no data to remove, it is all good.

I don't believe there are any 2TB disks available. He simply stated that with your four 500GB drives in a RAID0 'stripe' or in JBOD you would get a 'virtual' 2TB disk.

*If you were I, I would go about it this way:*
**1)** First of all, buy a motherboard with many S-ATA connectors, preferably eight but six would do. I would choose a dual core AMD system as they are a little cheaper and that performance won't be that important. Any modern CPU is going to get the job done. Get a powerful PSU, at least 500W if you're following my advice at step 4. Don't buy some cheap crap.

**2)** Get a reasonable disk to run the system from. Almost anything would do, buy whatever you like. No need for a 500GB disk for the system, 20GB would probably be sufficient so pick something cheap.

**3)** Test out your system and take the chance to play around a bit. Learn as much as possible. When you feel that you know your way around, proceed to the next step.

**3.5)** If you have two ATA connectors on your motherboard you could dig up some old disks and test some RAID configurations with them. It would be nice to know how to do before you commit and buy lots of disks. The capacity of the disk doesn't matter, anything from 4GB and upwards would be enough to test with.

**4)** Buy as much hard drive capacity as you need. You will need at least one disk for parity (in RAID5, two for RAID6) and it would be good (but not necessary) with one extra drive as a hot spare. This means that you will probably need 5 or 6 disks (500GB). (It is also a good idea to keep the system and data on separate partitions and the RAID array will almost force you to it.)

With 6x500GB you would get an array with the total capacity of 2.5TB (no hot spare) and if you use 6x750GB you would get 3.75TB.

To be able to move all your current data (2.0TB) over to the array you would need at least 5x500GB (usable capacity 2.0TB) or 4x750GB (usable capacity 2.25TB).

There is unfortunately not any way to use your current disks in the array without erasing them. If you want to use them you'll need some temporary location, guess that burning over 400 DVDs ain't that fun.

Hope this helped at least a little.

---

### Post by tim.n9puz on 2007-06-27
> **expatCM said:**
> Thanks for your reply.   I do not disagree with your comments .....  setting up the individual programs and getting them to work is going to be something close to a headache.....  and perhaps best addressed first.

One of your comments I find interesting though ......you indicated that you thought that I would end up with usable storage of about 500GB (presumably per drive).  This is very interesting ....   I format the drives at present to FAT32 and the formatted volume is about 465GB.  Do I interpret your comment correctly in that you are suggesting that the available storage for each volume would fundamentally increase using raid?  I think you are not suggesting 75% redundancy ....    If I am able to save about 35GB per drive then this gives me quite a lot of cumulative extra space...

I was primarily cautioning you that if you a) configure a RAID array, and b) set up a server with several other things you may not have done before there may be a lot of opportunities to get something wrong the first time and lose data.

If you have roughly 1500 GB of data on individual disks now and no way to back it up then I think you need to configure the new server with an effective 1500 GB of storage as seem by Linux as it views the RAID system. This may require an additional 4-5 ea. 500GB drives. You need to be able to create an empty RAID array and then move your existing data on to it.

---

### Post by expatCM on 2007-06-28
Limpam - thank you for your comprehensive comments.  Sorry to trouble but I live in a part of the world where it is hard to buy motherboards that are not real common. Could you please tell me which motherboard(s) you have in mind which have six or eight SATA ports so that I can look them up and print it out so that I can show the local store....

Tim - thank you.

---

### Post by Limpan on 2007-06-28
Here's with the AM2 socket that AMD uses (with links to a swedish/nordic computer store, but you will get more information and I think most of the specs are pretty easy to figure out):
[ABIT Fatal1ty AN9 32X]("http://www.komplett.se/k/ki.aspx?sku=322045")
[ABIT KN9 SLI]("http://www.komplett.se/k/ki.aspx?sku=322039")
[Asus M2N32-SLI Deluxe]("http://www.komplett.se/k/ki.aspx?sku=321030")
[MSI K9N SLI Platinum]("http://www.komplett.se/k/ki.aspx?sku=320228")
[Gigabyte GA-M57SLI-S4]("http://www.komplett.se/k/ki.aspx?sku=322111")

These all have at least six S-ATA connectors.

---

### Post by expatCM on 2007-06-28
Excellent Limpam, thank you for your help.  I can print these out and show the local dealer so that they cannot deny motherboards can have more than two SATA ports......    :)

The battle progresses.   One day I might even know what I am doing.          Might.

---

### Post by lintoon on 2007-06-28
How about buying another PC with 2Tb of storage (4x500Gb sata or whatever).  Maybe buy a Firewire 800 card then you can add as many external hard drives as permissible.  Then use rsync and schedule the synchronisation between the 2 PCs.  This way if your first PC boot drive fails, os updates fail or general fiddling mess up your system you still have a working machine ready and waiting.
You don't need a monitor.  Either buy a KVM switch or use NXServer to administer the new PC remotely.
Or, just go for a firewire 800 card, buy external drives and rsync your data to the new drives as backup. 

Oh and something else.  If your data is that important maybe a UPS or at least a protected mains extension from someone like Belkin.

Just a thought.   Good luck.

---

### Post by expatCM on 2007-06-28
Thanks for your comments lintoon....

In this part of the world you simply do not run a pc without a UPS and not a cheap UPS, one that has surge protection both for the power line and the phone line.  APC are the brand that I use but they are quite hard to find in the local market.

Similarly buying a PC with 2TB installed is not a reality ......  At present I have to bring in my hdd's in from other locations since the local market has only just heard that they exist and they are considered too expensive to stock.  I have never seen a motherboard here which has more than two SATA ports so again it is a matter of research on the Internet and then planning what to do and then where to buy.

I will however keep your comments well in mind and would like to say thank you for your input...

---

### Post by lintoon on 2007-06-28
Good choice expat.  You cant go wrong with an APC SmartUPS.  Is the firewire 800 card an option.  I only say this because of the transfer rate and the ability to add more drives to the chain.  
Best of luck.

---

### Post by expatCM on 2007-06-28
Really not sure ...   somehow I have doubts about the local market but I should keep an open mind until I know.  If not ...   well I need to search further geographically ...  :)

---

