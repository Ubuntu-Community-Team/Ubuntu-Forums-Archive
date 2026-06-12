---
title: "Defragmenting prior to partitioning"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by lefen on 2007-02-17
Hi all,

I'm just about to try to set up my machine as dual boot XP/Ubuntu 6.06 using the live CD installer. I'm planning in using Gparted to manually create additional partitions during the setup process and in preparation I've run the Window Disk Defragmenter a few times. Right now, my HD has only one partition, spanning the whole disk for my XP install.

As you can see from the screenshot, following defragmentation (about 3 runs), I've ended up with a bunch of contiguous files on the left, but some files still floating out in space on the right - the program just doesn't seem to want to move them with the others.


[[IMG]http://img240.imageshack.us/img240/823/fragmentedzf1.jpg[/IMG]](http://imageshack.us)


So, my question is, how can I move the outlying files back with the others? I'm asking since I assume that they'll force me to have a stupidly large NTFS partition and then very small FAT32 and Ext3 partitions? I was wondering if I could make the large partition smaller using Gparted on my Ubuntu live CD and forcing the files to move that way?

Thanks for any help (^_^)

---

### Post by mcduck on 2007-02-17
Boot windows into safe mode and then run defrag. Otherwise it can't move some files (as they are in use).

---

### Post by meng on 2007-02-17
Oh, you're so tantalizingly close to having a defragged partition!

---

### Post by floke on 2007-02-17
Don't worry too much about files on the right if they are movable (i.e. just 'normal' files). Gparted will sort it out. If you have green 'uinmoveable' files on the right then these are for the page file and the hibernation function. So turn hibernation and page filing off first. 

Post back and let us know how it all goes.

Good luck and enjoy

---

### Post by jvc26 on 2007-02-17
Aw that partition looks so close to being completely defragged! Safe mode defrag may well be your best option for that one if you have unmovable files in there.
Il

---

### Post by nickpaton on 2007-02-17
Welcome to the forums and ubuntu!

Have a look at this post:

[http://ubuntuforums.org/showthread.php?t=228464]("http://ubuntuforums.org/showthread.php?t=228464")

It rings a bell somewhere that it is swap information and will be recreated next time XP reboots so can be safely overwritten.

Suggest you wait for someone else to hopefully confirm

---

### Post by lefen on 2007-02-17
Hay guys, thanks for the quick replies!

I've just tried to defragment in safe mode and the files weren't moved. If anyone has any other suggestions I'd be very greatful, otherwise perhaps it's just a good idea to let Gparted do it's thing and automatically create an Ext3 partition out of the remaining disk space? 

I assume I'd be able to go back at a later date and add in a FAT32 partition on my main HD? It's not suck a big issue right now I suppose, since my external HD is formatted FAT32 and can be used to swap files.

---

### Post by floke on 2007-02-17
I had a similar thing a couple of days ago. Big unmovable files on the right - just turn off hibernation feature (power management) + turn off page file (I think this is in my computer - advanced - somewhere around here anyway - maybe google??). Then, sod it - just go for Gparted. When I was defragging my windows partition i had a picture just like yours (after removing hibernation etc.) - but when defragging again it moved a load of files to the right (dumb stupid **!$$!! windows) - so I had loads of blue to the left and some to the right but with a big white empty chunk in the middle - anyway - told GP to reduce Win to smallest possible size (leaving around 1G over minimum size since my wife uses it) and all was good.

Good luck

---

### Post by linux_kid on 2007-02-17
Don't worry about it, Gparted will move it for you, no big deal.  You don't need to do anything

P.S. Nice defragged drive :)

---

### Post by lefen on 2007-02-17
Hay all, well Gparted took care of it no problem.

I booted up the live CD, reduced my NTFS partition using Gparted and then added in a FAT32 partition. I hit install and let the thing create Ext3 and Swap partitions in the remaining space.

I've successfully installed Ubuntu and now have a dual boot box with Windows XP \(^0^)/ For the record, XP did a filesystem check the first time I booted back into it following repartitioning, but on the next reboot everything went as normal.

Thanks for the help everyone! Now I'm going to have fun getting Ubuntu to work with my USB modem! ;)

---

### Post by floke on 2007-02-17
Windows does that automatically - its a bit grumpy that you looked elsewhere:) 

Hey - enjoy Ubuntu mate!

---

### Post by stenci on 2007-02-18
I worked a few years with Unix 15-20 years ago. 
After a long break I decided to go back to the origin: yesterday I bought a new PC with Vista per-installed, the first thing after a quick setup of Vista I installed Ubuntu from a friend's CD.
I followed the steps creating a little Linux partition just to start. This is the configuration:
NTFS 300 GB
EXT3 20 GB
SWAP 2GB
RECOVERY 1GB
Then I installed Ubuntu and everything was fine. I could see the 2 Windows partitions with 19GB of stuff in the first partition.

Then I tried to reboot with Vista and... 
The reboot starts and after i get a desktop background and I see the mouse pointer, it hangs. The keyboard leds work and the mouse moves, but Vista is frozen.
I called the HP support and (after 3 hours and 17 minutes on the phone) they shipped me a recovery disk.

Is it "normal"?
Or did I do something wrong?

Thanks,
Stefano

---

### Post by floke on 2007-02-18
No idea about Vista - maybe it realised it was in the presence of a superior OS and disabled itself :) 

More likely, though - a problem with the dual boot setup - there are known issues (and fortunately also solutions) to this - don't know any links off the top of my head, but have a search around for Vista ubuntu dual boot.

---

### Post by linux_kid on 2007-02-18
Sorry about the Vista crap.
Rumor has it that Vista won't easily allow any other OS on the machine (are you surprised)
Microsoft is scared because they are loosing market shares :)

---

### Post by floke on 2007-02-18
Well, it can be done - so I've read - but its a bit trickier than dual booting with XP etc.

---

