---
title: "A few questions about upgrading a Macbook Pro hard drive"
date: 2009-06-20
forum: Apple Hardware Users
---

### Post by aysiu on 2009-06-20
This isn't strictly a Ubuntu question, but I respect the knowledge of the Ubuntu community, so I'm hoping this is okay. If another staff member decides it's not okay, I'm cool with that and can ask on a Mac forum.

So my wife is thinking about upgrading the hard drive in her Macbook Pro from 120 GB to 500 GB. If I can take care of the software part (cloning her current installation), she's willing to take care of the surgery (her fine motor skills are far better than mine).

Two questions:

1. If I dd her 120 GB drive and then dd it back, how can I enlarge the partition to fill the entire new drive and not just the first 120 GB of it? After all, for functionality's sake, I'd be doing a *sudo dd if=/dev/sda* and not a *sudo dd if=/dev/sda1*.

Any tips on that?

Would CloneZilla be a better tool than dd for this?

2. As far as I can tell, getting pretty much any SATA 2.5" hard drive should be good for the Macbook Pro (it's one of the older models from very early 2008; it is not a unibody). Is that correct? What's the best way to find out exactly what type of hard drive she currently has (without opening it up)?

3. Given the questions I've just asked, are we crazy to undertake this upgrade?

Any advice would be greatly appreciated. Thanks in advance.

---

### Post by pxwpxw on 2009-06-20
If you also invest in an external drive, then Apple Time Machine, Migration is a possibility (MacOSX Leopard) avoiding the dd problem.

[http://www.apple.com/macosx/what-is-macosx/time-machine.html](http://www.apple.com/macosx/what-is-macosx/time-machine.html)

Cant say I've tried it though.

---

### Post by aysiu on 2009-06-20
Time Machine sounds good in theory, but we haven't had much luck with it. It just hangs when we try to do a backup.

---

### Post by buttertoad on 2009-06-21
When I upgraded the hard drive in my MBP I used Carbon Copy Cloner [http://www.bombich.com/software/ccc.html]("http://www.bombich.com/software/ccc.html")

It worked great. I was able to keep my original installation and didn't have any issues. Time Machine would do something similar but it isn't a block to block copy. 

Good luck.

---

### Post by Richardcavell on 2009-06-21
1.  I don't like the dd idea, since you don't want the destination partition to be identical.  The directory structures and so on are not going to be identical.  What you want is for the files to be identical.  So use a program like Carbon Copy Cloner to make a file-for-file clone of your internal hard disk to an external hard disk, then from the external one back to your internal one after upgrading.  It works perfectly for me.  The only down side is that it might be rather slow to back up a hundred gigs of data over a USB connection to an external hard disk.

2.  MacBooks can generally only take a 9.5mm high drive.  Some laptop drives (ie 2.5 inch high drives) go up to 11 or 12.5 mm because the manufacturer tries to sneak an extra platter or two in.  I can't vouch for your specific model of MacBook Pro, but aim for a 9.5mm drive to be safe.

3.  To find out what sort of drive she has, use OS X.  Go to Apple logo -> About this Mac -> More Info.  Then select "Serial-ATA" on the left hand side.  

4.  As to what sort of hard disk to buy, it seems to me that going from 5400 rpm to 7200 rpm makes a big difference to the end-user's perceived responsiveness of the computer.  Tom's Hardware seems to like the Seagate Barracuda models.  You can't go faster than 7200 rpm in a laptop, because of vertical height, heat and angular momentum.

Let us know how you go.

Richard

---

### Post by aysiu on 2009-06-21
> **Richardcavell said:**
> 1.  I don't like the dd idea, since you don't want the destination partition to be identical.  The directory structures and so on are not going to be identical. Why won't the directory structures be identical? > What you want is for the files to be identical.  So use a program like Carbon Copy Cloner to make a file-for-file clone of your internal hard disk to an external hard disk, then from the external one back to your internal one after upgrading.  It works perfectly for me.  The only down side is that it might be rather slow to back up a hundred gigs of data over a USB connection to an external hard disk. But if you use something like Carbon Copy Cloner, do you have to reinstall OS X *before* you copy the files back?

What I like about dd is that I wouldn't have to copy the files back. I could just reimage the drive and theoretically it should work exactly as the old drive did. The only down side would be that the drive would be artificially limited to 120 GB instead of 500 GB, so I'd have to find a way to extend that partition out.

> 2.  MacBooks can generally only take a 9.5mm high drive.  Some laptop drives (ie 2.5 inch high drives) go up to 11 or 12.5 mm because the manufacturer tries to sneak an extra platter or two in.  I can't vouch for your specific model of MacBook Pro, but aim for a 9.5mm drive to be safe. Thanks for the tip. That's good to know.

> 3.  To find out what sort of drive she has, use OS X.  Go to Apple logo -> About this Mac -> More Info.  Then select "Serial-ATA" on the left hand side.   I did that and got the model of the drive but not much other detailed info on the specs (how fast it is, what size it is... I mean, you told me the size already, but the More Info did not).

> 4.  As to what sort of hard disk to buy, it seems to me that going from 5400 rpm to 7200 rpm makes a big difference to the end-user's perceived responsiveness of the computer.  Tom's Hardware seems to like the Seagate Barracuda models.  You can't go faster than 7200 rpm in a laptop, because of vertical height, heat and angular momentum. Are there downsides to 7200 rpm, though? Will it overheat? Does it significantly impact the battery life?

Thanks for all your help so far!

---

### Post by buttertoad on 2009-06-21
> But if you use something like Carbon Copy Cloner, do you have to reinstall OS X before you copy the files back?

What I like about dd is that I wouldn't have to copy the files back. I could just reimage the drive and theoretically it should work exactly as the old drive did. The only down side would be that the drive would be artificially limited to 120 GB instead of 500 GB, so I'd have to find a way to extend that partition out.

What is so useful about Carbon Copy Cloner (CCC) is that you won't need to reinstall. CCC is a low level copy like dd but without the size limitation. For example, I bought a new 500GB hard drive and and external enclosure. I installed the 500GB drive in the external enclosure and used CCC to clone my internal drive to the external one. I removed the internal drive from the MBP and installed it in the external enclosure while I took the 500GB drive and installed it in the MBP. I was able to then boot the computer from the 500GB drive and everything looked exactly the same except it was on a 500GB drive. Now I use the old drive in the external enclosure for backups and whatnot.


> Are there downsides to 7200 rpm, though? Will it overheat? Does it significantly impact the battery life?

Unless you are using applications that require a lot of rendering time or other hard drive intensive applications it's doubtful you would see a huge difference. a 7200rpm drive will run a little warmer and a little noisier then a slower one. Some people have a problem with this others don't.

---

### Post by Richardcavell on 2009-06-21
> Why won't the directory structures be identical?

I doubt that they will be identical in every way for two drives of different sizes.  Also if your drives are not identical and you make a block-for-block transfer, it may be suboptimal to doing a file-for-file transfer.

> But if you use something like Carbon Copy Cloner, do you have to reinstall OS X *before* you copy the files back?

No.  Cloning an OS X installation is tantamount to installing OS X.

> I did that and got the model of the drive but not much other detailed info on the specs (how fast it is, what size it is... I mean, you told me the size already, but the More Info did not).

You can Google for that info easily.  It's unlikely that More Info could tell you the spindle speed.  You could measure certain elements of your hard drive's capabilities, but it might be just as well to look it all up on tomshardware.com or anandtech.com.

>Are there downsides to 7200 rpm, though? Will it overheat? Does it significantly impact the battery life?

Not really.  From what I've read of other people's experiences, heat and power usage are not that much of an issue with 7200 rpm drives.  If you go higher than that, though, then they will become significant issues.  Modern MacBook Pros optionally come with 7200 rpm drives.

Richard

---

### Post by aysiu on 2009-06-21
Thank you to all for the information. It is really helpful.

---

