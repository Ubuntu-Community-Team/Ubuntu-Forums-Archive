---
title: "Install Partition Problems"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by skyman375 on 2006-05-17
I'm installing on an old HP Pavilion (Celeron 433 mhz, 64 MB RAM, 8 GB HD, had Windows 98 installed). When I boot from the Ubuntu CD, I get to the partition screen, and it can't seem to detect the hard drive to set up the partition. 

When I slect the continue option from the partitioner, the screen flashes, and I see the following error:

E: unimplemented function

from there, it just loops - no change, just right back to the "go back" or "continue" option in the partitioner.

---

### Post by zhoux on 2006-05-17
[QUOTE=skyman375]I'm installing on an old HP Pavilion (Celeron 433 mhz, 64 MB RAM, 8 GB HD, had Windows 98 installed). When I boot from the Ubuntu CD, I get to the partition screen, and it can't seem to detect the hard drive to set up the partition. 

When I slect the continue option from the partitioner, the screen flashes, and I see the following error:

E: unimplemented function

from there, it just loops - no change, just right back to the "go back" or "continue" option in the partitioner.[/QUOTE]

did you allow the partitioner to automatically partition your hdd?

---

### Post by skyman375 on 2006-05-17
It didn't automatically partition, that's the problem. I get the E: error, a screen flash, and an infinte loop.

---

### Post by zhoux on 2006-05-17
did you check the disc for integrity?

I'm a noob at linux, but i like to help out.

---

### Post by Sef on 2006-05-17
Possibilities:

1) Bad CD - Reburn

2) Bad burn - Reburn

3) Bad download - Did you md5sum the download?

[https://wiki.ubuntu.com/HowToMD5SUM?highlight=%28md5sum%29]("https://wiki.ubuntu.com/HowToMD5SUM?highlight=%28md5sum%29")

---

### Post by skyman375 on 2006-05-17
I was thinking it might be a problem with the Hard Drive. Is there anything I should have done to prep the HD? IT had win 98, and was reformatted from the dos prompt.

---

### Post by skyman375 on 2006-05-17
I downloaded from OS X, so I didn't do the MD5Sum.

---

### Post by zhoux on 2006-05-17
[QUOTE=skyman375]I was thinking it might be a problem with the Hard Drive. Is there anything I should have done to prep the HD? IT had win 98, and was reformatted from the dos prompt.[/QUOTE]

I don't think it is the HDD becuase, the partitioner will automatically reformat it.
Can the partitoner be loaded?

---

### Post by skyman375 on 2006-05-17
The partitioner loads, I get a dialog like this:

[!! Partition Disks]

[go back] [continue]

When I highlight continue and press enter, I get a flash where I can see the 
E: unimplemented feature

and then right back to the dialog prompt

---

### Post by zhoux on 2006-05-17
[QUOTE=skyman375]The partitioner loads, I get a dialog like this:

[!! Partition Disks]

[go back] [continue]

When I highlight continue and press enter, I get a flash where I can see the 
E: unimplemented feature

and then right back to the dialog prompt[/QUOTE]

Can you select options as how the partitioner will partition your disk. for example: manually edit the partition table....

---

### Post by skyman375 on 2006-05-17
No, that's all that comes up. It's a gray dialog box, with only those options.

---

### Post by Sef on 2006-05-17
> I downloaded from OS X, so I didn't do the MD5Sum.

That could be the problem, unless OSX automatically checks the md5sum.  That I do not know.  Does anyone know if it does automatically check the md5sum, or how to do it on OSX?

---

### Post by zhoux on 2006-05-17
[QUOTE=skyman375]No, that's all that comes up. It's a gray dialog box, with only those options.[/QUOTE]

That's a weird problem, can you highlight [Partition Disks]?

---

### Post by Sef on 2006-05-17
> No, that's all that comes up. It's a gray dialog box, with only those options.

I would redownload the iso.  From what you wrote you have a bad iso.

---

### Post by skyman375 on 2006-05-17
Can't highlight anything but [go back] or [continue]. One other thing - sorry I'm going back and forth between two rooms, it actually looks like this:

[!! Partition Disks]
??? ???
[go back]  [continue]

do the ?'s mean anything?

---

### Post by skyman375 on 2006-05-17
I'm re-downloading now. Thanks,

---

### Post by zhoux on 2006-05-17
[QUOTE=skyman375]Can't highlight anything but [go back] or [continue]. One other thing - sorry I'm going back and forth between two rooms, it actually looks like this:

[!! Partition Disks]
??? ???
[go back]  [continue]

do the ?'s mean anything?[/QUOTE]

I would suggest to redownload .iso and reburn it.

---

### Post by Sef on 2006-05-17
Download BitTorrent, so you will get a good download.  It will automatically md5sum the iso file.

[http://www.bittorrent.com/]("http://www.bittorrent.com/")

---

### Post by skyman375 on 2006-05-17
I used BT the first time, then burned via toast.

---

### Post by skyman375 on 2006-05-17
Just downloaded (via BT) and reburned. Ran install, and had the exact same problem. Any other suggestions?

---

### Post by JamesD on 2006-05-18
Hi please bear in mind that I have been reading this board for about 10 minutes, have been registered for about 5 minutes and have never installed Ubuntu. I will do so tonight when I get home.

However. Here is what I would do. First I would start a down load of the LiveCD (?) you know the one you don't have to install. Just run from the CD. While that is downloading. Delete the partion on the Compaq and try it that way. If it doesn't work, try the Live CD. Does that boot? Can you partition the drive from there? 

Those steps should tell you where the problem is.

Also people seem to recommend burning the CD slowly. I assume you now have 2 dowloaded ISOs of about 600MB each? If all seems well from the Live CD you could try a slow burn. However seeing as you get the same problem from 2 install ISOs I suspect you have a hardware problem. You may need a new (well a new, old) hard drive. Or it might be something else.

I do have a Compaq like that. It's not used at the moment. I guess I could send parts. So long as it didn't cost me much. It's not worth sending a hard drive, too heavy, too fragile, too cheap to buy. But the Compaq bits are non of those and I don't need them. Sorry I don't remember where you are.

Good luck. I'll check back in a few hours.

JD

---

### Post by JamesD on 2006-05-18
Nothing more, error posting. It went up twice. I'm trying to delete this one.

JD

---

### Post by Sef on 2006-05-18
JamesD:

Please start a new thread with your post.  Otherwise it looks like you are hijacking this one, which I am sure is not your intent.

---

### Post by Sef on 2006-05-18
Skyman:

1) Have you tried a live cd to make sure that your system will work with Ubuntu?

2) Use GParted either by itself or on the livecd and delete the partitions all the partitions and reinstall Ubuntu.  I used GParted to delete my partitions and reinstalled them with the install CD to get Ubuntu on my system.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by skyman375 on 2006-05-21
I tried using the Live CD, and it never actually completed loading (I think the processor is just too slow). I did correct the partitioning problem though. I booted a windows XP install cd and used it's partitioning app to repartition the disk. Then, I stopped the XP disk, and re-installed from the Ubuntu install disk, and the partitioning app worked fine this time, and the rest of the install went well. 

Unfortunately, the system is so slow (I think the combination of slow processor, low RAM, and a slow HD) that it's still almost totaly unusable. I will need to invest in some better hardware to really get a chance to use Ubuntu. Thanks for the help with this issue.

---

