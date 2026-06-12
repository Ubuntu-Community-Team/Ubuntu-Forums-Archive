---
title: "Making the Jump – Installation and setup check"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by Village on 2006-11-06
I’ve been playing around with Ubuntu for a month or so now, put Xubuntu onto an old Laptop and other than having big problems with my wifi card I’ve thought it worthwhile. So I’ve got hold of a 60gb hard drive and I am going to put that into my computer. I just wanted to check a few things first, before I jumped in. 

Spec;
2.66 MHz Intel P4
1Gb Ram
Belkin Wireless Desktop Network PCI 54g Card 
180 GB Storage HD
60 GB Windows HD
60 GB Ubuntu HD 
NVidia 6200
Dual Monitors –
	i. 1704 FTP
	ii. E151 FPp

I tried running the Xubuntu 6.10 live CD (it was the only one I had) and I don’t think the Monitor Driver works correctly, however on the Ubuntu 6.06 live CD it does. Should I just have one monitor, the more basic one, play around with it and then try and get Dual monitors to work. 

I’m planning on installing Ubuntu 6.10

My questions are;
1.
Should I install 6.10 right away, or 6.06 LTS and then upgrade to 6.10? 

2.
I was planning on having each OS on each Hard Drive along with their associated programs, but having the storage HD read by both is this possible? My storage HD is where the music, docs and images are. 

3.
Dual booting, is this possible with different OS’s on different HD’s? If so how?

4.
Should I just have one monitor, the more basic one, play around with it and then try and get Dual monitors to work. 

5.
Wifi Card, internet is very important. Do I need Ndiswrapper to get it to work? I should be able to figure that one out. 

I will of course back up to the Storage HD, which should be safe. I’ll only be installing Ubuntu onto the new HD.  

Thanks,
Village

---

### Post by ironfistchamp on 2006-11-06
Ok lets see if I can answer the questions. I am by no means an expert in Ubuntu but I am sure I can give you some useful information.

1)Install 6.10 if the Live CD works. If not and 6.06 works install that and you can try to update if you want. Well that is what I would do in your position but then again I don't mind reinstalling if I mess things up.

2)With the storage hard drive you may have a problem. If you mean you want to put you /home directory on it (which is possible) it will need to have an ext2, ext3 or reiserfs filesystem. You can't put your /home dir on a Vfat partition. Windows can read and write to ext2/3 filesystems but only with a special driver installed. I will try and find the link. If you just want it as a storage drive (as in not using it as your home directory) then you can have it as Vfat.

3)It is possible to Dual Boot with multiple OSes on multiple harddrives. I am doing it now. GRUB just works it out.

4)Stick with one monitor (the one that works) and play about with dual monitors when you have just one working as you wish.

5)You may need NDISWrapper. There may be native drivers but no one can say without the make and model of the card. It may be that even NDISWrapper can't help but it is supporting more and more cards.

Hope this was of some help

Ironfistchamp

---

### Post by Village on 2006-11-06
Thanks a lot for that,

Going to jump tomorrow probably. Figures crossed. 

My main thing is the storage HD. I think I might just keep it as a windows HD, and let linux access it. Like I said my music library and all docs are there, therefore both need access. Might have to get my head around NFTS and all that. I’m still very new to all this. I’m more of a computer user than computer engineer.

---

### Post by ironfistchamp on 2006-11-06
Good luck making the jump :D 

With the storage thing, make sure everything (and I mean everything) on that drive is backup. I can't count the number of times I have thought its backed up, lost it and realised I can't restore it.

If you are interested my hard drive setup looks like this:

Hard drive 1: 80Gb total, 20Gb NTFS and 60Gb NTFS (one for windows one for apps) - note Windows docs stored on here. 

Hard drive 2: 80Gb total, 80Gb reiserfs for Ubuntu Linux Edgy Eft

Hard drive 3: 120Gb total, 120Gb ext3 for all docs, music and that. Windows and Linux can read and write to it.

---

### Post by Village on 2006-11-07
Do you mean Back up the whole of my storage drive? that could take a while. 

I figured it would be safe as I'm only installing Ubuntu on to the new HD.

Is this because allowing read/write abilities to both Windows and Ubuntu could all go wrong?

Thanks,
Village

---

### Post by caravel on 2006-11-07
I would have the storage drive as FAT32 (the old Windows 95/98/ME filesystem, similar to the older MSDOS FAT filesystem) because Linux can read and write to it, and so can Windows obviously.  That way you won't have to install any drivers in Windows for ext2/ext3.  You'll have to back it all up, create new partitions and reformat in FAT32, if it isn't in FAT32 already of course.  You should do all of that from windows before you even install Linux.

When Linux is installed it will create a bootloader in the master boot record of your windows partition (the 60GB Windows HDD, presumably NTFS).  This, beside being vital to Linux actually booting at all, will also provide you with a boot menu allowing you to select the OS of your choice.  If you then decided you didn't want Linux installed anymore and deleted the Linux partitions from Windows disk management you would *break* this bootloader and render windows, and the whole system, ubootable.  So before you try that ask here first.

Another way to dual boot is to remove the Windows HDD completely and install The other HDD as a secondary master and install Linux to that.  This causes GRUB not to 'see' the windows partitions at all.  Then when everything is up and running you can replace the Windows CD and simply use the boot menu from your computer's BIOS setup utility.  This is usually accessed by hitting F8 after the system boots though it can vary.  With this method the GRUB bootloader doesn't touch your windows partition leaving the two independent.  The only common ground being the storage partition.  You should be careful when partitioning and installing Linux not to accidentally install over the Storage partition.

---

### Post by Village on 2006-11-07
Its sounding more complex all the time, still I guess I expected that, this windows machine is heavily used and has lots of bits and pieces on it. 

Perhaps I'll play it safe and just use the new 60gb HDD as Ubuntu only. Not allow access to the storage drive and just use it to play around on Linux. Prob would have default boot as windows and Linux for when I felt like it. 

yours getting scared,

Village

---

### Post by ironfistchamp on 2006-11-07
It sounds complicated but after a while you will get the hang of it. The reason I say back it all up is because if you get adventurous and what to try something interesting (like reformatting the Storage and changing the filesystem) you will want to make sure everything is backed up. Also it is just good sense. You never know when a power outage could kill it or something similar. It happens :( 

Ironfistchamp

PS: You could still mount the storage drive for read only access so you could just look at images and listen to music. Then later when you feel safer with Linux mount it as read and write and just save into there.

---

