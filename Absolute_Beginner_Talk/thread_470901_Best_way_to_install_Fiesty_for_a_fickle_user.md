---
title: "Best way to install Fiesty for a fickle user?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by samuraiCat on 2007-06-11
[Update #2]

Okay, everyone, I need your expertise. I will be putting together (literally) a new desktop PC on Wedneday or Thursday, and I want to know if this installation method will work and do what I want it to do.

Step One: First, I'll get a Guiness. 

(On Edit: Changed as per input below) Step Two: Install XP

Step Three: Open another Guiness.

Step Four: Next, I will boot up from my Fiesty liveCD.

Step Five: Since I want to use Fiesty but also test other distros and upgrade with ease, I'll partition the hard drive thusly from the liveCD: 
[INDENT](On edit #2: Added 20 more gigs to the OS)
1. 30G as ext3 (for my current distro, Fiesty in this case)
              2.  195G as ext3 (for /home with all my programs, personal files, etc)
3. 10G in NTFS for Windows crap (A temporary dual boot)
             4. 10G as ext3 (to later encrypt with Truecrypt)
             5.  5G as ext3 (for testing other distros)[/INDENT]

Step Six: Install Fiesty

Step Seven: Get printer, scanner, soundcard, firewire card, and video card working

Step Eight: Start installing Linux programs.


Now, here are my main questions:

1. Is this how I should do my install, generally?

2. Would it be a better idea to partition /home directory after I install Fiesty (Step Six)?

3. Will I be able to use Linux programs to read and manipulate .doc and .ppt files that reside in the NTFS (XP) partition, or should it really be formatted in FAT32?

Thanks a lot for your help!

---

### Post by Najand on 2007-06-11
You should install windows first and then install linux.
Also it is better to have Windows on the first partition of the harddisk.
Install /home at the same time of installing ubuntu.
You may read/write your files in NTFS partition with a driver called ntfs-3g

---

### Post by Seisen on 2007-06-11
Just make sure you don't spill the Guiness on the computer

---

### Post by samuraiCat on 2007-06-11
> **Najand said:**
> You should install windows first and then install linux.
Also it is better to have Windows on the first partition of the harddisk.
Install /home at the same time of installing ubuntu.
You may read/write your files in NTFS partition with a driver called ntfs-3g 

Thanks for the advice! Now, would it change your assesment if I told you that I was planning on only using that XP partition on very rare occations?

---

### Post by p_quarles on 2007-06-11
[COLOR=Black]First, most people have better luck installing Windows before, rather than after, installing a linux distro. MS isn't very good at noticing other OSs.

Feisty will allow you to partition the drive. It's partition manager is very good, and I'd recommend using it.

You can read NTFS partitions out of the box, but some tinkering is necessary to set up read/write access (you can find info by searching the forums when you get to that point).

3GB might not be enough for a Feisty installation. I read somewhere you should give it at least 10 gigs -- but I can't remember who said that, so it could be wrong. 

Good luck!
[/COLOR]

---

### Post by samuraiCat on 2007-06-11
> **Seisen said:**
> Just make sure you don't spill the Guiness on the computer Are stouts supported in Ubuntu? I really hate lager and pilsner.

---

### Post by phr0ze on 2007-06-11
Make step 5, step two. Add a step 3 to open another Guiness for the after putting the windows crap on your system. :)

---

### Post by samuraiCat on 2007-06-11
Thanks for the tips!

> First, most people have better luck installing Windows before, rather than after, installing a linux distro. MS isn't very good at noticing other OSs.

Okay, will do.

> 3GB might not be enough for a Feisty installation. I read somewhere you should give it at least 10 gigs -- but I can't remember who said that, so it could be wrong.

Okay, ten it is. Thanks!

---

### Post by Najand on 2007-06-11
> **samuraiCat said:**
> Thanks for the advice! Now, would it change your assesment if I told you that I was planning on only using that XP partition on very rare occations?

Well, as p-quarles said, it is just because Windose don't give a s*** to other OSes, so it just overwrite the MBR and you won't be able to boot your Linux Machine. Then you have to go through the recovery operation, which I believe people prefer not to go through it. 
So, even in that case, installing Windows before Linux is recommended.

---

### Post by sailor2001 on 2007-06-11
windows MUST be installed first. A fat32 partition is great for transferring files back and forth to windows/ubuntu..  My ubuntu is LOADED and yet only using 4gig +1/2g for boot + swap so you can judge from that a size partition for ubuntu.  I would think 20-40 gig is really more than enough

---

### Post by samuraiCat on 2007-06-11
> **phr0ze said:**
> Make step 5, step two. Add a step 3 to open another Guiness for the after putting the windows crap on your system. :)
Consider it done!

---

### Post by samuraiCat on 2007-06-11
> **sailor2001 said:**
> windows MUST be installed first. A fat32 partition is great for transferring files back and forth to windows/ubuntu..  My ubuntu is LOADED and yet only using 4gig +1/2g for boot + swap so you can judge from that a size partition for ubuntu.  I would think 20-40 gig is really more than enough

Thanks! So, will 30G be okay for the Ubuntu boot and swapfile?

---

