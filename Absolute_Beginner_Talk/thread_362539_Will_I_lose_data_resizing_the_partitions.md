---
title: "Will I lose data resizing the partitions???"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by charlybob on 2007-02-15
I've defragged my harddrive a few times and almost everything is together at the start of the disc. But there's a fragmented part and a contiguous part that are persistent not to move for some reason.

When I resize the windows partition, will this be a problem, or will it not matter?

I won't lose those files if I make it too small will I?

---

### Post by bodhi.zazen on 2007-02-15
No absolute guarantees ... but data loss would be rare.

Of course that is why you should back up any mission critical data before you play with your partitions ;)

---

### Post by charlybob on 2007-02-15
Yeah I've backed up the main stuff, I'd just rather not have to download everything again if I can help it. 

Might as well try it I guess.

---

### Post by maddog39 on 2007-02-15
Let's put it this way. :) When I first started with Ubuntu I was afraid of the same thing. The likelyness of data loss is very rare and in almost 2 years of dual-booting multiple-operating systems (not necessarily windows but sometimes other operating-systems) and haven't yet had a problem. I'd just go for it and not worry about it too much. :D

---

### Post by charlybob on 2007-02-15
It's not the actual booting I thought could get rid of the files. It's shrinking the partition so much that the files are outside of the initial partition size. I didn't know whether it would move them back into the partition or not.

---

### Post by PPAAUULL on 2007-02-15
Just to be safe I would do a defrag on the windows so that it puts the data near the start and it isn't scattered through out the HDD. I would think that if you did not do a defrag it would be more likely that you would lose data.

PS if you make the new partition and something is on it from windows, it is gone cause you need to format it which wipes the data from that partition.

---

### Post by charlybob on 2007-02-15
Ooh, didn't think you'd need to format new partitions.

Well I've defragged 8 times so far and they're not moving.

Are there any free defraggers on the net that are any better than the windows one then?

---

### Post by PPAAUULL on 2007-02-15
Wait a sec what do you mean moving? I would just defrag then back up the data you are scared of losing then go for it. I don't think that you will lose anything and if you do you always have backups.

---

### Post by bodhi.zazen on 2007-02-15
> **charlybob said:**
> Ooh, didn't think you'd need to format new partitions.

Well I've defragged 8 times so far and they're not moving.

Are there any free defraggers on the net that are any better than the windows one then?

No. That's windows for you ;)

---

### Post by charlybob on 2007-02-15
> **PPAAUULL said:**
> Wait a sec what do you mean moving?

I mean from what the windows defragmenter shows, they're staying right in the middle of where the linux partition will be.

---

### Post by PPAAUULL on 2007-02-15
Just go for it. If you have it backed up and you got most of the data out of the way you should be fine.

---

### Post by charlybob on 2007-02-15
Sorry, I know I'm very bad at explaining things, but this should show it better, it's the picture thing windows gives of where the data is, after, about the 10th time defragmenting it >_>

[http://i87.photobucket.com/albums/k135/charlybob/defrag.jpg](http://i87.photobucket.com/albums/k135/charlybob/defrag.jpg)

---

### Post by PPAAUULL on 2007-02-15
It is not movable. I would back it up and go for it. You most likly won't have any problems

---

### Post by charlybob on 2007-02-15
The green's the not movable stuff, but yeah I'm just gonna try it anyway soon as I've finished backing these last things up.

Least if it does mess it up, it's only windows.

---

### Post by charlybob on 2007-02-15
OK I've backed everything up, but I forgot I need to check one thing first.

My keyboards kind of strange. It's a USB one, but the bios doesn't recognise it, and neither does the live cd until it actually starts linux by the timer getting to 30. Should the screen where you choose which system to start recognise the keyboard, because if not, well I'll end up stuck at that screen, and I don't have a windows install CD to put it right with if it won't work.

Sorry for all the questions, but since my computer didn't come with the CD, I just dont want to do anything that could leave me with a computer I cant use when someone on here may know the answer.

---

### Post by dcstar on 2007-02-15
> **charlybob said:**
> 
Are there any free defraggers on the net that are any better than the windows one then?

[http://www.kessels.com/JkDefrag/](http://www.kessels.com/JkDefrag/)

This has better algorithms that the standard windows one.

---

### Post by Virtuous on 2007-02-16
> **charlybob said:**
> I've defragged my harddrive a few times and almost everything is together at the start of the disc. But there's a fragmented part and a contiguous part that are persistent not to move for some reason.

When I resize the windows partition, will this be a problem, or will it not matter?

I won't lose those files if I make it too small will I?

If your partitioning with Windows, I would recommend using Partition Magic or some other partitioning tool than what Microsoft has. If you use Microsoft's partitioning tool, you will definitely be loosing data. Since it would just erase some data rather than move them.

If you used a different partition tool you won't. I actually learned about partitioning in my A+ Technician class just a couple days ago. 

But I still would be cautious when partitioning. Good luck.

---

### Post by indytim on 2007-02-16
re. the keyboard situation.... if you have access to an old ps2 keyboard, plug it in and then boot to the LiveCD.  Should be universally recognized.  Once you've got K-Ubuntu built, you should be able to revert to your default keyboard.

IndyTim

---

