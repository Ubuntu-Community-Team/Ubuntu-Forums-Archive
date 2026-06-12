---
title: "Installing to an already partitioned drive."
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by andrewsco on 2006-01-12
Hi. 

I think this is just a quick question. I used an excellent guide to partition my drive using this link:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

So I followed that except I have 50gb Windows, 10 gb free sapce with swap, and around 15gig for ubuntu. I am running the 5.10 version.

I messed around with some wireless settings and as I have no files think its easier for me to re-install than redo these as I dont know what I am doing. So, do I just install it to where ubuntu is now? Is it that simple? I was under the understanding that the free space can be accessed by both windows and linux, so is this still going to work?

Thanks
Andrew

---

### Post by Herman on 2006-01-12
Hello, Andrew,
> as I have no files think its easier for me to re-install than redo these as I dont know what I am doing. So, do I just install it to where ubuntu is now? Is it that simple? I was under the understanding that the free space can be accessed by both windows and linux, so is this still going to work?
 You should be able to re-install quite easily, I do it quite often, just for the fun of it. The simplest way to do that is to put in your 'Breezy' install disk, and when it gets to '[!!] partition disks', choose 'manually edit partition table' again, like you did before. Instead of getting a partition table like in the 9th ntfs illustration (on the hermanzone site), you'll see one more like 24 ntfs. Just highlight your Ubuntu partition and choose 'delete the partition'. If you delete the swap as well you should have only your 50.0 GB ntfs Windows partition left, and 25.0 GB free space.
Now, if you want, you can follow the example again, but this time starting at 14ntfs, and everything should work out okay for you, hopefully.

There is one very important thing I need to check to make sure you are clear about first though. You need to follow the example install carefully as it shows how to make a FAT32 logical partition first, then lets the Ubuntu installer automatically partition the remaining free space.
It is important to follow this carefully, because later on you need the FAT32 partition for both Windows and Linux to 'read and write to'. Operating systems can't normally read and write to free space, it has to be formatted with some file system.
I am sorry I haven't been able to get the website to be able to download .pdf files yet, I have tried. I would like it if you could easily print out the example install if you want. It's okay if you have another computer to look at, but maybe sometimes people miss certian steps if they can't see it on another monitor, maybe that's what happened?
It's perfectly okay to delete and re-install as often as you like, I do it a lot and I'm still learning more about it. There's a lot to learn, that's why it's so much fun. Good luck with it, Andrew, you are doing fine! :D   from Herman.

---

### Post by andrewsco on 2006-01-12
Thanks for the great reply. Really helpful.

When I get home from work (I've been naught - surfing the web...!) then I will have a try. I have only just installed windows, so there are no files really just a few game installs - nothing I cant afford to reinstall. Would be nice to get it right first time though then I get the experience of doing it. 

On a side note, did you write this tutorial? I only ask as I attempted to follow it with the 5.04 version and it didn't work. I'm not sure if I just messed it up or not, but the 22.3 ntfs screen didn't pop, so further down the line I got a couple of errors, that also knackered my windows install too.

I ended an upto date version, just wondered if its a simple step I missed?

Andrew

---

### Post by Herman on 2006-01-12
Hello, Andrew,
> On a side note, did you write this tutorial? I only ask as I attempted to follow it with the 5.04 version and it didn't work. I'm not sure if I just messed it up or not, but the 22.3 ntfs screen didn't pop, so further down the line I got a couple of errors, that also knackered my windows install too.
I ended an upto date version, just wondered if its a simple step I missed? Yes, it was me who wrote the three 'example' installs. I prefer not to call them 'tutorials' or 'instructions' because I'm not a real teacher or instructor. I am just a fellow student (and/or enthusiast) of Ubuntu. I consider it rather flattering that people should think they are 'tutorials' though, (thanks for the compliment! :D).

These example installs are simply what has worked for me, on my computers here at home. I have tested them as well as I can before publishing them on the website and then rely on feedback from people such as yourself and Ubuntu forum moderators to let me know if everything is okay or not. I monitor the forums every day, as much as I have time for. Thanks for letting me know of your experience with the 5.04 version.
I'm sorry to read it didn't work out for you. There could be any number of reasons for that. Everyone's computer is a little different.
Even if you missed a step or made a mistake it still shouldn't have affected Windows, installing Ubuntu is really safe normally. It sounds to me like maybe your hard-disk might have had a previously corrupted partition table. That can happen and remain like that for a long time without you being aware of it, especially if you have ever used a non-linux partitioner like partition magic or Windows fdisk. It's extremely rare, but it can happen. It can lie dormant for some time and then suddenly become a problem. The chances of having a corrupted partition table are about the same as winning a million dollar lottery, but in reverse, so go buy a lotto ticket! Based on the law of averages, everything must reach an equal balance, so you should expect good luck to equal bad luck. It has happened to me once, (a corrupted partition table, not winning lottery, sadly), but I have done as much formatting, partitioning and re-installing as an ordinary person would in 1 000 000 years. Also, I do weird experiments as well. Corrently I am working on ways to cause my partition table to become corrupted on purpose so I can learn more about that. Maybe I will do so later today.
The example install for Ubuntu + NTFS has not been changed very much at all since 5.04, just the illustrations have been updated to look like 'Breezy', rather than 'Hoary'. The procedure is still exactly the same. If you run into the same problem again (extremely unlikely), I will be interested to learn out more about it. Just make sure you have everything backed up first. Good luck with it, Regards, (Herman) :D

---

