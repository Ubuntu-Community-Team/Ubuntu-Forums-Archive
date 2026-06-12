---
title: "Triple boot using images alreeady created"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-06-12
OK this may seem like a totally whack thing to do.  I use Acronis 10 for backups.  Not being super kung-fu like some of you here I want to try:

restoring my original laptop XP partition
Restoring my newer Vista Partition
Restore my Ubuntu partitions

...and make them all work.

I can restore Vista and shrink the partition to something reasonable like 30 gig and have the rest blank.
I can then restore the XP partition and shrink it with a utility down to like 30gig and tag it active, leaving 80gig for Ubuntu.

Now restoring Ubuntu and the swap partitions.  This is where I'm a little shakey.  What would be the best way to accomplish this?  Install a clean copy of Ubuntu (let grub see the Vista and XP installs so I can select whatever I want) and do some sort of restore?  Restore the images and then do some sort of repair -is there even such a thing?  I have my Ubuntu install setup so sweet I hate to start from scratch, I'd really like to save it if at all possible.

I could really use some sort of advice on the best way to attack this situation.  I am forced to support XP/Vista/OSx/Ubuntu.  I would love to have 3 OS' on my laptop that I can switch to to test things out if at all possible.

---

### Post by starcraft.man on 2007-06-12
Hi. I still use Acronis, its a good product. Your plan seems fine for the first two steps, you can shrink both (Vista may give a bit of trouble, be careful) easily and they should be fine.

Now when it comes to Ubuntu, you can actually back up the MBR (where GRUB installs with Acronis). I have done it numerous times and it always restores fine. That said, if you didn't expressly back it up then you can't just restore it to the MBR and it will handle the booting.

That said, since I assume you didn't do that here are your two options for the last step:

Better option:

1) Restore the swap and root partition to the drive.
2) Get live CD and boot into it.
3) [Restore GRUB by following this guide via online or printed.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub")
4) If all OSes are properly detected reboot and test all 3 to ensure booting is operational.
4b) If one fails, manual editing is likely required.
[Consult this guide for understanding GRUB and how to edit.]("http://users.bigpond.net.au/hermanzone/p15.htm")
Search the forums for any difficulty that may ensue (I'm not sure how easy Vista works with GRUB).

Easier: 
1) Reinstall Feisty from the live CD and install GRUB to the MBR detecting all 3.
2) Restore the Image of the root partition and swap over what you installed.

I know the second one looks easier, but I really really suggest the first. It may be a bit daunting, but I believe it is least likely to cause problems. 

Good luck, if it doesn't work post back and I should respond some time...

When you get it all working again. Reimage the whole thing INCLUDING the MBR. Then you'll never have trouble again. Also toss the old back ups out of course.

One more thing, if you want to access all your OS' fast for consulting, try a VM like [Virtual Box]("http://www.virtualbox.org/") and install it into Ubuntu partition. Then you can install XP and Vista in it (you should have at least 512 for both, 1 GB is best for Vista or more). It is a good option if you want to give it a try. Will mean you don't have to boot into the OS you want to try, you'll have access to all 3 all the time.

---

### Post by Atomic Dog on 2007-06-12
Thanks so much for the expertise advice.  I will do the first option. 

I do not have a legit copy of Vista to install as a VM.  VMware great with XP and so does VirtualBox as best I can tell.

I want the triple boot to not only mess with Vista and XP, but also reap the benefits of the goodies my laptop has that Ubuntu can't deal with like the cardreader and webcam.  Believe it or not, XP has way better driver support than Vista for the webcam.

Thanks again.  I'm starting a fresh backup tonight to my external drive before I attempt this!

---

### Post by starcraft.man on 2007-06-12
> **Atomic Dog said:**
> Thanks so much for the expertise advice.  I will do the first option. 

I do not have a legit copy of Vista to install as a VM.  VMware great with XP and so does VirtualBox as best I can tell.

I want the triple boot to not only mess with Vista and XP, but also reap the benefits of the goodies my laptop has that Ubuntu can't deal with like the cardreader and webcam.  Believe it or not, XP has way better driver support than Vista for the webcam.

Thanks again.  I'm starting a fresh backup tonight to my external drive before I attempt this!

I'm not surprised XP better supports your hardware, Vista broke lots of things and some companies just don't want to code new drivers for old products when they can just get you to buy their newest stock and spend more money. Anyway, you should look around the forum. I have heard of quite a few people getting their webcams working, less to a degree their card readers... those just aren't that popular I don't think.

Anyway, your welcome for the advice. Oh and good idea backing up, something can and often does go wrong, Murphy's law makes it so. Darn him for ever coming up with it :p.

Good Luck.

---

### Post by Atomic Dog on 2007-06-13
> **starcraft.man said:**
> I'm not surprised XP better supports your hardware, Vista broke lots of things and some companies just don't want to code new drivers for old products when they can just get you to buy their newest stock and spend more money. Anyway, you should look around the forum. I have heard of quite a few people getting their webcams working, less to a degree their card readers... those just aren't that popular I don't think.

Anyway, your welcome for the advice. Oh and good idea backing up, something can and often does go wrong, Murphy's law makes it so. Darn him for ever coming up with it :p.

Good Luck.

Tell me about it.  A co-worker once replaced a drive in an array in our terminal server.  Despite being warned to back it up first he went ahead and replaced it (no the machine was never backed up as my boss likes to live dangerously).  99.99% of the time it would go smoothly right?  *boom* wiped out the array...and no solid backup.  I spend an entire day building a new one and loading back all the apps and data from backups.  That's why I swear by Acronis True image.  I never make a big change without a backup.

Realize that 98% of the time I use Ubuntu.  I really like it and cut my Linux teeth on it.  People refer to me as the linux expert at work.  Yikes!  I'm far from an expert.   Vista I'll hardly ever use, and XP is an old friend that runs certain apps & hardware I need to use on occasion.

---

### Post by Atomic Dog on 2007-06-15
Starcraft man, I have made backups in duplicate and am confortable that if something blows up I can recover.

Restoring in Acronis gives me the option to restore "MBR and track 0"  Do I want to restore this?  Or should I just restore the partitions and then boot from a feisty CD and follow the grub instructions?  Obviously some of the partitions are not in the same position so I'm not sure if restoring MBR & track0 is worthwhile.

Hope to hear your opinion.  I'm sitting here reasy to pull the trigger!

---

### Post by starcraft.man on 2007-06-15
> **Atomic Dog said:**
> Starcraft man, I have made backups in duplicate and am confortable that if something blows up I can recover.

Restoring in Acronis gives me the option to restore "MBR and track 0"  Do I want to restore this?  Or should I just restore the partitions and then boot from a feisty CD and follow the grub instructions?  Obviously some of the partitions are not in the same position so I'm not sure if restoring MBR & track0 is worthwhile.

Hope to hear your opinion.  I'm sitting here reasy to pull the trigger!

Uh, no. Don't restore the MBR taken from the XP or Vista back up. I wouldn't even (if its available) for the Ubuntu. If you've made modifications then its not a good idea, it is a bit for bit copy you have to remember so any changes to what it expects will make problems. So yes, restore the partitions minus the MBR option and then reinstall GRUB from the instructions.

In future after you restore all 3 and image the whole drive (this will include the MBR and track0), you can restore the MBR and track0, it will be exactly the same then and function perfectly.

Best of luck with that, it should work fine :).

edit: yay, 1700 posts, I'm such a spammer :p.

---

### Post by Atomic Dog on 2007-06-15
Glad you replied.  I'm starting the long 8 hour restore process (shrinking things to all fit too).  So I used my HD with the Vista install already shrunk down, then chose to restore the XP partition (shrunk it down) and ext3 partition (also shrunk slightly).  I should end up with 45GB, 45GB and 61GB for Ubuntu with the unchanged 3.2GB swap.

The Ext3 and XP partition are tagged as Primary partitions (vista was already primary, & active), swap as logical.

Guess I won't know till tomorrow if it all worked :o  I hate leaving my laptop at work, but no way in heck am I interrupting this!

---

### Post by starcraft.man on 2007-06-15
Uh, just a note. How much physical ram do you have? The ceiling limit for total ram/swap (number combined) in Ubuntu (32 bit) is 4 GB (from everything I've read), thus if you have more than a GB of RAM it may be going to waste (undetected or simply unused). I'd recommend using less swap than totals up to 4 GB, and I am pretty sure nothing you do can max out 3 GB of swap, I have 2 on my 1 GB ram machine and I never break 800MB of swap used when running a whole VM and apps.

Just a thought. I say it because its important to minimize swap use, RAM is much faster than reading and writing to swap (your HDD). After you get everything settled I'd probably shrink the swap file down...

Oh and as for what your doing, sounds fine to me. It should work, if theres any problem with GRUB, we will do a bit of manually editing to iron out bugs.

---

### Post by Atomic Dog on 2007-06-15
I am running 2 gig of ram.  The original install chose 3.2 gig and that seemed OK to me.  But now that you mention it I have heard others say set a max of 2 gig for a swap, and even 2 gig is a lot. Maybe I'll cut it down later.

7 hours to go... man does that take some time. (USB drive holds the backups).

---

### Post by starcraft.man on 2007-06-15
> **Atomic Dog said:**
> I am running 2 gig of ram.  The original install chose 3.2 gig and that seemed OK to me.  But now that you mention it I have heard others say set a max of 2 gig for a swap, and even 2 gig is a lot. Maybe I'll cut it down later.

7 hours to go... man does that take some time. (USB drive holds the backups).

Ok, if you have 2 GB of ram, I definitely recommend you shrink it down to 1 GB. More than that of swap is wasted, 2 GB of ram may even be more than enough for running it without any swap at all.

So my recommendation: 2 GB Ram, 1 GB swap, and then you can add a GB later of ram and still be under Ubuntu's max. You may see a slight performance boost after doing this, using too much swap can be detrimental since HDD write and read is tremendously slower than RAM.

---

### Post by Atomic Dog on 2007-06-16
Thanks starcraft_man!  All went well, and all works.  Now I gotta backup this new setup.

---

