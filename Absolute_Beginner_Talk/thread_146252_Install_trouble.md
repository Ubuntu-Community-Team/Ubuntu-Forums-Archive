---
title: "Install trouble"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by Grandpastan on 2006-03-17
Hi. I am totally new to linux of any description. I got the install cd and decided to give it a try. The live version wasn't a fair test I don't think. I can't get as far as installing it though. I am trying to install it on a Sata Hd. It is an 80G drive split up into 8 separate drives. The one I am trying to set up for it is a 17 G drive. The last one on the HD.I can create the / and the swap partitions, but after I have done that the remainder is unusable. I set the / at 6G and the swap at 1G. I can't seem to find reference to my problem anywhere. Help.[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
](*,)

---

### Post by m.musashi on 2006-03-18
This may not directly answer your question but this [dual boot guide](http://users.bigpond.net.au/hermanzone/) deals a lot with multiple partions and the install process in general. It's quite good.

---

### Post by Grandpastan on 2006-03-18
I went to the page you suggested. I followed very carefully. When I get to setting up the second partition on the new drive, it doesn't let me specify what kind of partition it will be(primary/logical). It only allows me to on the / partition. Could this be the cause of the remainder of the space being unusable? If so, what do I do about it?  More info(if it means anything); I have Win 98 on a separate IDE drive "D". I have Win XP on my C Drive. I have  E,F,G,H drives as well. It would be My I drive that I am trying to set ubuntu up on. This is a Sata  Hard drive.

---

### Post by m.musashi on 2006-03-18
I think I understand the problem you are describing. I ran into something similar when I tried to create extra partitions using the ubuntu partitioner. I keep getting the unusable space problem after setting up the first (well second after XP) partition for ubuntu and then not being able to do a FAT partition as a storage space for both ubuntu and xp.

Unfortunately, I don't remember how I solved it. I think I did partitions from the "end" of the HD first but I'm not sure. I think I did a FAT drive on the end and then placed the ubuntu partition in the middle (xp, ubuntu, fat) if that makes sense. I tried several things and then evenually one of them worked. Someone once told me to keep a journal and I probably should have taken that advice.

If you have the option, another thought would be to put ubuntu on the IDE drive. That is what I did on my desktop. I have a SATA drive with XP and SuSE and then I added an IDE drive and used it for ubuntu. I seemed to work better that way.

Sorry, I can't be of more help. Play around with it and eventually you may figure it out or perhaps someone else might be able to offer better advice.

---

### Post by Grandpastan on 2006-03-20
Ok then. I did get farther than I've been before. I got it installed. It rebooted and guess what. I was in a never ending loop. Press A Key to reboot. Wish someone had told me not to install 2 OS's on the same drive. Completely hosed my XP. Had to re-install it. Suppose there are a few people sitting back and snickering. Oh well. I want to learn. I'm learning. Thanks people.

---

### Post by ds[de] on 2006-03-20
I don't know exactly what happened and why you got into that reboot-loop, but when you said it "hosed your xp", did you check the harddrive or couldn't you just not boot into win xp? Because depending on where you wanted to install the boot manager (grub/lilo), there might have been a possibility that just the master boot record got screwed up, not your data (on your harddrive).

I just took a shot in the dark here. If I'm mistaken, ignore this post, if not, maybe you'll remember this next time because there are ways of restoring/repairing your mbr without having to reinstall your OS.

Regards,
ds[de]

---

### Post by m.musashi on 2006-03-20
I'm not sure what you are describing. As long as you don't mess up the partitioning or erase the whole drive :) there shouldn't be any problem with installing more than one OS or messing up the OSs on other partitions. In theory, you can do as many OSs as you have space for - though it's possible some won't paly well with others. Ubuntu and XP seem to be fine and many people on this forum seem to be dual booting. I've never done more than two on a single drive but all my computers (2 laptops and 1 desktop) have a dual boot or in the case of the desktop a tri boot but only 2 on one HD and 1 on the other.

I have had problems with the MBR getting fried and as ds[de] points out that might have been the case. A bit more info on what happens regarding the reboot loop would help to diagnose that. Since you've reinstalled I guess it's a moot point. Have you been able to reinstall both XP and ubuntu successfully?

---

### Post by Grandpastan on 2006-03-21
I suspect it was the MBR as well. I tried to get it back from the recovery console on the Xp Cd. It couldn't even find the MBR, though I tried to fix,edit it and add to it. It couldn't find it. As for rebooting, it would just come up saying To Reboot, Press A Key. The only thing that would get me anywhere is the Del key to get into my Bios.

---

### Post by m.musashi on 2006-03-21
I tried several times to fix the MBR when I fried it. The windows xp cd has some tools for that but none of them worked and actually messed things up even more. Perhaps I just didn't know what I was doing. In my case I ended up reinstalling. Ubuntu will write a new boot loader (unless you are installing on one drive and booting from another - then I don't know what to do). There might be a better way to fix it but I'm not aware of any. Anyone else?

---

