---
title: "Need help installing on a Mac - I'm New to Lunix"
date: 2008-04-14
forum: Apple Intel Users
---

### Post by mymac8mypc on 2008-04-14
Ok, I'm new to Linux and I can't seem to install ubuntu from the download that I put on a CD.


I would like to keep Mac OSX and my data on my HD but install ubuntu on my Mac.



I have looked at [URL="https://help.ubuntu.com/community/GraphicalInstall"] this webpage but I can't get ubuntu to install.  :( 


I can boot to the CD, press install, enter in my data, but I don't know what to do when I get to the "Prepare Disk space" and "Prepare partitions"


This is what it looks like:


"Guided - use entire disk"
     SCS13 (0,1,0) (sda) - 250GB ATA HD


"Guided - use the largest continuous free space"


"Manual"

I think I should click "Manual"?


After that I don't what to delete and how to make a new partitions for Linux and how to install.....

:confused:


Thank you for your time!


Mike

---

### Post by NightwishFan on 2008-04-14
Partitioning is simple. You want enough space free for Ubuntu and swap, 20gb perhaps, depends on what you need. The in manual partitioning make a logical partition. One as ext3 mounted at / and the other as linux swap, size is about the 1.7-2.0x your amount of ram. If you have enough empty space, just use the use continuous free space option. Just make sure you have enough.

---

### Post by mymac8mypc on 2008-04-14
Thank you for your reply!


I'm new to Linux can you tell me what to click?


Also I have tried to install twice, when I went into OSX and opened the disk utility and there was 2 "SWAP" partitions, is this bad?

-Mike

---

### Post by NightwishFan on 2008-04-14
I do not think it is bad, but possibly unnecessary. Also I really cannot make heads or tails of that, but it seems like you have 18gb of free space. The "use largest continuous free space" would make use of that and install automatically. It seems like a messy partition set up what do you have all in there?

---

### Post by m84 on 2008-04-14
I have just followed the macbook walk through (santarosa), and it says nothing about making a linux swap partition.

Do i need to reformat and make another partition?

Does the walk through need to be changed?

thanks

---

### Post by mymac8mypc on 2008-04-14
Yes, I **had** one partition @ 250GB before I tried to install Linux.


I got it to install after clicking the "free space". but I did not set up a swap partition, is this bad, and can I set it up after installing?



Thanks for your help!

BTW: How do I give you points?

-Mike

---

### Post by Monsoonx27 on 2008-04-14
If i were you i would move the partition sda3 up into the free space above it. The create a swap partition which you need to do before installing ( a coupe hundred megs will do) then install ubuntu the remaining free space.

Do you have a boot loader installed that can handle Mac OSX?
 if you dont i suggest installing rEFIt which you can do in OSX

---

### Post by cyberdork33 on 2008-04-14
> **NightwishFan said:**
> Partitioning is simple. You want enough space free for Ubuntu and swap, 20gb perhaps, depends on what you need. The in manual partitioning make a logical partition. One as ext3 mounted at / and the other as linux swap, size is about the 1.7-2.0x your amount of ram. If you have enough empty space, just use the use continuous free space option. Just make sure you have enough.You cannot make a logical partition on a Mac since it uses a EFI/GPT partition format.

> **m84 said:**
> I have just followed the macbook walk through (santarosa), and it says nothing about making a linux swap partition.It is not required, but nice to have.

From what I can tell, you have a bunch of extra partitions in there. Boot from the Ubuntu Live CD and start the partition editor (gparted). [LIST]
[*]sda1 is an EFI partition. Do not mess with it. You so not want to mount it on startup.
[*]I would guess that sda2 is your OSX partition (should be a HFS+ format in gparted)
[*]Everything else after that is free space, or other small partitions.[/LIST]What I would do, is, as long as you did not have anu other OSs already installed such as windows, then select and delete the partitions after your OSX partition and click Apply. (if a partition is "locked" then you can choose to umount it so that it unlocks). After it finishes, close the partition editor, and start the ubuntu installer. when prompted choose to install to the "largest free space". This will create a root partition and a swap partition in the free space on the disk and install ubuntu.

rEFIt would be a good idea too, but not required.

---

### Post by mymac8mypc on 2008-04-14
Thanks for your reply!

I can understand what your saying, but there is one thing I don't understand:


In Disk Utility in OSX there are 2 partitions that are called "swap" should I delete one?


And, what is swap?


Again, thank you for your reply!

-Mike

---

### Post by NightwishFan on 2008-04-14
I didn't know that, thanks. Well I have never used a mac, I did not know it would be any different.

---

### Post by cyberdork33 on 2008-04-14
> **mymac8mypc said:**
> Thanks for your reply!

I can understand what your saying, but there is one thing I don't understand:


In Disk Utility in OSX there are 2 partitions that are called "swap" should I delete one?


And, what is swap?


Again, thank you for your reply!

-MikeI would avoid using Disk Utility, because it will attempt to resize the partitions to cover the free space, but yes you can delete both of them, a new one will get created by the installer. If you do the steps I showed, you should be ok.

swap is kind of like emulated RAM. It uses a part of your disk space as temporary storage if needed. It is also used for hibernation.

> **NightwishFan said:**
> I didn't know that, thanks. Well I have never used a mac, I did not know it would be any different.No problem. It is common.

---

### Post by m84 on 2008-04-14
I found this which may be of help....

[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

The most interesting thing is that you do not have to create a swap partition to have 'swap' -it can be a conventional file which you can create which is apparently just as good as a swap partition. However, it also says that a swap partition is required for hibernation. I'm not sure if this is true, but if it is I will reinstall and create a swap partition. I have 2GB of ram so i suppose 4GB of swap is in order, although it is annoying to give up that much space.

---

### Post by cyberdork33 on 2008-04-14
> **m84 said:**
> I found this which may be of help....

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

The most interesting thing is that you do not have to create a swap partition to have 'swap' -it can be a conventional file which you can create which is apparently just as good as a swap partition. However, it also says that a swap partition is required for hibernation. I'm not sure if this is true, but if it is I will reinstall and create a swap partition. I have 2GB of ram so i suppose 4GB of swap is in order, although it is annoying to give up that much space.The reason you need that much swap is because you need to dump the entire contents of ram to disk for hibernation.

---

### Post by russo.mic on 2008-04-14
So,  Your swap partition is a kind of "Virtual Ram" for your computer.  

It's not a bad thing to have, but not a deal-breaker.  If you wanted to install w/o swap, no big deal.  You can always make a swap file should you find a need.   

Russo

---

### Post by russo.mic on 2008-04-14
So,  Your swap partition is a kind of "Virtual Ram" for your computer.  Akin to a paging file in Windows.  

It's not a bad thing to have, but not a deal-breaker.  If you wanted to install w/o swap, no big deal.  You can always make a swap file should you find a need.   

Out of curiosity (and not to thread hijack), does anybody know if OS X uses a swap file?  I've never even thought about it...Cyberdork?  Seems up your alley.

Russo

---

### Post by cyberdork33 on 2008-04-14
> **russo.mic said:**
> Out of curiosity (and not to thread hijack), does anybody know if OS X uses a swap file?  I've never even thought about it...Cyberdork?  Seems up your alley.
Funny you would ask me, I have not had a Mac that long... I am not sure if there is a swapfile, but there almost has to be... Windows has swap, though it is called something else... actually, i think it is called virtual memory!

EDIT: Yep, they are in /var/vm/

---

### Post by markus17 on 2008-04-15
I've also just installed Ubuntu on my MacBook (CoreDuo) and have some difficulties with it. Mostly because I know absolutely nothing about Linux. The tutorial given on the Ubuntu side would be extremely helpful, but it doesn't say HOW to do some of the things in the terminal it asks you to do. Anyone have a useful resource for new Mactel Ubuntu users? I'm suffering with not knowing what to do and no one to ask about it. Thanks.

I hope that wasn't thread hijacking....

---

### Post by cyberdork33 on 2008-04-15
> **markus17 said:**
> I've also just installed Ubuntu on my MacBook (CoreDuo) and have some difficulties with it. Mostly because I know absolutely nothing about Linux. The tutorial given on the Ubuntu side would be extremely helpful, but it doesn't say HOW to do some of the things in the terminal it asks you to do. Anyone have a useful resource for new Mactel Ubuntu users? I'm suffering with not knowing what to do and no one to ask about it. Thanks.

I hope that wasn't thread hijacking....

You probably should have started a new thread, but it's OK.

Well, you will have to be more specific with your question. What guide are you following? "The tutorial given on the Ubuntu side" could mean a lot of things. (link?) Secondly, if you are having a problem with a particular command, just ask your question about that. I am pretty sure that you can almost just copy and paste into the commandline to get things working as stated, so if you are having difficultly with a certain portion you will have to give a hint to what the issue is.

---

### Post by mrsteveman1 on 2008-04-15
What is this Lunix you speak of :D 

I wish it was called Lunix, such a cool name

---

