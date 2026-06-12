---
title: "Installation/Partitoning/Hard Drive problems- help!"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by b-dizzle on 2006-06-04
Hello everyone, first off I'm brand new to the whole magical world of Linux, so excuse my n00bness.  I've been trying to get Ubuntu to install on my old computer, but have had some problems.

I'm trying to dual-boot with windows.  So first, I tried the manual partitioner in the Ubuntu installer.  Didn't work, and someone on the IRC informed me that the installer doesn't always play nice with NTFS, which was what I was trying to resize to make space for Ubuntu.  So they referred me to GParted, which didn't work either.  Tried Partition Magic, it didn't work either.  So then I scanned and defragged the drive and tried Partition magic again.   It didn't work again, and this time it stalled, so I had to turn it off manually.  Now Windows won't even start up - it flashes a blue screen but it disappears before I can read it.  When I try to access the drive via the Ubuntu live CD, it says it can't mount it.  It didn't have a problem with that before.

So, a few questions: are all my old files screwed?  Is there a way to recover them?  The only obvious way out I can see is reinstalling Windows; if I do this, can I somehow get to my old files?

And after I get Windows back up, does anyone know why it won't partition my drive?  Actually, I guess I could just repartition it when I reinstall windows.  

Sorry this question isn't totally Linux related, I just figured you guys probably know a lot more about this kind of stuff than I do, regardless of what OS you use.

---

### Post by skymt on 2006-06-04
Hmm. You have a problem. It's odd that Partition Magic wouldn't work for you. It's what I used installing Linux for the first time, and it resized my Windows NTFS partition perfectly. My best guess is that something in one of the previous partitioning attempts messed it up enough to confuse PM (which is pretty hard, but possible).

Anyway, I hope you have a backup, because your best bet right now is reformatting the drive. Install Windows first, over the entire drive. Resize the partition using Partition Magic. Then install Ubuntu in the empty space.

If you have essential data that you haven't backed up, you should have. ;) 

If you really, really need that data, get a good disk repair/recovery program. I've heard good things about [Spinrite](http://www.grc.com/spinrite.htm), but it's pretty expensive. If you find something that works for you, immediately boot to a live CD (convenient that you already have one, isn't it?) and back up.

I hope I've helped. I know it can be frustrating; I've had to reinstall various operating systems many times, most of the time after disk trouble.

---

### Post by Loffe_ on 2006-06-04
Partition Magic worked for me.

But I've heard others calling it *Partition Tragic*. Not to good...

Maybe you could try WinXP recovery console which is on the install disk. Otherwise you should tri a live-cd with programs to fix harddrives.

---

### Post by Merlin Whitewolf on 2006-06-04
[QUOTE=b-dizzle]Hello everyone, first off I'm brand new to the whole magical world of Linux, so excuse my n00bness.  I've been trying to get Ubuntu to install on my old computer, but have had some problems.

I'm trying to dual-boot with windows.  So first, I tried the manual partitioner in the Ubuntu installer.  Didn't work, and someone on the IRC informed me that the installer doesn't always play nice with NTFS, which was what I was trying to resize to make space for Ubuntu.  So they referred me to GParted, which didn't work either.  Tried Partition Magic, it didn't work either.  So then I scanned and defragged the drive and tried Partition magic again.   It didn't work again, and this time it stalled, so I had to turn it off manually.  Now Windows won't even start up - it flashes a blue screen but it disappears before I can read it.  When I try to access the drive via the Ubuntu live CD, it says it can't mount it.  It didn't have a problem with that before.

So, a few questions: are all my old files screwed?  Is there a way to recover them?  The only obvious way out I can see is reinstalling Windows; if I do this, can I somehow get to my old files?

And after I get Windows back up, does anyone know why it won't partition my drive?  Actually, I guess I could just repartition it when I reinstall windows.  

Sorry this question isn't totally Linux related, I just figured you guys probably know a lot more about this kind of stuff than I do, regardless of what OS you use.[/QUOTE]

I can't help with the windows files. Sorry. But I may be able to help with the partioning issue. If you do this, you may or may not need to reinstall windows. It took 3 tries, but I downloaded and burned the gParted live CD. The first 2 attempts were unbootable, then only partly functional. The reason to use the live CD rather than the program is that you can't reformat a mounted drive and the program can only work from a mounted drive. 
If you can get into windows, defrag it. This is very important as windows has a habit of scattering files all over the hard drive. Not drefragging may cause some files to be deleted.
Boot from your CD (or DVD) drive with the live CD in it. When it has gone through the set up, the gparted interface will load. Use gparted to resize the windows partition. When that has been completed, create a logical partition in most of the space you gained and format it to ext2. The space you left unused is to be used to create a swap partition. This can be at either end of it. This should be a minimum of 512mb, but I'd recommend a gig or a gig and a half for better performance. Exit gparted, remove the CD and turn off your pc. You may have to wait until after you restart your computer to remove the CD.
If you're sure your windows is okay, install Ubuntu to the logical partition you just created and set it to use the swap partition you created. When you've rebooted after the install, you'll see your windows listed on the menu. 
If you need to reinstall windows, do that first. It may offer complaints about the "unknown" partition type of your ext2 partition, but you can get it to install to the ntfs partition only. Then you can proceed with the Linux install. 

***Important*** Installing windows after linux will make your linux unbootable. Windows wants to be the "only OS" and will not cooperate with booting non windows OSes. :evil:  
That is why grub is needed. It will boot either.

-Merlin
"Learning is always one step at a time."

---

### Post by b-dizzle on 2006-06-04
> **skymt]
If you have essential data that you haven't backed up, you should have.  said:**
> 
Yeah, nothing uberimportant like Quicken files or legal stuff, the only thing I don't really have backed up is pictures.  It'd be nice to get em back, but not $89.99 nice...
[QUOTE=Loffe_]Otherwise you should tri a live-cd with programs to fix harddrives.
Any suggestions on that front?

After thinking about what I use that computer for (and the fact I now have a new one that I could do Windows stuff with), I'm thinking my plan may just be to try and recover anything I wanna keep, then format it and just run Ubuntu on it.  The only think I need it to do that I'm not sure it can is network with my Windows computer (I already know it can find the network and grab internet off it; I just wanna make sure file sharing and network printing works).  If there's any "heads-up"s from you guys on this front, let me know.  

And thanks for all the help so far.  I'm really starting to like the community aspect of Linux- you guys are at least 50x better than Dell or Microsoft support.

---

### Post by longinus on 2006-06-04
The same thing happened to me.
I've been using Ubuntu on one of my PCs for some time now, and I dual boot there. SOoo when Dappper came out, I decided to install it on my main PC (the one I work on), partly to have a good hardware to use Cinerama, etc..

BUT the partition editor destroyed my partition. Left me with a disk that can't be recognized.

I tried a lot of diferent programs to restore it.. Only the partition tables, mbr, etc, I didn't touch the data (no chkdisk, etc,etc). But nothing worked.

So I'm left with Ontrack EasyRecover.. It can't find the files in NTFS mode, BUT it can in RAW. Problem is the files don't have a name..only extension.. like FILXXXX.jpg. Anyway, it's better than nothing. I'm still trying to recover the lost partition, but I'm giving up.... I fell I little better knowing I can recover the files, even without their real names. 

Well... I over trusted the partition tools.. I shouldn't have.. ](*,)

---

### Post by confused57 on 2006-06-04
[QUOTE=b-dizzle]Hello everyone, first off I'm brand new to the whole magical world of Linux, so excuse my n00bness.  I've been trying to get Ubuntu to install on my old computer, but have had some problems.

  Now Windows won't even start up - it flashes a blue screen but it disappears before I can read it.  When I try to access the drive via the Ubuntu live CD, it says it can't mount it.  It didn't have a problem with that before.
[/QUOTE]

You may be able to press "scroll lock" or "pause break" when the blue screen appears to read the error message...then go online with the LiveCD and search for it.

Try opening up a terminal  with the LiveCD & type in:
```
sudo fdisk -l
```
the -l is a lower case "L"

Really though, gparted should show your partitions...?

See if there is something here that might help:
[http://psychocats.net/ubuntu/mountwindows.php](http://psychocats.net/ubuntu/mountwindows.php)

---

### Post by p1r0 on 2006-06-04
I'm going to ask a silly question, but: have you tried to put your drive as slave on another windows computer to recover your files???

If you haven't and you do it and works then you should use some dos/linux tool like fdisk and erase your partitions and create them back again. If you are installing win xp or 2k you don't need fdisk, just tell the installer to erase all your partitions and then create them.

In any case you shoul make your new windows partition as large as needed for windows and left the rest unpartitioned to make an ext2/3 partition for Linux with Partition Magic. Just to avoid the issue of resizing partition.

Hope this helps.

p1r0

---

### Post by Loffe_ on 2006-06-05
Put the disk as slave in a working Windows computer. Then you should give GetDataBack a try. I used it to recover some files from an erased partition some weeks ago.

[http://www.runtime.org/](http://www.runtime.org/)

---

### Post by b-dizzle on 2006-06-05
w00t.  I tried the installation on the liveCD again today just for kicks, and found that Partition Magic infact DID resize my Windows partition- it just stalled right afterwards.  So I'm installing ubuntu on the meager 6 gigs I have right now.  

Does anyone know of some sort of disk recovery program I can download and run in Linux?  If so, I can use it to get the files I want, format the drive, install Windows and then install Ubuntu, and everything will be cool.  I could also do the slave drive thing, but this sounds easier.

Thanks in advance.

---

### Post by b-dizzle on 2006-06-05
Super w00t.  For whatever reason, Ubuntu can now access the main Windows partition with all my files on it.  I havn't tried booting windows yet (although GRUB detected it when rebooting after the installation), but things are looking up, and substantially less expensive/depressing.  I'll edit this as things happen.

---

### Post by Loffe_ on 2006-06-06
Nice to hear that from you. Even when everything seems lost, there might be a solution falling down on you :D

---

### Post by carverj on 2006-06-06
Yes, its very easy to overlook the partitioners might. I have made the mistake of thinking I needed some third party partitioners help, or some file rescue program, when in fact its all right there on the install cd!! 
You learn from trial and error, and asking the right questions and looking in the right places
I have set up a back up a slave drive and have no probs. running 4 different OS's and sharing data between them. So that capability is always there to if you need it. After all, unless you have crossover office, there are some benefits of dual boot.

Have fun and well done
=D>

---

