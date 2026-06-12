---
title: "Reinstalling Ubuntu on a dual boot machine"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Goonie on 2006-03-29
Hi all

I had some major problems with wireless on my laptop and tried fixing it myself using a how-to I found on a forum but it messed up the machine pretty good. So I wanted to try reinstalling Ubuntu but I also run Windows on a different partition of the same disk and I'm afraid I'll do something wrong and mess up the Windows. I use the Windows for work so there are a lot of documents, programs and settings that would be terrible to lose. So, how do I reinstall Ubuntu safely without harming my windows?

thanks

Regards
Gunnar Freyr

---

### Post by siminone on 2006-03-29
you will have no problems reinstalling Ubuntu as long as you don't touch any NTFS or FAT32 partitions in the partition configuration process when installing.

---

### Post by Sef on 2006-03-29
> So, how do I reinstall Ubuntu safely without harming my windows?

**Back up** your documents first.  There is no 100% guarantee that everything will go right.  Yes, it almost always does go right, if done correctly, but mistakes can be made, and problems can occur.

This is how I reinstalled when I had a dual boot:

When I got to the partition table, I erased all the partitions, except the Windows one, and my /home.  

Have you ever manually partitioned a hard drive, or do you want some more info on partitioning with Ubuntu's partitioner (gparted)?  If not or if so, let me know and I will describe in more detail what I did.

---

### Post by Goonie on 2006-03-29
Thanks for the replies guys

I have manually partitioned a drive using fdisk in a gentoo installation once and I didn't have any problems then. I've never used or even heard of Ubuntu's partitioner.

So if I understand you correctly, I can boot up from the Ubuntu install cd and when I get to the partition section I can manually partition the disk and install Ubuntu on the partition (or unpartitioned space) that doesn't contain the windows setup? Will the GRUB setup stay the same? It is installed in the MBR now. Will I have to worry about GRUB at all?

Thx,
Gunnar Freyr

---

### Post by Sef on 2006-03-29
> So if I understand you correctly, I can boot up from the Ubuntu install cd and when I get to the partition section I can manually partition the disk and install Ubuntu on the partition (or unpartitioned space) that doesn't contain the windows setup?

Yes. That is correct. 

> Will I have to worry about GRUB at all?

No, you shouldn't have to worry about GRUB.  I suspect it will write over the current GRUB and will set up a new GRUB, so you can dual boot.

---

### Post by Goonie on 2006-03-30
Hi again

I'm going to make an image of my hard drive for backup purposes today and go for the reinstall tonight. 

The Ubuntu community really is friendly and helpful :-D If I can get my wireless up and running I'll be spamming these forums with questions about everything.... By helping this newbie you just might have opened Pandora's box hehe.

Thanks again
Gunnar Freyr

---

### Post by patrick295767 on 2006-03-30
hi, 

If you dont touch to your partition windows, you can play around with other partitions & installations of OS'es, and so on.
  
If you keep linux, you can make use of : 
```
grub-install
```
after changing the boot grub menu
  
The chain lines (at the end), can be used for windows partitions...
  
Nice How to Dual Boot Ubuntu:
-------------------------------
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by IDipSkoalMint on 2006-03-30
By the title, you're simply reinstalling Ubuntu. When you get to the partition section, just "delete" the partitions that contain Ubuntu to make it unallocated space, and then just format over it when you install. I did that and had no problems. ;)

---

### Post by Goonie on 2006-03-30
Hello

I reinstalled Ubuntu and everything went fine but sadly it did not solve my wireless problem. I simply can't get the wireless to work even though I've replaced the actual Intel 2200 wireless netcard and tried everything I can think off. I think Ubuntu is the most exciting distro around but I'm sadly not going to be able to use it. This is really frustrating since I know the hardware is fine and everything should work. Thanks for all your help guys, I really appreciate it. 

Regards
Gunnar Freyr

---

### Post by torpedo on 2007-06-16
I am trying to re-install ubuntu on a dual-boot machine. I did not find the comments in this thread to be sufficient. I would be grateful if somebody could be more specific as to how this is done safely.

When I get to the partition manager, I choose "Manual install" because the Guided version wants to partition the partition where Ubuntu is already installed, making it half of what it is. So after Manual install has been selected, I see 4 partitions: one is NTFS and that's where Windows is, another one is fat32 and that is where the recovery stuff for my ThinkPad is, then I have ext3 which is where Ubuntu is installed, and a swap that's 1422 MB. I delete the latter two. After that they turn to "free space". What do I do next? If I try and press forward, it complains that it wants me to specify the partitions where Ubuntu is going to be installed, but I do not want to do that manually because the risk of screwing up is really high. I tried to specify partitioning manually on another machine where I installed Ubuntu and it was a mess. So how do I proceed from there safely? Thanks!

---

### Post by metaphorm on 2007-09-21
I too would like a detailed HOW-TO on re-installing Ubuntu. I have to upgrade my machine in a week or so (mobo etc.). I have a dual boot machine with Windows XP and Ubuntu 7.04 Feisty on separate drives. I have made the /home partition so would like to keep my settings intact after the reinstall. What do I do when I use the Desktop CD and get to the manual partition stage. 

Someone please elaborate on torpedo's previous query, or point to a resource that answers it. Many thanks.

---

### Post by Heavy Light 117 on 2008-04-19
Alright so I'm in the same boat as you guys and this is where I am. After you go into the manual configuration menu I deleted my swap and ubuntu partition. I then reformatted the swap partition back into a new swap partition. I did the same for the other partition (except I kept it as an ext? I think that what it was, just the same as it was before i deleted it) I then mounted it as root which is the (\) {I believe thats the first option}  I then clicked forward and now its asking me if i want to migrate my documents and settings from xp. I think I got it... i hope. I will update if it works.

---

