---
title: "100% Newbie: partitions before install?"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by marfados on 2006-04-26
Hello to everybody and thanks for this amazing forum to help people like me to iniciate in Ubuntu/Linus world,

I am absolutely newbie on this stuff, so, please, be very much patient with me (and with my English, I am from Spain).

So, after this introdutory comments I explain my situation:

I have downloade the Live CD of Ubuntu 6.06 beta, I have boot with it and is wonderful. So, I have decided to install it in my HD together the Windows XP. To do this, I have been using the Acronis disk director to create a new partition for the Ubuntu and here are my problems. I do not know the following:

- How many partitions do I have to create? One? three for the /, /boot and swap?
- Which tipe of partition? Primary, extended (or one extended with three logical parts for above?)

My actual disk structure is:

- Local disk C (primary): with 30 gb free space
- Partition of C (letter H:): with 20 gb free

As you can see, I am very confused with this matter. I have read a lot of forums and, finally, I am more confused than before but I do not want to give up. 

I would appreciate whatever help you can give me.

Thanks in advance,

---

### Post by alamba on 2006-04-26
I haven't used Acronis but below is what I know to the best of my limited abilities:

1. "Free" disk space is not enough, you will need a seperate logical partition to install ubuntu in from this free space. For that, use gparted from the live CD and shrink your current partition and create another empty one in ext3 format.

2. You will need a minimum of 2 partitions for ubuntu, i.e., / (root partition) and /swap (swap partition). If you so desire you can create seperate ones for /boot and /home too.

Do not forget to install grub too since you wish to dual boot.

A

---

### Post by catlett on 2006-04-26
Let the install do the partitioning for you.
 It's easier to tell you what not to do. Just don't select erase entire drive. Choose either," use all of /dev/hda2"(that's what H will look like to linux {device/dev, hard drive/hd, first hard drive/a, second partition/2}) or "use continuos free space". If your hard drive wasn't partitioned the easiest is way to install is "resize existing partition."
The main point is the install will partition for you.
This is a good dual boot howto.[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) It uses the current stable release to explain. You're using the unstable testing version but the directions should be the same.

---

### Post by marfados on 2006-04-26
Thanks alamba for your quick reply. 

Questions:
- The two minimun partitions: do I have to create them as logical ones with the gparted? both have to be ext3 format? 
- How do I have to install the "grub"?
- is it after or during the Ubuntu installation?

Thanks again,

---

### Post by marfados on 2006-04-26
Thanks to catlett also,

I did not see your respond because I was responding to alamba. It is very interesting your comment. I will check the link.

Thanks,

---

### Post by mseney on 2006-04-26
Is the partioner a little forked right now? I manually created the new partitions however it would not let me associate "/" or "/home" with one of them. The drop down list for the partition did nothing when I clicked on it.

---

### Post by mseney on 2006-04-27
[QUOTE=mseney]Is the partioner a little forked right now? I manually created the new partitions however it would not let me associate "/" or "/home" with one of them. The drop down list for the partition did nothing when I clicked on it.[/QUOTE]

Well after trying to install 6.06 beta 7-10 times it finally took. It seemed that if I clicked through the questions fast things worked better. On one occassion I had to click back and then go forward again for it to say it was going to make the partition ext3 and format it. Now that it's installed to the hard disk it's running great. So far with the installed form I'm impressed. I think before June the GUI installer needs some attention and also the choice of text based install would be awesome.

My Specs:

Intel Pentium 4 Prescott w/ HT (3.0Ghz/1M L2 Cache) Socket 478
Biostar Motherboard 
1 Gig Mushkin DDR RAM
80G IDE Maxtor ATA/133 HDD
BFG 6800GS 256M AGP 8x Video Card

---

### Post by penywise on 2006-04-27
Personally - I used Partition Magic 8.0, cut two partitions.
One of them was the "big" one and I left it... empty and formated.

The second new partition I cut was 1 Gb and I used the Partition Magic to format it as "SWAP".

Upon installing the Ubuntu - it formated that first partition I cut by itself, and I chose EXT3.

(careful - read before doing anything or you may format your whole HDD)

---

### Post by Sef on 2006-04-27
> Personally - I used Partition Magic 8.0,

Be careful with partition magic, it and Linux don't always get along.  It is recommended to use another partitioner.

---

### Post by penywise on 2006-04-27
[QUOTE=Sef]Be careful with partition magic, it and Linux don't always get along.  It is recommended to use another partitioner.[/QUOTE]

Hm... I partioned it from the Windows XP... besides the only thing I "partitioned" with it was the 1 Gb SWAP partition...

I left the other partition I cut just "formated", so the Ubuntu converted it to ext3 while running the installation

But I will keep that in mind - thanks

---

### Post by bailout on 2006-04-27
What I would do is use acronis to create "unallocated" space that you want to use to install ubuntu to. That is, decide how much space you can take from your current windows install, defrag windows, use acronis to shrink your windows partition so that that you are left with an area on your hard drive that is unformatted. 

Then just run the ubuntu install. It will ask you where to install to and one of the options will be the unformatted space you have created. Choose this and let the installer create the partiotions for you.

---

