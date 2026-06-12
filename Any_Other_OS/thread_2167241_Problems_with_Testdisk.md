---
title: "Problems with Testdisk"
date: 2013-08-12
forum: Any Other OS
---

### Post by theorange9 on 2013-08-12
Hey guys,
I accidentally shut off my computer while resizing partitions, (battery ran out) and now one of the partitions is screwed. (I have a windows ntfs and a mac hfs+) However, the Mac partition still works fine. I got a new hard drive and cloned the old one onto it using clonezilla, as I was planning on using testdisk to rebuild the boot sector. However, I think it might be a better idea to just somehow gain access to my corrupted partition, copy my important files, then just wipe the drive, reinstall mac, reinstall windows, then just put all my files back in. I believe there is a way to do this in testdisk, however, I am having quite a few problems with it.

I am running testdisk on Mac OS X.

First of all, as soon as I open any device, testdisk states that it does not have write privileges, even though I set all permissions to "read and write" I think that because it is in read only mode, I am missing many features.

Second, when I attempt to do a quick search, it goes insanely slow. For some reason, the search always starts at 36%, and in the last one and a half hours, it has climbed to 37%. Is it supposed to be that slow? I might also mention that I am accessing the drive via a had enclosure with 2 USB 2.0 ports.

What would be the best possible way to recover my files? I'm not really that familiar with testdisk.

Thanks in advance for any help.

I do have to mention, I typed this all on a mobile device, so if I missed any details I'll be glad to clarify.

---

### Post by varunendra on 2013-08-13
> **theorange9 said:**
> ....I think it might be a better idea to just somehow gain access to my corrupted partition, copy my important files, then just wipe the drive, reinstall mac, reinstall windows, then just put all my files back in.
Good Idea.

> I'm not really that familiar with testdisk.
Here's how : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

It is the step after "[Deeper search]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search")" where you get the option to list (using 'P' key) and copy the contents (files or entire directories) if they could be listed.

I don't know how testdisk works on a Mac, so may not be able to help beyond this.

**PS:**
Neither your source (where you'd be running testdisk from) nor the target partitions are Ubuntu or linux based, and the accident also doesn't seem to be related with Ubuntu or Linux in any way. So why are you asking this question on Ubuntu Forums? Just trying to figure out if I'm missing something here..

---

### Post by coffeecat on 2013-08-13
> **theorange9 said:**
> (I have a windows ntfs and a mac hfs+)

What hardware are you using? Is this an Apple machine?

---

### Post by theorange9 on 2013-08-13
> **varunendra said:**
> Here's how : [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

It is the step after "[Deeper search]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search")" where you get the option to list (using 'P' key) and copy the contents (files or entire directories) if they could be listed.

Ahh yes, I have seen that page, the problem is, the quick search seems to take eternities to finish. It also seems to do that with the deeper search.

> **varunendra said:**
> [B]PS:
Neither your source (where you'd be running testdisk from) nor the target partitions are Ubuntu or linux based, and the accident also doesn't seem to be related with Ubuntu or Linux in any way. So why are you asking this question on Ubuntu Forums? Just trying to figure out if I'm missing something here..[/B]

I have a ubuntu live cd, should I use that? Also, I think I was supposed to put this in the Apple Users subforum, but I must have forgot that existed... I posted [this post]("http://ubuntuforums.org/showthread.php?t=2162685"), more detailed description of my situation there.

> **coffeecat said:**
> What hardware are you using? Is this an Apple machine?

Yes, I have a 2011 MBP 8,2.

---

### Post by varunendra on 2013-08-13
Since your partition seems to be already pretty messed up, I'd suggest to just let testdisk do it's job at its own pace *(which is usually faster than most data/partition recovery tools if the partition is healthy)* if there are no physical errors on the partition and/or is not looping over some particular cylinder area.

If it does report physical errors (bad clusters etc.) or starts looping over a certain area, you may try "ddrescue" program to create an image of the drive/partition. You can then use this image instead of the physical drive to recover data. It is safer and recommended where there are physical problems with the drive and may get worse with continued usage. However, if the drive is physically healthy, forget this paragraph and just let testdisk finish its job.

---

### Post by theorange9 on 2013-08-13
Surely its not supposed to go at .5%/hour though? I read that it reads about 80gigs/5mins. Also, it starts at 36% for some odd reason. It has about 1,950,000,000 cylinders to search on my drive.

---

### Post by varunendra on 2013-08-13
> **theorange9 said:**
> I read that it reads about 80gigs/5mins.
I think it is the maximum possible speed in ideal conditions, while actually it depends on the status of the partition/data to analyse. The last time I used it, it took about 24+ hours to scan a 250 GB drive, and I also remember it recovered a 100 GB+ partition in less than 45 minutes once.

But 1,950,000,000 cylinders sound impossible to me.  Are you sure you chose correct partition table type in the beginning (Intel or Mac or EFI/GPT...)? Maybe you need to manually set its geometry in testdisk, but I have never gone that far and [s]is definitely very[/s] [COLOR="#FF0000"]**Edit : maybe** *(since the change is temporary until the partition table is written)*[/COLOR] dangerous if done without proper understanding of what you are doing.

For reference, the number of cylinders in my 500 GB HDD is 60801 (Intel partition table).

---

### Post by theorange9 on 2013-08-13
Oops, my bad, I meant to say 1,950,000,000 sectors. Its a 1TB hybrid drive. Testdisk doesn't seem to show how many cylinders it is. If I took it out of my enclosure and hooked it up to the sata port in my macbook, will it scan faster? It's sata III 6gbps, so its probably much faster than whatever 2 usbs are...

---

### Post by theorange9 on 2013-08-13
Also, I have a couple messages when quick searching:

check_FAT: Unusual media descriptor (0xf0!=0xf8) < I have no idea what this is.

Warning: number of heads/cylinders mismatches 16 (FAT) != 1 (HD) < Apparently this is supposed to happen when there is a corrupt partition.

Warning: number of sectors per track mismatches 32 (FAT) != 1 (HD) <I'm not sure, but I think this is also supposed to happen.

---

### Post by varunendra on 2013-08-13
> **theorange9 said:**
> If I took it out of my enclosure and hooked it up to the sata port in my macbook, will it scan faster?
Definitely.
Also, testdisk probably works best on Linux, so running it on Ubuntu (the live cd that you already have) may further improve performance.

> **theorange9 said:**
> 
check_FAT: Unusual media descriptor (0xf0!=0xf8) < I have no idea what this is.

Warning: number of heads/cylinders mismatches 16 (FAT) != 1 (HD) < Apparently this is supposed to happen when there is a corrupt partition.

Warning: number of sectors per track mismatches 32 (FAT) != 1 (HD) <I'm not sure, but I think this is also supposed to happen.

I'm not very sure about these errors either. But the warnings can be removed by manually setting the CHS value to what testdisk expects. Scanning with these mismatched values means the recovered partition/files may not be intact.

As far as I know, all the changes you make (changing geometry, chs values etc.) are all temporary changes that testdisk uses to determine 'how to parse' the data. These changes become permanent only when you "Write" the detected/suggested partition table structure to the disk. Before doing that, you will have the option to list and copy the data which you can verify for integrity.

If no data could be listed after the deeper search, it means the parsing/analysis didn't go well and probably you need to re-scan the partition with different geometry/chs values.

---

### Post by theorange9 on 2013-08-13
I did as you said and ran testdisk on Ubuntu, and it works! For some reason on OS X it stated that there were 1,950,000,000 cylinders, when in fact those were actually the sectors. On Ubuntu testdisk shows the correct amount of 121,601 cylinders. The quick search was fast enough that I didn't really feel like hooking my he up to a sata  port, so it's still in the enclosure. Testdisk has searched about 30 percent in the past half hour, so I suspect that its working correctly. So now all I need to do once the search is done, is to copy the files over to a non-corrupt partition, correct?

---

### Post by varunendra on 2013-08-13
Aha ! Sounds cool !! :)
> **theorange9 said:**
> So now all I need to do once the search is done, is to copy the files over to a non-corrupt partition, correct?

Correct, if it can list the contents after the deeper search (or even a quick one, if you are super lucky). Make sure to verify the integrity of the copied files before "Writing" the partition table to the disk. If you are going to format the partition anyway after the file recovery, then of course there is no need to write the partition table.

---

### Post by theorange9 on 2013-08-13
My idea was to just copy the my documents and programs files folder or something, put it on my old 500gb hd, which I will be turning into a portable hd, then just install windows on a fresh hard disk, then replace the new program files with the ones on my portable hd.

Also, what do you mean by "verify the integrity of the copied files?" How would I go about doing that?

---

### Post by theorange9 on 2013-08-13
Alright, so I have the files and am ready to copy them over, but one problem: obviously, the fact that I'm running Ubuntu on a DVD doesn't give me much space for stuff, and when choosing which directory to copy to in testdisk, it only lets me choose the partition I'm using-the Ubuntu DVD. Is there any way I could save it to my mac partition?

---

### Post by varunendra on 2013-08-13
> **theorange9 said:**
> what do you mean by "verify the integrity of the copied files?" How would I go about doing that?
By verification I meant to just open the files to see if they were intact and can be opened fine. You could do it with all the files if possible or just a few of them as 'samples'.

> **theorange9 said:**
> when choosing which directory to copy to in testdisk, it only lets me choose the partition I'm using-the Ubuntu DVD. Is there any way I could save it to my mac partition?

You will need to mount the target partition(s) with read-write access. For that you may need to install "hfsplus" and/or "hfsprogs" package(s) -
```
sudo apt-get update
sudo apt-get install hfsplus hfsprogs
```
(you must be connected to internet to do above)

Once they are mounted, browse to **/media/<mount-point>/<your preferred directory>** using left/right/up/down arrow keys in testdisk > then 'C' to confirm the correct directory (as mentioned in testdisk screen itself).

---

### Post by Bucky Ball on 2013-08-14
*Thread moved to **Other OS/Distro Support**.*

Frankly, unsure why this is on these forums as it is primarily about Mac and Win. You might be better asking on the appropriate forums. Good luck, nonetheless.

---

### Post by theorange9 on 2013-08-18
Sorry I haven't replied in a while, too busy enjoying my windows! I guess it worked, I recovered my files with testdisk, then spliced the files into a new installation, and everything works greats! Thanks for all the help guys!

---

