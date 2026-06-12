---
title: "Need Help Preparing for Installation"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by NonStop on 2008-03-28
When 8.04 is released I plan to finally install it on my system. however, the guide that i found on your wiki doesn't seem to explain how to manually select partitions (they're numbers not drive letters like in Windows). 

I have one hard drive on my laptop, which has 3 partitions, ACER - C: (for Windows, DATA - D: (for data), and DATA 2 - F: (for ubuntu). Ideally, I want to install ubuntu in the future to F:, which is currently just under 15 GIG in space.

A step by step guide would be great, though I can wait till I get a disk through for the latest release, and then write down all the stuff it says when I select manual partition. I would really appreciate this.

---

### Post by Cypher on 2008-03-28
You will benefit from leaving the disk lettering scheme in the Windows land. Partitions in Linux are numbered and prefixed by the HD they are on. So, in Windows, C is the primary partition on your primary HD, and D has to be the primary partition on a second driver if it exists, otherwise it can be just another parittion on your primary HD. This can be quite confusing.

In Linux, if you have a single HD, then it's either called "HDA" or "SDA" depending on the kind of drive (IDE, SATA, SCSI, etc). You can have up to 4 primary parittions, this HDA1-HDA4. Or if you have a very large HD, then you'd create 3 primary partitions, and an extended partition that spans the rest of the HD and then create logical partitions within that extended space.

With the use of extended/logical partitions, the numbers will be something like HDA1-3 for the primary partitions and HDA5-N where N is the last partition you create..#4 is skipped..

---

### Post by SpongeBob SquarePants on 2008-03-28
> **NonStop said:**
> When 8.04 is released I plan to finally install it on my system. however, the guide that i found on your wiki doesn't seem to explain how to manually select partitions (they're numbers not drive letters like in Windows). 

I have one hard drive on my laptop, which has 3 partitions, ACER - C: (for Windows, DATA - D: (for data), and DATA 2 - F: (for ubuntu). Ideally, I want to install ubuntu in the future to F:, which is currently just under 15 GIG in space.

A step by step guide would be great, though I can wait till I get a disk through for the latest release, and then write down all the stuff it says when I select manual partition. I would really appreciate this.

During installation, when it comes to partitioning, you're given the option to partition manually. Just choose that option and it will display your current partition information for you. Just look out for the 15 GB partition....assuming your other partitions are of a different size....and then create an "extended partition" in that space. In that extended partition then create two (or three depending upon whether you want a separate /home folder) "logical" drives in the existing 15GB partition. One needs to be swap (which needs to be the size and a half again of your RAM...so for 1 GB of RAM choose 1.5 GB for swap), and the other needs to be root (/). If you wish a /home partition too then halve the root (/) size and make the free space a home (/home) partition. Then click on apply and you're done.

With regards the assignment of letters etc, on my machine Windows sees my drives as "IDE", with a C partition and three unknown partitions. Linux sees that same drive as "hda", and the partitions are "hda1", "hda5", "hda6", and "hda7". The gap in numbering is because I have an extended partition on that drive. If I had say three primary partition they'd just read as "hda1", "hda2 "and "hda3". If you have a SATA drive, it should show up in Gparted as "sda", and the partitions "sda1", "sda2" etc..

If in doubt, load up a Live version of Ubuntu and choose Gparted (or Partition Editor from System>Administration). It will show you how Linux sees your drive.

---

### Post by NonStop on 2008-03-28
> **SpongeBob SquarePants said:**
> During installation, when it comes to partitioning, you're given the option to partition manually. Just choose that option and it will display your current partition information for you. Just look out for the 15 GB partition....assuming your other partitions are of a different size....and then create an "extended partition" in that space. In that extended partition then create two (or three depending upon whether you want a separate /home folder) "logical" drives in the existing 15GB partition. One needs to be swap (which needs to be the size and a half again of your RAM...so for 1 GB of RAM choose 1.5 GB for swap), and the other needs to be root (/). If you wish a /home partition too then halve the root (/) size and make the free space a home (/home) partition. Then click on apply and you're done.

With regards the assignment of letters etc, on my machine Windows sees my drives as "IDE", with a C partition and three unknown partitions. Linux sees that same drive as "hda", and the partitions are "hda1", "hda5", "hda6", and "hda7". The gap in numbering is because I have an extended partition on that drive. If I had say three primary partition they'd just read as "hda1", "hda2 "and "hda3". If you have a SATA drive, it should show up in Gparted as "sda", and the partitions "sda1", "sda2" etc..

If in doubt, load up a Live version of Ubuntu and choose Gparted (or Partition Editor from System>Administration). It will show you how Linux sees your drive.

Ok. Gonna try this soon as I get the disk, and let you guys know the results of how it goes. Do I have to make the extended partition? I know I sound annoying but I am a complete newbie. Any screenshots similar to what I have to do would help me so much.

---

### Post by bumanie on 2008-03-28
ubuntu should make the extended partitions for you. Fortunately grub is not as fussy as boot.ini and will boot from any partition. I however think that 15g is rather small. Are you planning to use your present 'data' partition to save/transfer ubuntu files to?
What the above posts say is quite correct. Just let you know that at the manual stage of partitioning, when you click on your 15g partition you will have choose 'edit partition' choose the amount of space fro / ;click OK.Then you'll have to click on whatever space is left, click 'edit partition' and make a swap of probably 1g.

---

### Post by NonStop on 2008-03-28
> **bumanie said:**
> ubuntu should make the extended partitions for you. Fortunately grub is not as fussy as boot.ini and will boot from any partition. I however think that 15g is rather small. Are you planning to use your present 'data' partition to save/transfer ubuntu files to?
What the above posts say is quite correct. Just let you know that at the manual stage of partitioning, when you click on your 15g partition you will have choose 'edit partition' choose the amount of space fro / ;click OK.Then you'll have to click on whatever space is left, click 'edit partition' and make a swap of probably 1g.

Data is just media, my documents, etc. I plan on using 15 GIG for Ubuntu and its programs, then use the DATA drive to put on and access my data. Is that doable?

Choose what amount of space when I hit edit partition? Cheers.

---

### Post by bumanie on 2008-03-28
> Data is just media, my documents, etc. I plan on using 15 GIG for Ubuntu and its programs, then use the DATA drive to put on and access my data. Is that doable?
Yes, that is able to be done. It is not necessarily the most efficient way to do things but it is a good idea to keep data and / separate. These days ubuntu natively supports read and write to ntfs through the ntfs-3g project. There is also a program that allows windows to read and write to ext2/3; it's here [http://fs-driver.org/](http://fs-driver.org/)

---

### Post by Duck2006 on 2008-03-28
A step by step guide on installing ubuntu.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by NonStop on 2008-03-28
> **Duck2006 said:**
> A step by step guide on installing ubuntu.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Good guide, cheers. When ti coems to selecting the partiton (I only select one, right?), what should I fill in for at this point:

[img]http://www.psychocats.net/ubuntu/images/feistydual12.png[/img]

---

### Post by Duck2006 on 2008-03-28
You need to mark one as your root partition / make for what size you want (if you are not having a home partition, if so make it 10 to 15Gb)
You need one as your swap partition iGb should be good for that
if your going to have a home partition then make it what size you need.
ie

/ 15Gb
swap 1Gb
home 20Gb or bigger.

if you just want a swap and root then
/ 20Gb
swap 1Gb

---

### Post by Inxsible on 2008-03-28
[LEFT]You can use partitions sizes depending on your usage. As a guideline though,

root should be atleast 5GB, Swap should be atleast 500 MB - 1GB and if you are going to have many users on the machine, then its a good idea to have a little larger /home partition

This is what i have (YMMV) :
25 GB - Windows Vista
15 GB - Windows Data
9  GB - / (root)
20 GB - /home
1  GB - swap
rest - /Shared - which holds my music movies etc and is shared by Windows and Linux both


[/LEFT]

---

### Post by NonStop on 2008-03-28
Why would I need a /home partition if all my date is on my DATA drive?

---

### Post by Inxsible on 2008-03-28
> **NonStop said:**
> Why would I need a /home partition if all my date is on my DATA drive?/home partition holds all the user information in a linux system.

What DATA partition are you referring to ? like a shared drive?

---

### Post by Duck2006 on 2008-03-28
So if you have to do a reinstall, all your user information is still in you home partition.

---

### Post by NonStop on 2008-03-29
I see. Am i right in saying the /home partition is only there for your files? Cos what I'm saying is can I access and download fiels to my DATA drive, much like I do in Windows?

---

### Post by tangibleorange on 2008-03-29
Yes. In a normal Ubuntu install, there are only two partitions. a '/' and a swap partition. on the '/' partition all the system files and data are included, like on a default windows install. However, it is often seen as good practice to keep all your data on a separate /home partition, and access it from there, just in case the '/' fails for some reason you still have access to your data.

However, as you already have a separate DATA drive/partition, I don't think it would be necessary for you. Here is how I imagine your partitions looking:

WINDOWS - contains all your windows system files
DATA - contains all your personal files. Can be accessed and written to in Ubuntu or windows.
'/' - root file system for Ubuntu - all system files for Ubuntu. Can be about the 15GB you suggested if you don't plan on storing personal data or installing too many programs on it.
swap - swap file (like a page file) that enables Ubuntu to use more memory - nothing to worry about. should be about 1.5GB

forgive me if I've misunderstood, but I think that's how you want your partitions to look like?

---

### Post by bumanie on 2008-03-29
Hi nonstop, Last night, I was going to suggest a separate /home, but decided it was less important seeing you had a data partition. Personally, I still think its a good idea, but as you only had 15g to play, a separate data partition should be adequate.

---

### Post by NonStop on 2008-03-29
> **tangibleorange said:**
> Yes. In a normal Ubuntu install, there are only two partitions. a '/' and a swap partition. on the '/' partition all the system files and data are included, like on a default windows install. However, it is often seen as good practice to keep all your data on a separate /home partition, and access it from there, just in case the '/' fails for some reason you still have access to your data.

However, as you already have a separate DATA drive/partition, I don't think it would be necessary for you. Here is how I imagine your partitions looking:

WINDOWS - contains all your windows system files
DATA - contains all your personal files. Can be accessed and written to in Ubuntu or windows.
'/' - root file system for Ubuntu - all system files for Ubuntu. Can be about the 15GB you suggested if you don't plan on storing personal data or installing too many programs on it.
swap - swap file (like a page file) that enables Ubuntu to use more memory - nothing to worry about. should be about 1.5GB

forgive me if I've misunderstood, but I think that's how you want your partitions to look like?

You are correct. Cheers.

> **bumanie said:**
> Hi nonstop, Last night, I was going to suggest a separate /home, but decided it was less important seeing you had a data partition. Personally, I still think its a good idea, but as you only had 15g to play, a separate data partition should be adequate.

May I ask wy would it still be a good idea?

---

### Post by wagb278 on 2008-04-12
I'm still learning too, but here is why you might consider a partition dedicated to /home:

Each Ubuntu user account you set up will have a directory stored at /home/username.  In each user's home directory will be personalized settings unique to that user.  This directory is the default 'current directory' when a user completes a login action.  You might relate /home in Linux to "Documents and Settings" in Windows.  Linux's /home/username relates to "My Documents" in Windows.

I presume that many Linux users store their personal files in their /home/username directories where they are private.  Placing personal files on a /DATA partition is probably intended to be public.

If you ever perform a new install of Ubuntu (or other distribution) you can tell the install process to not re-format, or overwrite  the /home partition thus all the user settings and any personal data files are untouched.  If /home is _not_ in it's own partition it will be blown-away with a new install. 

Of course you should backup /home before a new install just to be safe.  We do all backup our data - right?

Hey experts out there - what files need to be backed up and restored after a new install to recover user account information?

As mentioned, I'm still learning too, but I hope this helps.

---

