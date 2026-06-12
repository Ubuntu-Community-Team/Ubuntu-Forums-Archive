---
title: "Resize IDE1... for 2 hours now, normal?"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by evny on 2006-11-03
Hello,  I am a newbie, not only with Ubuntu but with Windows too.  I recently got an HP dv5004cl laptop, which has Turion 64, 1 mb RAM, 80 gig HD.  I need to use Windows even though I don't like it, so I want to do a dual boot.  I burned the live Edgy CD and tried it out.  It worked, so tonight I decided to install it.

When I got to Prepare Disk Space, I chose "Resize IDE1 master..." and left it at the default setting of 50%.  There is hardly anything on this computer and I ran the defrag thing 3 times before installing.  

Anyway, I have been looking at the same screen for 2 hours now.  The little circle is spinning but I can't tell if anything is happening.  How long does it typically take for the Windows partition to be resized?  I wonder if I should leave it on all night, or stop and try again.

Edited to say that I gave up on it, took the CD out and restarted a couple of times, (because Windows was acting weird) and it seems that no new partition was created. 

I wonder what it was doing all that time?

---

### Post by K.Mandla on 2006-11-03
Hard to say. I know resizing or moving a partition can take a *very* long time, but if it's not moving at all, it's not moving at all. ;) It probably got confused and sat still until you stopped it.

Try the [GPartEd live CD]("http://gparted.sourceforge.net/livecd.php"). It's the same GPartEd environment you might have seen in Ubuntu, but it boots to a live environment, which means it has much better control over the drives and the partitions.

Then try installing with the alternate CD, which might be more practical for building a dual boot system. It's not required, but you might find it to be more reliable.

---

### Post by fatneck on 2006-11-03
I failed with the Ubuntu install CD to resize the Windows partition several times. I booted back into Windows and used a Windows tool to reduce the partition size and just left an unused/unformatted section of hard drive.

Then when I next ran the Ubuntu CD it worked using the unused/unformatted section I'd just created.

---

### Post by evny on 2006-11-03
Thanks for the quick replies!  I will try again, using something else to resize the partition.

---

### Post by justifier on 2006-11-03
Did u choose 50% or 50 gigs? easy mistake to make when typeing how much space you want to use, check this!!

No im not saying it as if u may be an idiot but its and easy mistake to make

---

### Post by Bartender on 2006-11-03
I've done several practice installs on my old 400MHz PC.  resizing a partition (120GB hard drive) never took more than a few minutes.

---

### Post by PriceChild on 2006-11-03
A good tip is to defragment the windows drive before attempting any operations on it :)

---

### Post by evny on 2006-11-03
Thanks for all your help.  I ran the defragmenter several times and it seems like there's plenty of room on the right side of the graph.  Like I said, I hardly have anything on the computer. So I set the slider to 50%, and the circle just turns and turns.  I saw on another thread that it might be a good idea to try and run gparted from the system/administration menu while in the live CD.  I tried that and I got "An error occurred while applying the operations..." When I clicked on the details it said, among other things, Filesystem check failed!  Totally 1 cluster accounting mismatches..." and so on.  It says I should run chkdsk /f and then reboot twice.

Up until I got this computer, I had only used Macintosh.  I guess I need to figure out how to run this chkdsk /f thing.

---

### Post by PriceChild on 2006-11-03
I would run the checkdisk utility included with windows.

Open up My Computer, right click the hard drive & click properties.

Click the "Tools" tab, then "Check disc now". Choose all the options then press ok and agree to reboot.

These instructions may not be totally accurate... haven't used xp in a while.

Pricey

---

### Post by evny on 2006-11-07
Well, I finally figured it out. This is so stupid. Because I did not know how to get the laptop to boot from the CD, (the documentation doesn't say how,) I went online to look.  On some site it said to boot an HP laptop with a CD, hold down the power button for 5 seconds, then turn it back on again.  Since it wasn't turned off properly, the partition couldn't be resized.  Do'h!

So I was able to install from the Live CD and I'm posting from Ubuntu now. My only problem now is the Broadcom wireless card.  I tried the How to, but I have kernel 2.6.17-10 not -7, so it doesn't work.  I'm sure there's a way, but meanwhile, I'm just going to get used to Ubuntu.

Thanks again for the help.

---

