---
title: "Look at my partitions!"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by mitdxiw on 2006-01-04
Hey, I think I've decided hwo to partition my new hard drive for my new computer (I'm dual booting Ubuntu and Win XP), please give me some feedback:

250GB Drive

100GB Primary NTFS - Windows XP
8GB Primary Ext3 / - Ubuntu System
90GB Logical Ext3 /home - Ubuntu Files
50GB Primary FAT32 /media/hda1 - Shared win xp/ubuntu files
2GB SWAP - the swap

any advice on this?

---

### Post by earobinson on 2006-01-04
2 gig is a lot of swap... but then I have 2 gig swap. I assume you have 1 gig of ram? I have a gig of ram and my swap never really gets used. But I keep it because like you I have a lot of space so Im not worried about it.

looks like a great setup to me

---

### Post by vasudevank on 2006-01-04
Everything Looks great, the swap is a little big, on my computer wiht 512 MB RAM i don't use very much swap, but if you less ram is it is good

---

### Post by mitdxiw on 2006-01-04
My concern was with the primary and logical. When do I use each? I'm not really sure what the difference is. Also, I set bootable flags on the NTFS and ext3 system only right?

---

### Post by earobinson on 2006-01-04
[https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dualboot%29](https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dualboot%29)

---

### Post by frodon on 2006-01-04
For me there's really something wrong : 100Go NTFS Windows XP.
There's something to do here. If you want to use NTFS i advice you to make 2 partitions : 10Go for XP and 90Go for datas in order to format only the 10Go partition when you will have virus problems with windows.
Or you could also make the 90Go partition as ext3 because you already have a 50Go partition to share datas between windows and linux and with ext2fs drivers you will be able to have a read access of your ext3 partitions under windows.

that's all :)

---

### Post by xtacocorex on 2006-01-04
Edited because my advice sucked, I'd follow the above posts.

There is this program: [http://www.fs-driver.org/](http://www.fs-driver.org/) which allows Windows to read and write ext2 and ext3 partitions.

---

### Post by gosh on 2006-01-04
Isn't 100Gb for XP a bit much? Or do you have a lot of Windows-software that you still use?

I would create a larger FAT32 partition (or an extra partition) for XP/Ubuntu sharing and a smaller XP partition.

---

### Post by steve.horsley on 2006-01-04
I would leave another 8G partition free, ready to install Dapper when it arrives without having to wipe out your trusty old Breezy.

---

### Post by mitdxiw on 2006-01-06
Thanks for all the advice. You guys have been really very helpful. I just had one last question. All of my applications in Linux install under the /usr/bin folder right? If thats true, then I should make the / partition way larger than 8GB and the /home/ smaller right? I want to have a lot of space to install what ever apps i want..

What do you think of my new and improved scheme:

50GB NTFS
120GB FAT32
18GB ext3 / <- Do apps install here
50GB ext3 /home <- or here, why do I want space here in /home?
2GB swap
10GB unpartitioned

I want it to be a fair split ebtween XP and Ubuntu. And, I have never gotten a virus in XP, I'm not an idiot..

---

### Post by kidcharles on 2006-01-06
Whether you want to put more space in / or in /home depends on what you will be doing with Linux. If you are going to be saving a bunch of audio/video files for example, you will want more space in /home because that is where they will end up.  If you will be installing large games (like Quake 4) that have several gigabytes of data files, you'll want more space in /. I have a separate partition called /games but that's just how I roll ;) .

---

### Post by mitdxiw on 2006-01-06
The computer will be primarily for software development and other college-level work (writing papers, etc). I have a large amount of movies and music I would like to share with Windows and Linux. I guess my questions breaks down to: how much space do linux apps take? I dont want to ever feel restricted in installing things like office type apps, etc.. I do NOT play any games nor do I plan to install any. I will however use photoshop type apps and possibly some movie editing apps. I propose this:

50GB NTFS for Win XP software and other evils
120GB FAT32 for music, movies, pictures, etc
2GB SWAP for swapping lol
28GB EXT3 mounted to / for Linux software/etc
50GB EXT3 mounted to /home for software development projects, etc

What do you all think? Does the FAT32 drive have to be mounted to anything, can I mount it say /multimedia?

---

### Post by akniss on 2006-01-07
If you will be doing video editing, keep in mind that FAT32 has a 4GB maximum file size.  You may have to make a decision at some point which OS you will use to edit video, and store your video files on their respective filesystems.

---

