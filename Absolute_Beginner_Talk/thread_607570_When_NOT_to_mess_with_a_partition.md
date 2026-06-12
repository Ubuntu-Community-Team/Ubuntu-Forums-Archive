---
title: "When NOT to mess with a partition?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Unislash on 2007-11-09
Heya,

Question: What are my chances of resizing a partition with about... 40 bad sectors?

I just recently got ubuntu (fiesty) installed on a second partition in my 60gb hard drive. I accidentally left some 5gb of space free and wanted to resize my windows partition to envelope this. I have spent about 8 hours over the last two days reading the net and trying to work through the mess i have in front of me :P.

It turns out that my windows partition has a bad sector (well, i knew this from the moment my original resize didn't work, now didn't i). I did a lot of things to try and fix this, including following the directions that gparted says (run chkdsk with /f and /r parameters). There was still a bad sector (no surprise there) after doing not only that, but everything i could find to try and fix it (which was pretty much running chkdsk with different parameters).

Anyhoo, i decided to try to back up the partition before i went on with the resize. Problem is... i'm an inexperienced linux user and i didn't know how to do, well, a lot of stuff. I eventually got over that hurdle by using apt-get install partimage and then unsuccessfully running that and learning later that i could just go into the terminal and use nftsclone [options] [values], which i eventually did. It worked like a charm compared to everything else... but it also told me the whole story--that i had upwards of 40 bad sectors--which is why i ask the original question. 

So, what are my chances? Nil? (comments are always welcomed)

Cheers,
Unislash

PS: If anyone wants more information on what i did to "successfully" clone my partition (such as a fellow newbie), just say so :)

---

### Post by mcduck on 2007-11-09
Might work. But it's not worth it as the disk is dying anyway.

Bad sectors are the sign that tells you it's time to go and buy a new hard disk, back up all your data as soon as possible and never to trust that old disk again as anything you store on it might get corrupted..
 
I wouldn't bother resizing any partition on that disk any more. Just get a new one and install Ubuntu on that.

After you got new disk and have all your data safely there, you can of course use the old disk for testing and playing around etc, as long as you don't need to rely on that old disk not failing.

---

### Post by Unislash on 2007-11-09
Thanks for the reply :)

Now, this disk is only a year old, so i'm not sure if that's the problem (could be--i dunno if a year is a life's worth for a HDD). Hmmm... well, here's the history of my disk:

First off, i had a toshiba laptop back about 3 years ago. Worked fine and everything except that it overheated constantly. Figures. So, after getting fed up with that problem, i decided to get a new laptop (2 years after i'd been using the toshiba). I ended up getting a Eurocom laptop (they are a desktop replacement company, so i can replace anything in my laptop without having to gut the whole thing like you would with a common laptop). During this transition, i made the mistake of cloning my toshiba hard drive to my eurocom laptop--i had no idea what kind of problems that would give me for nearly a year...

After that year of dealing with a laptop that can't edit power options amongst other things, i decided that i should wipe the hard drive after moving my important files to an external hard drive. I did this about a month ago. I then installed windows, followed by ubuntu fiesty, and you know that whole partition story.

So, my thinking is that possibly the hard drive retained the bad sectors from the old disk with the overheating computer. Is that possible?

Anyway, i made a backup as best i could. It couldn't read 40 sectors, so that much information i don't have. How could i check which files those sectors entail? Is that possible too?

Cheers,
Unislash

---

### Post by skymera on 2007-11-09
Spinrite done a fantatic job at recovering my laptops hard disk!

it was very badly damanged, and now works like new :)

once again not free, but heh, think out of the box. :wink:

---

### Post by LowSky on 2007-11-09
A year isn't very long, most hard drive companies say a heard drive should get about 3-5 years, and I own a few that are going well beyond that. But if you treat you computer like a a ragdoll, and dont shutdown correctly, and use it on heat absorbing surfaces, the computer isn't going to last that long.

on a side note...why would you clone a toshiba's hard drive and put it into another brand of laptop? I would understand if it was the same laptop but it is not.

Personally I would reformat the disc entirely and then check it for integrity, if it still shows the bad sectors go out and buy a new drive

---

### Post by az on 2007-11-09
> **Unislash said:**
> 

So, my thinking is that possibly the hard drive retained the bad sectors from the old disk with the overheating computer. Is that possible?

Anyway, i made a backup as best i could. It couldn't read 40 sectors, so that much information i don't have. How could i check which files those sectors entail? Is that possible too?

Cheers,
Unislash

"bad sectors" are bad blocks.  They are 512 bytes each.  They are on the disk, not the filesystem.  You do not transfer bad blocks from one disk to another - you just don't get the data off.

Anyway, it's irrelevant.  You tried to move the data around so I don't know if the integrity of the filesystem is still intact.

The best thing to do when faced with a failing hard drive is make an image of is as best as possible to save the data.  Using tools like GNU-ddrescue, you can re-read the bad blocks until you get a good read.  GNU-ddrescue will also produce an image where the unreadable areas are zeroed (and not just missing -  which can complicate things when you want to reconstruct the filesystem).

That being said, you say you have a copy of the filsystem using ntfsclone.  Just mount it and see:

mount -t ntfs -o loop ntfsclone.img /mnt/ntfsclone
 
Browse /mnt/ntfsclone and see if the filesystem is intact.  If it is working fine, try writing the image back to another hard drive and boot it.

Do not use the same drive.  It is not reliable and never will be.
> **skymera said:**
> Spinrite done a fantatic job at recovering my laptops hard disk!

it was very badly damanged, and now works like new :)

once again not free, but heh, think out of the box. :wink:

Spinrite is a toy.  I'm happy it worked for you, but I would also caution you to backup all you data and get a new drive.  Your drive failed once and it will fail again.  Spinrite doesn't protect you from that.

I do not recommend anyone play around with Spinrite until you have backed up (or imaged) your data.  Spinrite can increase your data loss by attempting to write to a failing drive.

---

