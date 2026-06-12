---
title: "Tool for repair sectors on a HD"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by thomas7.10 on 2008-04-14
Hi!

I think something is wrong with my HD. So i'm wondering now if there is a Program that checks for bad sectors and repairs them. Most likely my bad sectors are virtual ones. It would be great if that would be on a bootable CD. I tried with ubuntu live disk but that mounts automatically the HD and so i can't use fsck. Someone got a clue?

Thomas

---

### Post by hyper_ch on 2008-04-14
(1) run the desktop-cd
(2) unmount the drives that you want to check
(3) run chkfs (or ckfs) on those partitions

---

### Post by thomas7.10 on 2008-04-14
sounds good - how do i unmount a drive?

---

### Post by akudewan on 2008-04-14
Suppose you want to unmount hda1, run this in a terminal :
```

sudo umount /dev/hda1

```

Replace hda1 by whatever is appropriate

PS: In some cases, right-clicking on the drive and selecting Unmount will work just as well

---

### Post by hyper_ch on 2008-04-14
on the live-cd you don't need to use sudo (I think) and live cd is necessary if you want to check your system partition(s)

---

### Post by nick_h on 2008-04-14
Running *fsck* and/or *badblocks* is a good idea.

You may also want to download disk checking software provided by your HDD manufacturer.

---

### Post by az on 2008-04-14
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

See the above link on how to use S.M.A.R.T.

Smart can make your drive avoid bad blocks.  That's the best way to keep your drive alive.

---

### Post by thomas7.10 on 2008-04-14
So now i can tell that i got it managed to break down everything.

The hole storry from the beginning.

I wanted to install XP while ubuntu still having on the system. So i downloaded a windows XP ISO file from the internet because my computer wich i bought with windows installed on it came without any kind of disk. So then i downloaded and burned many different windows on CD then i also downloaded GParted live CD and did as i was told in the tutorial. Then it took me ages to get a windows that really recogniced the free space. So ok got this done at least.
So i came from the ubuntu live CD and tried to set bootflags or whatever. That didn't work at all and in the end when starting my computer with the boot flag set to ubuntu it said Operating system corrupted. Ok ubuntu got lost that's the thing i had to accept.
So i changed back to windows and it was still booting. It's some kind of fancy graphic version. But my sounddrivers are not supported because they need a windows update and i can't get the update because the only windows version i got to run seems to be detected as a illegal copy.
Furthermore it is in a strange language with unknown letters.. some asian: &#3615;&#3627;&#3585;&#3648;&#3585;&#3604;&#3635; &#3616;&#3604;&#3648;&#3627;&#3611;&#3649; &#3611;&#3649;&#3629;

So and in the end of the day nothing works. No windows no linux (I still have the linux files on the disk and can acess them via a live cd).

Is there any possiblity to get the ******* mashine to run as i want it to without loosing all my data? 

At the moment i consider burning my PC on the balcony and buying a typewriter as the most satisfying  i could do.

---

### Post by skymera on 2008-04-14
Spinrite 6 (private message me about it)

It checks all of your disks, 5 levels of depth and can take 1hour - a day.

It fixed my laptop and reapird all the secors.

---

### Post by az on 2008-04-15
> **skymera said:**
> Spinrite 6 (private message me about it)

It checks all of your disks, 5 levels of depth and can take 1hour - a day.

It fixed my laptop and reapird all the secors.

Spirite is not recommended.  When it works, it does the same thing as SMART, only take a more dangerous route to get there.

It's marketed with the slogan that "it really works".  You never hear about the times that Spinrite fails and eats your data.  You should never write to a failing device.

---

### Post by thomas7.10 on 2008-04-15
Ok i think i'll buy a portable HD then copy all my data on that and then i will trz do delete everything, repair sectors and all this stuff with some kind of tool - i'm willing to pay for such kind of tool. 

So isn't there a tool that just removes everything and fixes everything that needs to be fixed?

---

### Post by az on 2008-04-15
> **thomas7.10 said:**
> Ok i think i'll buy a portable HD then copy all my data on that and then i will trz do delete everything, repair sectors and all this stuff with some kind of tool - i'm willing to pay for such kind of tool. 

So isn't there a tool that just removes everything and fixes everything that needs to be fixed?

S.M.A.R.T. should be build into your drive already.  You just need to tell it to check itself.  It should be able to reassign blocks without you having to move your data around.

There is no proprietary tool that can do the job better.

---

### Post by nick_h on 2008-04-15
Yes, SMART is a good starting point.
```
sudo apt-get install smartmontools
```
and then follow the directions in the link.

Disk diagnostics from the manufacturer will also be free.

---

### Post by thomas7.10 on 2008-04-15
So i decided to live with it as it is and give it a new try when Hardy is out - so i will at least not have to deal with the question if i should make a clean install or update...

---

