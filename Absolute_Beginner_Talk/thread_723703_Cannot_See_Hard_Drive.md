---
title: "Cannot See Hard Drive"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by Literati on 2008-03-13
I have two hard drives connected to my computer
an 80GB hard drive
and a 400GB hard drive.
The BIOS sees BOTH harddrives, no problem. 

The 80GB is formatted and is running my Ubuntu now, whereas the 400GB has NOT been formatted, only hooked up

I just checked the System Monitor, and even though it's hooked up (yet unformatted) it does NOT see the 400GB drive.

What should I do?

---

### Post by ruy_lopez on 2008-03-13
What's the ouput from this command:

```

sudo fdisk -l

```

---

### Post by Mogurijin on 2008-03-13
You could try and see if Gparted sees your drive. I don't think it is installed defaultly (even though it is on the Live CD), so you might have to download it (apt-get install gparted, or something like that). Hopefully gparted can see the unformatted disk and format it for you.

---

### Post by Literati on 2008-03-13
> **ruy_lopez said:**
> What's the ouput from this command:

```

sudo fdisk -l

```

I posted that [HERE]("http://ubuntuforums.org/showpost.php?p=4510736&postcount=3")

And Mog, I'm running the program, but it's taking forever to "Scan all devices"
So I'll post back when I have something for you :)

---

### Post by ruy_lopez on 2008-03-13
The 400gb drive is /dev/sdb.

Use gparted, like Mogijirin says. Up in the right corner you can select the device "/dev/sdb". Once selected, it'll probably appear as a gray block. You'll have to decide how you want to partition the drive.

If you want a 400gb partition, select the grey block, click new, choose ext3 as the type, and make the maximum size. Then click apply.

Once you have it partitioned, run fdisk -l again, and post the output. We'll help you mount the new drive.

---

### Post by Literati on 2008-03-13
> **ruy_lopez said:**
> The 400gb drive is /dev/sdb.

Use gparted, like Mogijirin says. Up in the right corner you can select the device "/dev/sdb". Once selected, it'll probably appear as a gray block. You'll have to decide how you want to partition the drive.

Any suggestions?
I hear obout people using it as home. But then I don't know how to go about taking /home from this drive, and putting it on that drive... o_O

---

### Post by ruy_lopez on 2008-03-13
> **Literati said:**
> Any suggestions?
I hear obout people using it as home. But then I don't know how to go about taking /home from this drive, and putting it on that drive... o_O

Concentrate on partitioning the drive for now. It's not hard to create a home partition. I can show you how.

The question to ask yourself is, do you want a 400gb partition, or a number of smaller partitions?

---

### Post by Duck2006 on 2008-03-13
This will show you how to make a home partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I would not use the hole of the drive as a home partition. you only need round 20Gb as a home partition. the rest you can format as a data partition.

---

### Post by Literati on 2008-03-13
It really doesn't bother me. 
Ubuntu is the ONLY OS I'll be running on this computer.
I'll upgrade it to 8.04 when that gets released, but that's it. 
There will be no Windows on this, no other distros. Nothing.

I think the main thing is.
I don't exactly understand what it MEANS to partition your harddrive.
I mean, how will a partition affect my files? 
If I make this /home partition someday, what happens to my old home in the / folder? 
I'm just not sure what it all means for me as a user.

---

### Post by gijoecam on 2008-03-13
What happens when the BIOS sees the new hard drive, but gparted does not register it?  That's the boat I'm in right now...

-Joe

---

### Post by wrecche on 2008-04-15
> **gijoecam said:**
> What happens when the BIOS sees the new hard drive, but gparted does not register it?  That's the boat I'm in right now...

-Joe

Likewise.. damn, and its annoying because there is no reason why it should NOT show up.

I have it bootable from grub even.. just nothing in the OS.. 

blah..

---

### Post by maccawolf on 2008-05-10
all my drives are seen in my computer, but when I try to run gparted.... NOTHING.

It scans for drives forever and I just get bored with it searching after 10-15 mins so I shut it down.

---

### Post by rptizzle on 2008-05-23
> **Duck2006 said:**
> This will show you how to make a home partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I would not use the hole of the drive as a home partition. you only need round 20Gb as a home partition. the rest you can format as a data partition.

The page on that site says "If you want to know more about partition planning, read this." - 'this' being a link, and a DEAD link. I wish I could read that page.

---

### Post by rptizzle on 2008-05-23
> **Literati said:**
> 
I don't exactly understand what it MEANS to partition your harddrive.
I mean, how will a partition affect my files? 
If I make this /home partition someday, what happens to my old home in the / folder? 
I'm just not sure what it all means for me as a user.

Partitioning the drive is necessary before you can use it. Any drive has to first be partitioned. When you partition the drive, you determine whether it will be your primary drive or an extended drive.

Partitioning is not only necessary, but it's good because it allows you to have more than one partition. For example, I currently have two 500 GB and one 250 GB drive. So I have 3 physical drives. I could partition each one of my 500 GB in half and end up with 4 different partitions of 250 GB each (out of two physical drives). Then if I add my one 250 GB physical drive I should see a total of 5 partitions of 250 GB each. I could do that, but I don't. This is just an example.

I don't do that because I don't like having too many partitions. I prefer to have as few partitions as possible. It's easier for me to organize my files with fewer partitions.

As a Windows user, I always create two partitions on my primary drive: one for just the OS and the other for my files that I want to keep. If my OS gets corrupted I can reinstall it without worrying about losing any important files - because they are saved on a different partition that I live intact while reinstalling the OS.

I'm switching to Ubuntu and hope to keep this system of separating the OS from my important files, just in case. I take it that my home folder has to be on a separate partition for that to happen.

I find it interesting that Ubuntu does not designate letters for drive partitions. I'm not sure that's good or bad, but I'm used to the letters for drives in Windows: C: drive (primary), D: drive, etc.

Another disadvantage of partitioning a drive unnecessarily: suppose you have a 500 GB partition that you split into 10 different partition of 50 GB each, just because you can. Now suppose you get a file of 90 GB, which is possible depending on what you're doing. You cannot save this file to any of your partitions because the file is bigger than any partition you have. Now, if you had a 500 GB partition you could have 5 files of that size on the same 500 GB drive which only has one big partition.

Cheers.

- Ricardo

---

### Post by Duck2006 on 2008-05-23
> **rptizzle said:**
> The page on that site says "If you want to know more about partition planning, read this." - 'this' being a link, and a DEAD link. I wish I could read that page.

I think this is the page.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

