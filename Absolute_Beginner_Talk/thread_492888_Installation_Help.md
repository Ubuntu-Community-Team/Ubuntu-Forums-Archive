---
title: "Installation Help"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by B-777 on 2007-07-05
I am new to Ubuntu and needed some install help.

I have downloaded and burned the ISO to CD without a problem.

The problem arises when I try to install ubuntu from the CD.

These are the steps I have taken:

1. Boot my PC from the CD
2. Unbuntu install menu appears
3. Choose start and install ubuntu from the menu

The problem arises after I pick #3. It will go to the shell giving the error "tty could not be loaded, job aborted" or  some other statement to that affect.

I would like to run ubuntu as a stand alone O/S, I won't be using XP anymore and don't have any files to transfer.

How do I get around this?

H

---

### Post by igknighted on 2007-07-05
Sounds like a bad burn... what speed did you burn the CD at... you should use 4x burn speed at the fastest to minimize errors.  Also, did you check the md5sum of the download before burning it?  Might be worth checking out to be sure your d/l wasn't corrupted.

---

### Post by silent1643 on 2007-07-05
could be a bad burn, make sure to burn your ubuntu disc at 4x 
just my .02

---

### Post by B-777 on 2007-07-05
> **igknighted said:**
> Sounds like a bad burn... what speed did you burn the CD at... you should use 4x burn speed at the fastest to minimize errors. 

I think that may have been the problem...I think it burned at more than the recommended speed (4X). I will try burning it again at a slower speed.

 > Also, did you check the md5sum of the download before burning it?  Might be worth checking out to be sure your d/l wasn't corrupted.

Yes, the md5sum checked out. I think its the first problem you mentioned (bad burn).

Will try downloading the iso again and burning it again at a slower speed as previously mentioned.

---

### Post by bigken on 2007-07-05
how much ram do you have ?

---

### Post by coolen on 2007-07-05
Looks like you're already getting help, so I just wanted to say, welcome! I hope you can work around this issue, and enjoy your experience with Ubuntu.

---

### Post by B-777 on 2007-07-05
> **bigken said:**
> how much ram do you have ?

512 MB

---

### Post by bigken on 2007-07-05
thats more than enough like the others have said could be a bad burn 
you could also try gparted LIveCD to format your drive 1st then run the 
installer ;)

oh and failing that give the alternate cd a shot

---

### Post by B-777 on 2007-07-05
> **coolen said:**
> Looks like you're already getting help, so I just wanted to say, welcome! I hope you can work around this issue, and enjoy your experience with Ubuntu.

Thanks coolen, I am sure I will once I get all this figured out ;)

From the screenshots I have seen, it really looks like a great O/S with a windows like interface, just need to learn the ins and outs of Ubuntu.

Oh and theres another question I had.

Should I reformat my Hard drive before installing ubuntu or does ubuntu have the option of refromatting the hard drive before you install, like it is when you install XP from a CD?

---

### Post by coolen on 2007-07-05
All happens from the installer. You can resize and move partitions around all you want, too.
Although I applaud your choice, just be sure that you want to ditch Windows. Most users choose to dual-boot. It's helpful for the transition phase, if you're holding on to a few applications for which there is no Linux equivalent, or as a backup if something goes wrong (it happens, we admit it).
I'd hate for you to dive right in and run into a massive hardware issue.
If you want, you can leave Windows there for now, and later, having set up Ubuntu, format it and use it for /home. It's common practice to use a separate home partition.

---

### Post by bodhi.zazen on 2007-07-05
If it is not a bad burn, you will need to install via the alternate CD

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by DoricMan on 2007-07-05
I had such a problem as this, but only on Ubuntu 7.04. I wanted to dual-boot Ubuntu and XP on an XP desktop that had 3 Serial ATA hard disks, and 2 IDE hard disks. I found that I had to disconnect the 2 IDE hard disks and then was able to install Feisty as normal.
I hope this helps.:D

---

### Post by B-777 on 2007-07-05
Ok I have boiled down the problem to a bad burn.

I am using infra recorder, as per the instructions in the burn to CD.

I set the write to CD speed at 4X (Even tried 2X & 1X) but it is still burning at 8X, no matter what I try speed I try.

Is there a work around this or another freeware program like infra recorder I could try?

---

### Post by bigken on 2007-07-05
if your using windows try the iso burner in my signature

it could also be a bad batch of discs ?

---

### Post by B-777 on 2007-07-05
> **bigken said:**
> if your using windows try the iso burner in my signature

it could also be a bad batch of discs ?

Well, I did manage to copy a whole bunch of MP3s onto a CD without a problem, but not sure why it won't burn an ISO image.

Will give it a go.

---

### Post by B-777 on 2007-07-05
Now I have FINALLY figured out whats going on :p

It wasn't a bad burn after all.

When I select the start or install ubuntu it starts loading, but for whatever reason, it is trying to read off the a: drive (which has no disc in it) instead of the CD.

It then goes into the console and gives me the tty could not load error.

Is this a BIOS error? do I need to go into my BIOS and change the boot device priority or is this another problem.

Sorry about the confusion...didn't realize the true problem until now.

---

### Post by bodhi.zazen on 2007-07-05
It is a bug and has been reported, that is why I suggested the alternate CD earlier.

*Assuming I have the correct bug, can't find the link on Launchpad at the moment.

---

### Post by B-777 on 2007-07-05
> **bodhi.zazen said:**
> It is a bug and has been reported, that is why I suggested the alternate CD earlier.

*Assuming I have the correct bug, can't find the link on Launchpad at the moment.

No worries...I'll try the alternate CD install as suggested...didn't realize it was a bug.

If you do find the bug, please post it here for me to read and keep track of.

I am going to try an earlier version of Ubuntu until this bug is worked out.

Thanks for all the quick responses :)

---

### Post by B-777 on 2007-07-05
> **bodhi.zazen said:**
> It is a bug and has been reported, that is why I suggested the alternate CD earlier.

*Assuming I have the correct bug, can't find the link on Launchpad at the moment.

No worries...I'll try an earlier version until the bug is worked out..as I didn't realize it was a bug.

If you do find the bug, please post it here for me to read and keep track of.

I am going to try an earlier version of Ubuntu until this bug is worked out.

Thanks for all the quick responses :)

---

### Post by B-777 on 2007-07-05
Downloading the 7.04 alternate install as we speak.

But one question I had is, will still install the "Demo" mode as found in the standard install?

I would like to try it out just so I can get used to the new options and interface before doing a complete install.

---

### Post by bodhi.zazen on 2007-07-05
No, the alternate CD does not run live, it is for installation only ...

---

### Post by B-777 on 2007-07-05
> **bodhi.zazen said:**
> No, the alternate CD does not run live, it is for installation only ...

Thanks. 

Looks like I will have to try the previous version until this bug in 7.04 is resolved (If it exists).

---

