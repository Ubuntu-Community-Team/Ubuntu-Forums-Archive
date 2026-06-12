---
title: "Setting up partition for Dual boot XP and Feisty (XP on first)"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-17
The "How To" I am using to set up a dual boot with XP and Feisty (with XP already on the computer first) says that when you start the Feisty live CD and select "install" from its desktop, then after the usual language and time zone screens etc it gets to the place where it sets up thel partition. And according to the "How To", there should be four options

1. Resize IDE1 Master (Partition #1) and use freed space (for use in dual partition)
2. Erase entire disc IDE1 Master
3. Use largest continuous free space
4. Manually edit partition table

So they are recommending option #1 as that will automatically create two partitions and give me a slider bar to determine how much space to alot to each.

But that very option #1 is not present on my live CD. There are only the options #2-4. I have two live CDs: one mailed to me directly from Ubuntu, and one which I downloaded as an ISO. Neither one gives me the option #1.

So how do I create the dual partition? In Vista there is an option to "shrink the partition" and thereby create empty space on the hard drive which allows one to then select option #3 above for creation of the second partition. But in XP, in disk management there is no such option to "shrink the partition".

So how do I create the dual partition for XP and Ubuntu, with XP already on the computer?

---

### Post by oilchangeguy on 2007-08-17
read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by swarup on 2007-08-17
> **oilchangeguy said:**
> read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

That site does not solve my problem. Because there too, it says that the live CD will give the option to set up two partitions for you. But at least on my two live CDs, it is not like that. There are only the options #2-4 which I listed above. There is nothing such as option #1 to "resize the Master and create a second partition".

---

### Post by mikewhatever on 2007-08-17
The last option is the way to go then. Shrink the XP partition and create root and swap for Ubuntu out of the unallocated space.

---

### Post by sailor2001 on 2007-08-17
if I recall correctly, Edgy had the 4 options but Feisty does not. To use a continuous free space would be setting up the partition you want with a slide bar to size it

---

### Post by AndyCooll on 2007-08-17
The link in my signature is an excellent guide to dual-booting (and it DOES tell you how to re-partition).

:cool:

---

### Post by swarup on 2007-08-17
> **mikewhatever said:**
> The last option is the way to go then.

The first option on the screen says, "Guided - use entire disk"

That means it will take the whole hard drive for Ubuntu, right?

The second option says "Guided - use the largest continuous free space"

And the third option says, "Manual".

If anyone can tell me how to use the second option ie to shrink the XP partition and create free space before starting the live CD, then I could do that.

Otherwise I suppose the only option is the "Manual" option. Although tried selecting it, and the parameters one has to set are pretty technical. If anyone can guide me on those, I suppose it could be done. But on my own, I would not know how to proceed.

---

### Post by oilchangeguy on 2007-08-17
please advise your hard drives size, and remaining free space. and have you defraged windows (at least twice)?

---

### Post by swarup on 2007-08-17
> **sailor2001 said:**
> if I recall correctly, Edgy had the 4 options but Feisty does not. To use a continuous free space would be setting up the partition you want with a slide bar to size it

I don't think so. The continous free space needs to be set up before you start the live CD. I tried the option, and it says "there is no continuous free space to use for a partition".

---

### Post by loudnlownoma on 2007-08-17
> **sailor2001 said:**
> if I recall correctly, Edgy had the 4 options but Feisty does not. To use a continuous free space would be setting up the partition you want with a slide bar to size it

Installed Feisty last night and did receive all four options.  I used the manual option anyway, however, I had setup the partitions in my previous XP install, so that I had a 20 GB raw partition waiting already.  It was just a matter of selecting the partition I had setup before and setting the swap and root drives.

@OP, unfortunately, I am fairly new to the Linux(even more so to kubuntu) world, and don't know that I would be able to offer the correct advice for your situation, needing to create the new partition with Windows already installed on it...sorry.

---

### Post by swarup on 2007-08-17
> **AndyCooll said:**
> The link in my signature is an excellent guide to dual-booting (and it DOES tell you how to re-partition).

:cool:

That's great. But one thing-- your site says it is for the "alternate installer". I think mine is the standard installer for 386 machines, rather than the "alternate installer". Will it still work?

My basic problem is just that of creating a dual partition, which my live CD does not seem to want to do for me to my great surprise and dismay. Will your website solve that problem for me and still allow me to use the live CD which I have with me now?

My Windows OS is XP, and the file system is NTFS. NOT FAT 32

---

### Post by swarup on 2007-08-17
Can someone out there please tell me how to resize my primary Windows partition so I can then put Feisty on the remaining free space? 

Once I get some free space created on the drive, then the Feisty installer will create a partition on it. --But until I create free space, this live CD is not going to do anything for me.

(Unless someone tells me how to use the "Manual" in the live CD partitioner)

---

### Post by swarup on 2007-08-17
I am not understanding why creating this dual partition is turning out to be so difficult in XP. I've done it with Win 98 and with Vista, and with each of them it was a piece of cake to create an empty partition for Feisty. But XP? What is the way?

Has anyone used gparted? It is the GNOME Partition Editor. It comes in the form of a live CD 
(gparted-livecd-0.3.4-8.iso), but I have never used it. How does it install? Do you boot the computer with this CD, and then it does its work? I suppose it must be something like that. I'll try and create this disk. Perhaps it will do the job. If anyone has experience with it, please let me know. Thanks!

---

### Post by yorkie on 2007-08-17
[http://www.linux.com/articles/114157](http://www.linux.com/articles/114157) 

Two videos on using gparted  number 2 video resizing windows partition
number 3 video creating linux partition.
this can be done using gparted live cd 
or ubuntu live cd using manual edit partitions 
cheers

---

### Post by phxflyer on 2007-08-29
> **swarup said:**
> I am not understanding why creating this dual partition is turning out to be so difficult in XP. I've done it with Win 98 and with Vista, and with each of them it was a piece of cake to create an empty partition for Feisty. But XP? What is the way?

Has anyone used gparted? It is the GNOME Partition Editor. It comes in the form of a live CD 
(gparted-livecd-0.3.4-8.iso), but I have never used it. How does it install? Do you boot the computer with this CD, and then it does its work? I suppose it must be something like that. I'll try and create this disk. Perhaps it will do the job. If anyone has experience with it, please let me know. Thanks!

Actually, I'm having the same problem. It's not with the live CD, it must be with XP. I had the same disk work fine on my desktop machine and not work with my laptop. I sure there is a simple answer

---

### Post by Harpoon on 2007-08-29
I hate to say this, but I havefound that the absolute easiest way to do this is by going back to XP and using Partition Magic.  It will resize your windows partition, and you can then either set up your parttitions for linux, or leave it as free space for the installer.

If you are not sure if you are going to keep the linux installation, then let the ubuntu installer use all the avalable **free space** you created above.  If (for some reason) this is a long-term partnership, then I suggest setting up your home directory in its own partition (saves grief when when upgrading the os, or when you foul the os and have to fix it). 

Without a doubt, some of the biggest obstacles that leave new users dead in the water, and walking away with the "this is only for geeks" impression is the lack of good, readable, and easily understood non-technical descriptions in the partitioning tools (installer, gparted, whatever). 

Been there, done that.  Try PMagic to get you started.

---

### Post by swarup on 2007-08-30
> **Harpoon said:**
> I hate to say this, but I havefound that the absolute easiest way to do this is by going back to XP and using Partition Magic.  It will resize your windows partition, and you can then either set up your parttitions for linux, or leave it as free space for the installer.

If you are not sure if you are going to keep the linux installation, then let the ubuntu installer use all the avalable **free space** you created above.  If (for some reason) this is a long-term partnership, then I suggest setting up your home directory in its own partition (saves grief when when upgrading the os, or when you foul the os and have to fix it). 

Without a doubt, some of the biggest obstacles that leave new users dead in the water, and walking away with the "this is only for geeks" impression is the lack of good, readable, and easily understood non-technical descriptions in the partitioning tools (installer, gparted, whatever). 

Been there, done that.  Try PMagic to get you started.

Many thanks for your helpful reply. I was not aware that there is actually a tool inside Win XP for resizing the partition it is in. Those days when I was struggling to get this done, in all the material I read, I don't think I came across anywhere where it stated one can do this right from within XP, I knew Vista could downsize itself, but I was under the impression that XP could not. Is "Partition Magic" a utility that one accesses right in XP? Where does one find it? (I'll check under "find" next time I'm on an XP machine, if I don't hear back on this). 

I had burned a live "gparted" disc, but was unable to get it running. For some reason, gparted did not like the monitor/screen I was using and would not boot up into its GUI. Ultimately I burned a (I think it was called) live CD rescue disc which had gparted on it and was able to use gparted on that disc to downsize XP. The rest of the install was a piece of cake.

But you're right-- this matter of partitioning is surely the greatest obstacle for new would-be linux users. It's not difficult to do, but like so many other things-- if one doesn't know how and it's not properly explained, then it can be almost a nightmare.

---

### Post by Harpoon on 2007-08-31
Thanks for the good news abount getting the install done.  As to PartitionMagic, I mislead you by not saying it was a commercial application (too expensive for one time use).  Indeed, I booted intp Windows (shudder) and checked again only to find that there is no option to resize partitions built in.  But that is what commercial partnerships are all about (I got my money, now you go get yours).

Have fun with linux, and if you run into any post-install problems let me know.

---

### Post by swarup on 2007-08-31
> **Harpoon said:**
> Thanks for the good news abount getting the install done.  As to PartitionMagic, I mislead you by not saying it was a commercial application (too expensive for one time use).  Indeed, I booted intp Windows (shudder) and checked again only to find that there is no option to resize partitions built in.  

Yeah, that was what I thought earlier-- when I was trying to make room for an Ubuntu partition, I went in XP to Disk manager and found to my dismay that unlike Vista, there is no option to resize the partition there. It's too bad 

> **Harpoon said:**
> But that is what commercial partnerships are all about (I got my money, now you go get yours).

Yep, you're right. 

> **Harpoon said:**
> Have fun with linux, and if you run into any post-install problems let me know.

Thank you kindly.

---

