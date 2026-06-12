---
title: "Partition EXT HD for so I can install linux.."
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by makko on 2007-02-27
Hi,
I Have an external WD 320GB hard drive that I would like to partition off say 25GB for using ubuntu..
How would I go about doing this without losing the data already on it? Also, is there any thing I should be aware of when doing this ?

Thanks..

---

### Post by annda on 2007-02-27
the usual: back up you important data (nothing has ever happened to me in 20 or so installs but who knows?)

otherwise, go ahead, partition using the live/install CD (defragment first and choose "use free space" on install) and have fun!

---

### Post by angryfirelord on 2007-02-27
When you run the Ubuntu installer, a partitioner will appear. Simply resize it to the amount that you want.

The only thing you should be aware of is that if the hard drive is pretty filled up, you may lose some data. The partitioner will go from the outside-in of your partitioner. If you haven't installed too many programs & have about 1/2 free space, you should be alright.

Please note that you must have a small (no bigger than 512MB) swap partition as well.

---

### Post by makko on 2007-02-27
Ok, I have 220GB free...so the the ubuntu partitioner will not effect the files on it? Will it sort out the swap partition also? And it won't effect the current bios setting on my laptop or my windows installation? Just checking..

---

### Post by angryfirelord on 2007-02-27
220GB free? You should be fine (I've done it before with no issues), but it doesn't hurt to back up your important files. You will have to add two partitions, one for the system & one for the swap.

Here's what I'd do. Resize Windows(right click on it click resize, and lower the amount listed), add the first partition and make it 512MB (you can type that in). You'll see a list of filesystems, but select *linux-swap*. Then, add another partition and use the remaining free space. For now, use the ext3 filesystem.

Your BIOS setting will say the same, nor should you have to make any changes to it.

Happy Ubuntu-ing!

---

### Post by makko on 2007-02-28
I'm in the middle of it now and i'm sorry to say i'm having hassle at every possible corner..I have just tried google and now I 'm reall frustrated..
I need a good guide on partitioning the ext usn 320BG HD and possibly a guide on installing it...

in the install window in the partition editor I add two partitions, 1 swap and he other ext 3 and allocate the proper amount of space but afterwards they both come up as being 0kb what to do??

---

### Post by makko on 2007-02-28
OK!!! Now I have lost all my files on my hard drive!! The drive does not mount in windows XP anymore!! How do I get this back?? I need some of the files on that disk...GOD I hate Ubuntu at the moment...

---

### Post by angryfirelord on 2007-03-03
I'm sort of at a loss. All you need to do is create one swap and one ext3 mounted as /...

I know this sounds retarded, but make sure you have specified an amount of how much space you need. 

Better yet, take a snapshot of each screen while you are setting it up so I can see what you are doing (if you're using the desktop version). I believe it' under Applications-->Accessories-->Take Screenshot.

---

