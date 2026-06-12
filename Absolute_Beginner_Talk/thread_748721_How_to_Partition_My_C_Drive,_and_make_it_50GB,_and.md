---
title: "How to Partition My C: Drive, and make it 50GB, and let 50GB free?"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by R6V2 on 2008-04-07
I have a gParted, but no clue how to use it. If I can get a partition editor, to change the size of my C: drive, so that I have room to dual-boot with linux. Please help me! If this is done, I can get  Linux Installed! Yay! Yay!

---

### Post by Bruce M. on 2008-04-07
> **R6V2 said:**
> I have a gParted, but no clue how to use it. If I can get a partition editor, to change the size of my C: drive, so that I have room to dual-boot with linux. Please help me! If this is done, I can get  Linux Installed! Yay! Yay!

Depending on which CD you have read one of these:

Using Ubuntu Live CD:  [Installing a Dual-Boot with Windows and Ubuntu]("http://www.psychocats.net/ubuntu/installing")

Using Ubuntu Alt CD: [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by JoshuaRL on 2008-04-07
I would suggest you use the option Guided: Partition Drive and use the slider to use 50% of the drive.

---

### Post by R6V2 on 2008-04-07
Take a look at the screenshot below, im tring to use the 8.4BETA. I don't have either of the options you told me about.

---

### Post by JoshuaRL on 2008-04-07
Sorry.

Guided: Use the largest continous free space.  Then use the slider to partition your drive.

---

### Post by R6V2 on 2008-04-07
There is no slider...

Even if I put it on that setting, and press forward, I get this:

Failed To Partition The Selected Disk
This probably happened because the selected disk or free space is too small to be automatically partitioned.

---

### Post by JoshuaRL on 2008-04-07
Honestly it's been a little while since I installed, and I haven't tried Hardy yet.

[Does this help you any?](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by R6V2 on 2008-04-07
No, I've already looked at all these tutorials, and help, and they don't help. And no one seems to be able to find out what my problem is, and why I cant install Linux.

*Sorry* If im a little cranky, or attacking you, i've been tring to install Linux for 4 days now...

---

### Post by JoshuaRL on 2008-04-07
Don't commit to anything, but search around in that menu a bit for a slider.  That's what you're looking for.

---

### Post by R6V2 on 2008-04-07
There isn't a slider there. I have a 100GB Harddisk, with 70GB free, and the only thing it gives me is in the picture above...

I apperciate your help, but i've gotten no-where today. I feel like cring.

---

### Post by Vadi on 2008-04-07
I think you should get the 7.10 install CD. 8.04 is still in beta - and that's a *real* beta, not like a Google beta. Unexperienced / new people shouldn't be using it!

So get 7.10 off ubuntu.com, and use that. Then you'll definitely get a slider.

---

### Post by R6V2 on 2008-04-07
Alright, well I'll put in the .10, I have downloaded and tried so far:

.04 .06 .10 8.04(BETA)

---

### Post by JoshuaRL on 2008-04-07
That was going to be my next suggestion Vadi, good one.

All I can figure out is that it's Hardy and still Beta.  But I know for a fact that Gutsy will have the slider.

---

### Post by R6V2 on 2008-04-07
> **JoshuaRL said:**
> That was going to be my next suggestion Vadi, good one.

All I can figure out is that it's Hardy and still Beta.  But I know for a fact that Gutsy will have the slider.
What if I said it didn't?

---

### Post by maniac_X on 2008-04-07
If you are able to, get the Parted Magic Live CD .iso image and burn it and boot with that.
Available here: [http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

Before booting with that, go into Windows and defrag your harddrive. This will help prevent errors when the Windows partition gets resized.

Now boot with the Part Magic Live CD and choose the partitioner. After you resize the drive, you will have a free space that is unformatted. That is the area the Ubuntu Live CD will use for installation if you choose the "Guided - use largest continuos free space" (as shown on your screen shot) selection during the instal phase.

---

### Post by R6V2 on 2008-04-07
> **maniac_X said:**
> If you are able to, get the Parted Magic Live CD .iso image and burn it and boot with that.
Available here: [http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)

Before booting with that, go into Windows and defrag your harddrive. This will help prevent errors when the Windows partition gets resized.

Now boot with the Part Magic Live CD and choose the partitioner. After you resize the drive, you will have a free space that is unformatted. That is the area the Ubuntu Live CD will use for installation if you choose the "Guided - use largest continuos free space" (as shown on your screen shot) selection during the instal phase.
Well, once it loaded, I choose the partition editor, and then highlighted my drive, and then clicked: Resize/move, and it wouldn't let me lower the size of it. !!?!?!?!?!? WHY!??!??

---

### Post by louieb on 2008-04-07
May be something GParted sees about your widows partition. Its pretty picky and won't resize it if everything doesn't look just right.  In windows defrag the drive and run chkdsk.  May even have to turn off virtual memory in windows. (Turn virtual memory back on after its been resized). And shutdown windows. Do not suspend or hibernate or unplug it. 

Just in case your not sure about how GParted/partedmagic works heres a video. [Linux.com :: Dual-booting Windows and Linux the easy way (Linux.com videos)]("http://www.linux.com/feature/114157")

---

### Post by R6V2 on 2008-04-07
Well, my dad (Great with Comps) Said that because it couldn't edit it, theres a problem with windows, im going to wipe out windows, install XP on only half my disk, then install linux!

---

### Post by lackofcreativity on 2008-04-07
I've been able to do this by using the Manual option, then manually reducing the size of the Windows drive and making a swap partition then another partition to install on. I've never had any good experiences dual-booting with XP anyway.

---

### Post by maniac_X on 2008-04-07
> **R6V2 said:**
> Well, once it loaded, I choose the partition editor, and then highlighted my drive, and then clicked: Resize/move, and it wouldn't let me lower the size of it. !!?!?!?!?!? WHY!??!??

That is definately odd and your dad may be right. I never had issues like yours when using the [Part Magic Live CD]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads"). I also sometimes use the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") as well. Never had issues with either one with regard to resizing a partition.

Good luck on your reinstalls. That's always fun (not!). It's not so bad with linux reinstalls though, it's usually much quicker.

---

### Post by R6V2 on 2008-04-07
> **maniac_X said:**
> That is definately odd and your dad may be right. I never had issues like yours when using the [Part Magic Live CD]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads"). I also sometimes use the [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") as well. Never had issues with either one with regard to resizing a partition.

Good luck on your reinstalls. That's always fun (not!). It's not so bad with linux reinstalls though, it's usually much quicker.
Yeah, I guess it's odd, but I like watching the Blue screen anyway...lol.

That's how bad I want linux, enough to format my drive :)

---

### Post by JoshuaRL on 2008-04-07
> **R6V2 said:**
> Yeah, I guess it's odd, but I like watching the Blue screen anyway...lol.

That's how bad I want linux, enough to format my drive :)

Dude, welcome to the fold.  Sorry we couldn't help you fix anything without a full wipe and reinstall.  Oh well, all is fair and good if you learned something and gained some confidence.

Welcome to Ubuntu!

---

