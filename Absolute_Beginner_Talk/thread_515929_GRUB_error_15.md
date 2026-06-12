---
title: "GRUB error 15"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by amneziac on 2007-08-02
omg, I am trying so hard to just get this OS working but it keeps messing up on me. Now I'm scared because when it was at 94% the installer just closes and nothing happens, then I restart my computer and it keeps saying 

GRUB Loading Stage 1.5.

GRUB Loading please wait...
Error 15


WHAT HAPPENED?!

---

### Post by asmoore82 on 2007-08-02
I would test the RAM with the LiveCD;
if the RAM is okay maybe test the hard drive

---

### Post by annda on 2007-08-02
most probably the install didn't complete. error 15 means "missing file" - probably the kernel wasn't installed. can you reinstall? you won't have to repartition your disk this time - choose the manual option and select your linux partitions (root mounted as "/" and swap).

---

### Post by dannyboy79 on 2007-08-02
most likely you're grub install got messed up but without knowing exactly what completed and what didn't, I would suggest using the installer to reinstall eveything BUT if I were you I would reformat as who knows what's on the drive. I would want to start with a clean format.

---

### Post by amneziac on 2007-08-02
its weird because at 94% it just closes and nothing happens and when its at like 80% it says "100% is full", so how can i fix all this, im so nervous now that I cant load windows
on the root partition it says 2200MB of 2212 MB is used....

---

### Post by dannyboy79 on 2007-08-02
ok, well that's a different story then. how big is the partition that you're trying to install Ubuntu on? you can always just boot up a livecd, then manually mount your windows partition and I gurantee that your stuff is there and it ok. The only time Ubuntu will overwrite it is if you told it to (whether you realized it or not) within the installer. once you have it mounted and you can see it, if you have another usb disk, you could mount that as well and copy data from the mounted windows partition off onto a safe disk that won't be involved during the install BUT I can tell that the installer only does what you tell it to and does not overwrite windows stuff accidentally.

---

### Post by amneziac on 2007-08-02
Ok so here are the problems that I'm getting

1. Installation ends at 94%
2. Everytime I turn on the computer it says: Grub Loading please wait Error 15.
3. Root partition size is 2212MB but 2200MB is already used now and installation didnt even finish
4. At about 80% it says that the partition is 100% full (which makes sense since there is now only 12 MB on the root partition)
5. When I had space on it, when it almost finished it said "Cannot install GRUB (hd0) Fatal Error.

The root file system is where Ubuntu is installing right? if it is then my partition is 2212 MB but it says 2200 MB is used
I'm in maunal to prepare partitions so heres what I have

/dev/hda1 ntfs /media/hda1 Size: 99772 MB Used: 43600 MB
/dev/hda6 swap Size: 254 MB Used: 0 MB
/dev/hda5 ntfs /media/hda5 Size: 97806 MB Used 3300 MB
/dev/hda7 ext3 / Size: 2212 MB Used: 2200 MB

---

### Post by amneziac on 2007-08-02
so if someone could please give me a step by step guide on what to do that would be awesome

---

### Post by dannyboy79 on 2007-08-02
well to get back into windows you could use a winxp cd in recovery mode and issue a 
fixmbr
this will return your mbr so that windows boots up again. BUT I have to say, approx 2.2 seems like it's barely enough. 

Show me the output of sudo fdisk -l from a livecd. then also within that live cd, mount all your partitions to a folder you create within /mnt or where ever and issue the 
df -h
command, this will give you approximately how much space is left on each partition.

Not to mention it sounds like your MBR isn't allowing you to write to it. I ahve heard of this before. The FREE solution is to get testdisk or some other utility to "shread" the drive including the MBR. Meaning "wipe it away" not just format it. It acutally writes zero's to the entire drive. I think Seatools from Seagate will work on any drive but I can't guarentee that. I know testdisk can erase the MBR. Testdisk is on the Gparted Livecd. OR you can use a livecd and use the dd command. gogle "write zeros with dd".

Then either try to install grub OR do the install over.

---

### Post by annda on 2007-08-02
oops, you've given only 2 GB to ubuntu - that is definitely too little! if you can't cut a chunk off your media storage partition (hda5), you WILL have trouble installing. other than resizing hda5 (it has a lot of free space), i'd recommend the alternate install cd - but as a second choice only. 4-5 BG is a decent size, meaning you should have a nice install and some space left over for installing additional programs and storing some personal files.

---

### Post by amneziac on 2007-08-02
oh crap, i though the hda5 was how much space i wanted for Ubuntu, but I guess all the space I want for installing programs, personal files, and all that should go to ext3 then right?

---

### Post by dannyboy79 on 2007-08-02
> **amneziac said:**
> oh crap, i though the hda5 was how much space i wanted for Ubuntu, but I guess all the space I want for installing programs, personal files, and all that should go to ext3 then right?

don't know what you're asking? We need to know what you want your parititon table to look like. For example, do you want a /home partition? At a min, you'll need / and /swap. swap is formatted as swap and / is formatted as ext3.

my partition table for example looks like this

/dev/hda1 is my /boot partition (50mb)
/dev/hda2 is my / partition (10gb)
/dev/hda3 is my swap parititon (1.5gb)
/dev/hda4 is an extended partition for growing purposes (remaining space)
/dev/hda5 is my /home partition (remaining space)

---

### Post by amneziac on 2007-08-02
/dev/hda1 ntfs /media/hda1 (remaining)
/dev/hda6 swap (254MB) < swap
/dev/hda5 ntfs /media/hda5 Size: 97806 MB
/dev/hda7 ext3 / (50 GB) < root

so thank God I got this finally installed
now my last question, you had 1.5GB swap, so should i make mine a lot larger than 254MB?

---

### Post by dannyboy79 on 2007-08-03
that's up to you. If you have less than 1.5gb of physical ram than I would but that's just my opinion. a general rule is to make swap 1.5 to 2 times the size of physical ram BUT when you get up around 2gb of physical ram you won't ever really use that much ever (for the average user)

---

