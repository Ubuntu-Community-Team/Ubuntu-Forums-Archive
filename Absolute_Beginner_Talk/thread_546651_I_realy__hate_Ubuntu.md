---
title: "I realy  hate Ubuntu"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by alx4 on 2007-09-09
hi really hate Ubuntu
i've just downloaded ubuntu 7.04 and burn it on a cd. 
I've run the live Ubuntu cd without installing it, and without make any changes or reading/writing to my HDD.
I've shout down the ubuntu, and started WinXp again. Now my WinXp is moving really slow. My HDD is always on reading/writing. My partions are NTFS. 

How to solve the problem that ubuntu causes to my HDD without formatting it?

---

### Post by shirilover on 2007-09-09
With the information that you have supplied, your ire should be directed at windows, not Ubuntu.

When in doubt, use the standard windows fix, restart.

---

### Post by por100pre1 on 2007-09-09
Do some disk defragmenting and disk cleanup first. If that is not enough check the [hard disk for errors]("http://www.microsoft.com/windowsxp/using/helpandsupport/learnmore/tips/kbtip.mspx"). I used Windows xp for many years I think this could be Windows fault. hope this helps. :)

---

### Post by Warren Watts on 2007-09-09
Is it possible you partitioned **all of the remaining free space on your hard drive** as an Ubuntu partition?  
Windows creates its swap file from free disk space, and if you didn't leave any "elbow room" for Windows to work in, it will definitely slow it down.
If this is indeed the case, you need to use a tool like Gparted to resize your Ubuntu partition to allow Windows some room to breathe, so to speak.

---

### Post by Paulmd on 2007-09-09
> **alx4 said:**
> hi really hate Ubuntu
i've just downloaded ubuntu 7.04 and burn it on a cd. 
I've run the live Ubuntu cd without installing it, and without make any changes or reading/writing to my HDD.
I've shout down the ubuntu, and started WinXp again. Now my WinXp is moving really slow. My HDD is always on reading/writing. My partions are NTFS. 

How to solve the problem that ubuntu causes to my HDD without formatting it?

Not sure about this one. The live CD doesn't write to the hard drive at all, unless you choose to install. So I really don't think that Ubuntu is at fault.

Anyway, XP is currently running slow because of excessive disk swapping.  There can be several reasons for this, but they boil down to not enough RAM for current applications.

The root cause is SOMETIMES a virus, sometimes just too many programs running all at once, especially quickstarters.

I would suggest taking your issue to another forum or newsgroup.

The microsoft.public.* newsgroups are well populated with helpful volunteers. In particular, the microsoft.public.windowsxp.general group. 

One way to get to the newsgroups is to sign up with Google groups

I would suggest a better title for your post, such as "Windows XP runs slow after running the Ubuntu Live CD"

---

### Post by Warren Watts on 2007-09-09
> **alx4 said:**
> I've run the live Ubuntu cd **without installing it, and without make any changes or reading/writing to my HDD**.

OOPS!  I wasn't paying attention when I replied a second ago...  :oops:
Ignore what I said...  :#-o

---

### Post by rich.bradshaw on 2007-09-09
I would guess that having become used to the speed and efficiency of Ubuntu, Windows seems slow in comparison.

If you don't install Ubuntu, it cannot modify any data on your harddrives.

---

### Post by n3tfury on 2007-09-09
> **rich.bradshaw said:**
> I would guess that having become used to the speed and efficiency of Ubuntu, Windows seems slow in comparison.



lol, no.  especially not compared to a live cd.  windows has its security faults, but unless you've got spyware a plenty, it's not slow.

---

### Post by Paulmd on 2007-09-09
> **rich.bradshaw said:**
> I would guess that having become used to the speed and efficiency of Ubuntu, Windows seems slow in comparison.

If you don't install Ubuntu, it cannot modify any data on your harddrives.

To quote Click and Clack (of Cartalk fame). Boo-oooo-ooogus. At least the line about speed and efficiency is. At least in this case, the live CDs are really pretty slow.  I can say on the computer I'm now typing on, that win2k was a lot peppier than Ubuntu.  I almost want to go back, but there's too much other stuff I like about Ubuntu. :)

Also: the disk thrashing is a new symptom, If windows had been very slow before, he's unlikely to have noticed a change.

The second part is definitely true, though. I don't see how running Ubuntu from the live CD could have affected Windows.

---

### Post by Taino on 2007-09-09
> **alx4 said:**
> I've run the live Ubuntu cd without installing it, and without make any changes or reading/writing to my HDD.

If this part is true then why are you blaming Ubuntu?

If you shut down the Live CD properly then it would of asked you to "reboot" which free's up used memory and on "reboot" your PC would be 100% back to normal.

(normal meaning the way it already was)

I think you just have a messed up computer on your hands, seems it was messed up before you even ran the Ubuntu Live CD.

Yep you should run scandisk or chkdsk and defrag your drive, but before you even do that i would unplug your computer for 5 minutes from the wall, (no power at all) then plug it back in, boot up, and run scandisk or chkdsk and defrag.

You may have a memory problem on your PC.

---

### Post by Steve1961 on 2007-09-09
If you didn't change anything when you ran the live CD I fail to see how your problems can be related to Ubuntu.  As other posters have stated, run chkdsk, defrag, sweep for spyware and viruses, and check your startup programmes.

---

### Post by Tautoa on 2007-09-09
Alternatively, boot up the LiveCD again, use GParted to make a partition for Ubuntu, and then install it.
Reboot into the Ubuntu partition, give it a try, find alternatives to all the programs you use on Windows (there are plenty of threads in this forum about that).
If you don't like something about Ubuntu, chances are, you can change it, (again, just search the forum).

Give the OS a fair shot before you decide you hate it... you may find that you actually prefer it to Windows, in which case you could get rid of Windows entirely, and give Ubuntu the rest of your hard drive space.
After that, it won't make a difference how slow Windows is, because you'll never want to use it again :)

---

### Post by swoll1980 on 2007-09-09
Running a Ubuntu live cd can't mess up your computer up any more than watching a dvd could. Either you did something you weren't supposed to on accident(like screw with your  partitions)  or your computer was screwed up to begin with. Period!!!

---

### Post by Jimmyfj on 2007-09-09
Maybe your Windows isn't running all that slow after all. Remember you have just tried out a very fast system, even when run from a Live CD. And I can assure you that the Live CD does not write anything to your disk. Could be that your Windows just experience a need for defragmentation. Maybe you need to check the amount of starting services when your Windows boots up. Also you could have a virus which didn't come from from the Live CD but from your last Windows session. The older the install on Windows the slower it gets. That's a know fact.

---

### Post by pat7089 on 2007-09-09
If your hard drive is always running, it means that there are some programs running in the background that you may not be aware of. I'd scan for spyware and viruses, neither of which are the fault of Ubuntu.

---

