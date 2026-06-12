---
title: "Confused, selective booting?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by championchap on 2006-07-10
Hey guys, well.. im not even sure if Kubuntu has anything to do with my problem, but it started when i installed it.. so i thought it best to ask here.

I was planning on formatting my drive, to clear out my old Fedora instalation (i didn get along with it to well) and to clean out my XP shaith.
So, i thought "hmm, may as well give Kubuntu a go.. whats the harm right?" Well, i only had a breezy disk at the time, so i got to work, i formatted and got about halfway through the installation before i hit problems.. this left me with a half installed Kubuntu on my HDD.

Afterwards i slapped in my XP installation disk, which is now simply refusing to boot. Ive tried everything i can think of. I burned a new XP disk, ive slapped in a clean HDD.. but nothing i do seems to work.

Linux however is read easily enough, and i just recieved my Kubuntu Dapper CD's in the mail yesterday, that installed without a problem.

But what i use my computer for primarily is Macromedia Flash, which i simply cant do with Linux without reducing it all to a snail pace.

Everyone else ive asked about this has just said "huh, weird..."
any ideas?

---

### Post by diepruis on 2006-07-10
So your computer won't even boot from the WindowsXP CD? But it does boot from the Kubuntu CD?

---

### Post by brentoboy on 2006-07-10
I had a system at one point that an XP just couldnt handle.  I had a bunch of differnt linux partitions on there  I think the one that made the biggest problem was the one on /dev/hda1

I think the windows install CD wants a non-linux box to start with, and then you have to add linux after your windows install.

anyway, I fixed it by flushing all the linux partitions and creating one big fat32 partition from the ubuntu installer, and then aborting after the installer finished setting up and formatting partitions.

then windows worked.

the alternative that I see is removing the linux drive, and installing windows on your new drive that you mentioned.  Then, pop the linux drive back in and cross your fingers.

---

### Post by championchap on 2006-07-10
Well, the other HDD i mentioned ive already tried with the Windows Disk, as far as i know its completly blank.

I could try formatting the Kubuntu drive and exiting after formatting like you suggested i guess.
When i run the bootloader before grub starts i choose 3 to boot from the CD Drive, then it tries.. and fails. Tells me to retry or go back to the BIOS. Nothing seems to help.

One suggestion ive had is getting hold of another CD Drive in case there is a problem there.

I really dont know what to do.

---

### Post by nalmeth on 2006-07-10
Whats the problem here? You've tried working with flash in linux, and it's too slow, so you're trying to go back to XP?

First, what are you needing to do with flash? There may be solutions for the laggyness when running flash, I've never experienced this with my (admittedly) limited use of the darn thing.

Second, a new CD-Drive might help, or if you're looking for another option, there may be a new BIOS available for your motherboard. This can clear up a lot of problems with your PC, some you may not even recongnize yet. Look up how to 'flash your BIOS', but take great care when doing this, it can be dangerous if you don't follow instructions to the tee.

Possibly then the XP CD will boot.

---

### Post by championchap on 2006-07-10
I do a lot of animation, game programming and complex graphics using Flash.
But yeah, i need to go back to XP, theres a lot of commercial apps on Windows that i cant really do without.

anyway, this isnt really the issue.

thanx for the BIOS Tip, but you know, the Windows CD used to boot fine. I reinstalled XP not 5 months ago now on the same hardware without a single problem.

Ill give it a look though.

---

### Post by diepruis on 2006-07-11
Huh, weird :) Just joking...

Have you tried changing around the boot order in the BIOS itself?

---

### Post by championchap on 2006-07-13
sorry ive not been checking on this.. been using the time to get better accuainted with Kubuntu

umm, yeah.. ive got my boot order set us as CD then HDD, always will be.. well, probably.
It was the first thing i checked.

---

### Post by diepruis on 2006-07-14
Mmmmm... This will sound obvious, but have you tried cleaning the CD? My kubuntu CD didn't want to boot and this solved it.

---

