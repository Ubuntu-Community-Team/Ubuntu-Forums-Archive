---
title: "What format to make backup partition?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by Carbonfish on 2006-08-16
Hi Everybody,

I have a 250 GB Lacie external HDD that I use to backup my iBook and for other storage, and I would like to use a 110 GB "free space" partition on that external drive to also backup Ubuntu from my ThinkPad. What I can't seem to find (although it is probably right in front of me) is, what format do I make the partition where Ubuntu will live. The format of the partition for the bootable clone of my Mac is HFS+, but I am unclear on what format Linux likes/needs.

Thanks for putting up with my ignorance. I am getting better though!

EDIT: Oh yeah! I have been here:  [http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

and read carefully, and while I am sure that partimage will properly do it's thing, it still doesn't tell me what format the partition will wind up being as far as I can see. Am I just overlooking it?

KC

---

### Post by em3raldxiii on 2006-08-16
Typically, Ubuntu uses ext3, as far as I know.  Linux also likes to have a SWAP partition, though I am unsure what the optimum size would be.  I've read in a few places that either the same size as your RAM or double the size of your RAM for the Swap partition.

As far as I know, though, Ubuntu can use ext2 or ReiserFS ... though I am sure others will be able to clarify better than me.  I am fairly certain that ext3 would be the right way to go.

On the other hand, I also think you can go FAT32, though I doubt that would be optimal because it doesn't like large files (over 4GB), and large partitions are a bit wonky.

---

### Post by goatflyer on 2006-08-16
Linux "likes" ext3 best, but you don't need to manually partition the HD before install, the Ubuntu installer will offer to let you partition manually during the install.  At that point, you will want to make more than just 1 partition.

You should definitely make a swap partition >= 2*physical ram size of your machine.  You might want to make a /home partition to make backing up your personal data easier.  The installer will want to make a /root partition to place the rest of the system.

---

### Post by orb9220 on 2006-08-16
If you are going to use rsync to backup a linux partition it won't do it to fat32. But tar command does I believe.

You need to ask yourself one question. Will I be storing any data that I  want xp or apple to be able to access? Pictures,Music,etc... then you will need to use a file sytem that can be read and written to.

For my dual boot ubuntu-XP I have a 112GB fat32 partition for pics and music and movies. Which my XP can also access.

What you might consider is to intially just create a smaller ext3 for your backups and leave the rest unallocated then you can resize the ext3 to a larger size as you need and also have the flexiability to create aditional partitions later when the need arises.

---

### Post by Carbonfish on 2006-08-17
Thanks for the replies,

orb9220, I think that you hit the closest to the mark as far as what I am looking for is concerned. I have plenty of external storage space (for now), and don't really care whether any information can be shared between OS's. I realize that one partition doesn't care what the other ones on the drive are doing, but that said, I am just looking to have one relatively big partition dedicated to Linux, one partition dedicated to the iBook, and then I will have to decide how I want to use the rest of the drive and I think (unless I am mistaken) that I need to make that decision before I finalize the set-up because once I have the thing partitioned, the only way to re-partition is to risk the data already on the drive. 

Right now I have a 30GB partition that has a bootable clone of my iBook HDD on it. There is 110GB that is formatted as "free space", and there is another 110GB partition that is formatted HFS+ right now, but I can re-arrange that any way I choose. I would just prefer to get it right the first time.

Thanks for your help and suggestions. It's taken me a little bit over a week to finally get everything working on my ThinkPad after completely switching it to Ubuntu and I would hate to have to start over from scratch, so I figure that I really need to get serious about doin' the backup thing!

Thanks again,

Kent

---

