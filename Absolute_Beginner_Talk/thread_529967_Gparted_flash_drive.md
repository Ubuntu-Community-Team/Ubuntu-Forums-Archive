---
title: "Gparted flash drive?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by jpr13 on 2007-08-19
I want to foramt a flash drive and it is locked. How can I unlock it??

                            Jason

---

### Post by verbalshadow on 2007-08-19
You should be able to unmount it by right click on the partition in gparted and selecting unmount. if that doesn't work goto the desktop and right click the drive there and select eject or unmount.

---

### Post by Aishiko on 2007-08-19
> **jpr13 said:**
> I want to foramt a flash drive and it is locked. How can I unlock it??

                            Jason
Sorry all Flash drives are set up so you can't format them in anything other then a FAT filesystem and since Linux, Windows, and Mac can read and write to FAT why bother trying to change it's format?

---

### Post by Ek0nomik on 2007-08-19
> **Aishiko said:**
> Sorry all Flash drives are set up so you can't format them in anything other then a FAT filesystem and since Linux, Windows, and Mac can read and write to FAT why bother trying to change it's format?

Not true.  You can change the file system, he probably just needs to unmount it as verbalshadow suggested.

It is, however, not always the best idea to format the USB device to a journalling file system, as soon you will find the USB device filling up with "hidden" data (which is what the journalling system is supposed to do).  If he has a big enough USB device though he will be fine.

---

### Post by Aishiko on 2007-08-19
ohh I was told you couldn't.

but then since FAT out of the box works with every thing and I use flash drives to transfer data from 1 computer to another I don't see a real reason to gimp it's ability to do so by puting a filesystem on that might not be as univerally compatable like NTFS or EXT3.  Just my 2 cents.

Oh and what filesystem are you planing to use?  I'm now curious.

---

### Post by Ek0nomik on 2007-08-20
> **Aishiko said:**
> ohh I was told you couldn't.

but then since FAT out of the box works with every thing and I use flash drives to transfer data from 1 computer to another I don't see a real reason to gimp it's ability to do so by puting a filesystem on that might not be as univerally compatable like NTFS or EXT3.  Just my 2 cents.

Oh and what filesystem are you planing to use?  I'm now curious.

Definitely.  You are right on the ball.  :)

Having it be FAT32 makes it very convenient as you can take it to a *nix or Windows box and have it work just fine.  I have both of my external hard drives and FAT32 for that reason.  :)

---

### Post by Aishiko on 2007-08-20
> **Ek0nomik said:**
> Definitely.  You are right on the ball.  :)

Having it be FAT32 makes it very convenient as you can take it to a *nix or Windows box and have it work just fine.  I have both of my external hard drives and FAT32 for that reason.  :)
LOL and since FAT32 has a I think 30 gig limit Flash media is going to take a while to get to the point where it's bigger then that and unless you have a 40gig or bigger harddrive as a swap drive or NAS FAT32 will work as well, but that being said I have 2 drives I mistakenly formated as NTFS and use as swap mediums, so I'm going to have to transfer the data off and reformat as FAT32 sometime in the future proablly under Windoze :P, to avoid any potential compatablity  issues.

---

### Post by Ek0nomik on 2007-08-20
> **Aishiko said:**
> LOL and since FAT32 has a I think 30 gig limit Flash media is going to take a while to get to the point where it's bigger then that and unless you have a 40gig or bigger harddrive as a swap drive or NAS FAT32 will work as well, but that being said I have 2 drives I mistakenly formated as NTFS and use as swap mediums, so I'm going to have to transfer the data off and reformat as FAT32 sometime in the future proablly under Windoze :P, to avoid any potential compatablity  issues.

FAT32 has a 30GB limit?  What do you mean?

FAT32 file systems have a 4GB limit per single file.

---

### Post by Aishiko on 2007-08-20
> **Ek0nomik said:**
> FAT32 has a 30GB limit?  What do you mean?

FAT32 file systems have a 4GB limit per single file.
30 gigs for the volume's limit I was wrong it's 8Tib according to [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems) I was off by a small amount (OK, OK I only said it was about 1/3 of a percent of the actual limit)  Ohh well either way flash media are going to take a much longer time to get to then 30 gigs. :P

---

### Post by Ek0nomik on 2007-08-20
> **Aishiko said:**
> 30 gigs for the volume's limit I was wrong it's 8Tib according to [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems) I was off by a small amount (OK, OK I only said it was about 1/3 of a percent of the actual limit)  Ohh well either way flash media are going to take a much longer time to get to then 30 gigs. :P

Indeed, it will take a bit.

I have a 500GB and 250GB hard disk as FAT32.

---

### Post by Aishiko on 2007-08-20
hmmmmm I might just FAT32 that 500 giger once I get it next week.

---

### Post by Ek0nomik on 2007-08-20
> **Aishiko said:**
> hmmmmm I might just FAT32 that 500 giger once I get it next week.

What else are you still considering?

---

### Post by Aishiko on 2007-08-20
well I was thinking of EXT3 at first and then NTFS since I think I'll put it in my windoze computer until I'm comfortable in Ubuntu.

then Port it over to that computer.

---

### Post by Ek0nomik on 2007-08-20
If you are going to start using Ubuntu permanently I wouldn't suggest using NTFS.

---

### Post by Aishiko on 2007-08-20
I hope to, I even looked into taking classes on Lunix at the CC but deadline for registration is tomorrow and they don't have my FSFA information yet so I'd have to pay out of pocket for classes and I don't have that kind of money free right now, plus the course is on RedHat, and last time I tried that I was annoyed at the lack of support, the inablitly to add programs in any way I couldn't even get the blasted thing to complie a program, locate and mount an Optical drive, let alone find my internet and then it after a week of head banging ended up not even letting me log in it would hang and then just sat there.  Like if it couldn't find the gear it would grind them.  Wrote off Linux for a bit after that I considered it a wasted investment.

---

### Post by Ek0nomik on 2007-08-20
> **Aishiko said:**
> I hope to, I even looked into taking classes on Lunix at the CC but deadline for registration is tomorrow and they don't have my FSFA information yet so I'd have to pay out of pocket for classes and I don't have that kind of money free right now, plus the course is on RedHat, and last time I tried that I was annoyed at the lack of support, the inablitly to add programs in any way I couldn't even get the blasted thing to complie a program, locate and mount an Optical drive, let alone find my internet and then it after a week of head banging ended up not even letting me log in it would hang and then just sat there.  Like if it couldn't find the gear it would grind them.  Wrote off Linux for a bit after that I considered it a wasted investment.

Taking a class could be beneficial.  I have never taken one, so I can't claim it to be a waste.

I personally have found the best way to learn, from my experiences, is browsing the forum and attacking a problem one step at a time.

When I went to figure something out I'll make a post on the forum, or if I am getting an unexpected error I search the forum or a search engine.  You have a lot of free tools available to you.  :)

Do you have Ubuntu installed right now?  If you need help with certain things I'll give you any help I can offer.  :)

---

### Post by Aishiko on 2007-08-20
I don't think the class would be a waste, I found REDHAT to be a waste of the time and moeny I'd put into it.    So I'm leery of going into a class that teaches you how to use Redhat and is part of a 2 course thing that leads to redhat cerification when I have no intrest in being certified or even taking the second course sine in the spring I'll be back at my 4 year university.

---

