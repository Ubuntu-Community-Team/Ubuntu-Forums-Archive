---
title: "Dual Boot ubuntu with xp"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by krunk on 2007-02-22
Hi, Im trying to dual boot ubuntu with Winxp SP 2. I've got the latest ubuntu desktop live CD, im using it right now to send this message. However, when I try to install Ubuntu on this machine I get an error saying that the partition space could not be created.. I've been told I need to use Gnome partition editor to create the space but im not sure how to go about doing this.. 

do i resize /dev/hde1 and leave space for ubuntu? or create new in the " unallocated " section (which currently has 7.84mb assigned to it.

Im lost here so any advice would help, thanks! :)

---

### Post by Jsu07 on 2007-02-22
You need to decrease the size of your XP partition. It will then have unused memory and that is where you will create the new Ubuntu partition. Dont forget to allocate space for your swap partition. Hope this helps. I usually allocate 9gb and 1gb for the swap. The swap needs to be roughly as big as the amount of RAM you have.

---

### Post by igknighted on 2007-02-22
Defrag your WinXP drive a couple times before you install Ubuntu as well so the data is in the front of the drive and you wont overwrite it by resizing.

---

### Post by krunk on 2007-02-22
OK im defragging my winxp drive right now, but just so we're clear here.. I use Gnome to resize my 60gb hd and size up about 10gb. Then when i run the ubuntu install it should have enough space?

Do I need to do anything else with Gnome before running the install, or just re-size my current HD partition? Thanks!

---

### Post by krunk on 2007-02-22
ok im really lost here, Im clicking Manually Partition from the LIVECD install options, since it encounters an error when i try for the CD to do it automatically.

Do i need to click "NEW" and make a partition? what type should it be? ext3? then also make a swap partition that is 1gb? im so lost i just need someone to tell me what i should be doing to  partition my drive correctly.... thank  you!

---

### Post by rusty4r on 2007-02-22
Don't give up your on the right track. I can't remember the exact screen so I suggest you google "Ubuntu Linux Resources". This web page is a how to written just for new to Linux users like me. It has what you need and much much more.

I don't know yet how to put a link in here or I would just do that.

Hope you find that page as much help as I did.

---

### Post by jml on 2007-02-22
Have you already shrunk the Windows partition?  If yes, then you should have free space on your drive.  Be sure the next steps you do are going to be applied to the free space.  A good rule of thumb is to create a swap partition that is about twice the size of your computer's ram.  For example if you have 256 megs of RAM, create a 512 meg swap partition.  As for the file system, I prefer ext3.

Joe

---

### Post by rusty4r on 2007-02-22
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")

Here is that link you need.

---

### Post by geovino on 2007-02-22
For someone new to Ubuntu... here's a fun video to watch about installing Ubuntu for the first time. [http://adventuresinlinux.tv/main/content/view/15/53/](http://adventuresinlinux.tv/main/content/view/15/53/)

Check it out. it's pretty good!

---

### Post by krunk on 2007-02-22
Thanks for your help guys, if I could just get past this one issue.. im sure I'd be fine. BUT.. no matter if I use Gnome or Partition Magic, I get an error while trying to re-size the drive. Partition magic gives me a " #1529 Information mismatch in directory entry " error. Anyone else encountered this and know how to fix it?

---

### Post by rusty4r on 2007-02-22
Well I don't know what the error is but, I've read that you should not use partition magic and I'm not sure what you mean by using Gnome. If your using the utility that does the partitioning after you click the install icon thats Gparted. Which is what i would use.

I'll search and see about the error message.

---

### Post by rusty4r on 2007-02-22
I found this thread that might be of help.

[http://www.ubuntuforums.org/showthread.php?t=360784&highlight=partition+error]("http://www.ubuntuforums.org/showthread.php?t=360784&highlight=partition+error")

---

### Post by timohnani on 2007-07-31
Hi guys,

I had the same problem. I also got the error 1529 with partition magic. I tried defragmenting but to no avail. However after reading around these forums I finally managed to make it work. I did this by first running the windows defrag programme about 3-4 times. Each the process too less time to complete indicating quite a non-fragmented disc. 

After this I run GParted using the live CD and managed to make the partitions. I achieved this by first re-sizing my Windows XP (NFTS) partition. After this I created the necessary linux partitions. 

Then I just installed Kunbuntu. During the installation I used the "manual partitioning". I then set the mount points and checked the options to format and everything went fine. 

I have no idea whether it was GParted that made the difference or the fact that I defragmented several times. But now its ok. 

Timo

---

