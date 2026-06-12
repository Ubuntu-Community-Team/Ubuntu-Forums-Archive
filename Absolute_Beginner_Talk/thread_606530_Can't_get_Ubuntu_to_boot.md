---
title: "Can't get Ubuntu to boot"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by DoocesWild on 2007-11-08
I wanted to try out gOS, so I downloaded the image, burned it, and brought it to my desktop.  I restarted my computer, and got nothing.  I brought it to my laptop, ran gOS just fine. 

Saw that gOS was just simply Ubuntu, so I looked into Ubuntu, and I like what I see here.  So, I repeated the process with my Ubuntu disc.  Same thing, works on my laptop, not my desktop.

I've installed windows xp a hundred times on my desktop, and every time it simply involves inserting the boot disc, restarting, and following the instructions.

For some reason, my computer won't boot with my gOS disc, Ubuntu disc, or my windows disc.  It skips by it and heads straight on over to windows.  

I've already checked, my boot order is Floppy, DVD Drive, then HD.  When I have a boot disc in the drive, it hangs for quite a while when it's "Checking the IDE Drives" then the light turns off.  After this point, it says something along the lines of "Boot From CD" then skips right over to windows.  

As far as I can remember I haven't made any hardware changes.  Any ideas on how to get my computer to read from my boot discs again?  I'd love to dual boot Ubuntu and Windows...

---

### Post by alienexplorers on 2007-11-08
In your BIOS do you have an option to boot DVD,FD0,HD in that order?

---

### Post by RoboBo on 2007-11-08
I have the same issue with my XP desktop - BIOS is a Phoenix & saw on another thread that is a "known issue". My boot order is CD-ROM, Floppy, Hard Drive, Network.  When I restart the 7.10 Live CD will light up for a short time, then the cloppy sounds, then XP comes up. I have been looking for a floppy program to get the machine in Linux then point to the Ubuntu CD. 

Don't have an answer, but sure am interested in a solution for the issue.

---

### Post by Doggles on 2007-11-08
If your drive is spinning up and waiting for a while, it sounds like it is at least trying to access the disk... hmmmmmm....

How was the CD burnt? - I know this might be insulting, but it was made from an iso image and therefore is a proper bootbale disk? (I've seen it couple of times where burning software was used to simply put the iso file onto the CD simply as a file in a folder, rather than as an image for the whole disk) 

...and can it be read under XP by that particular drive? - just checking because sometimes a particular drive won't like a particular disk. For instance, I have a backup archive (of all things...) on a DVD, and one of the drives in my desktop can read it fine, while the other one just grumbles for a bit and then fails to mount it... so it is possible for it to work fine on your laptop but still be rejected by your desktop's drive.

To really double-check this you could try another linux disk to verify that your desktop is trying to boot from CD. I use a live CD that I got out of "Linux Format" magazine because I know that commercially produced disks usually stand a much better chance of working in any drive.

---

### Post by devilears on 2007-11-08
When it says "Boot From CD" , hit the enter button.

---

### Post by DoocesWild on 2007-11-08
To try and sum up everything here, 

I've tried to hit the enter button when it says Boot from CD.  When it used to work, it would say "Boot from CD... Press any Key to boot from CD" but it never gets to this point.

The live discs I've burnt have been using Nero, in the burning ROM, choose Recorder, Burn Image.  The thing is, I've been trying to use a legit copy of XP Pro as well, and that's always worked for me, of course, up until now.

I can change anything in my BIOS in terms of boot order.  Do you think changing it from floppy, cd, hd to cd, floppy, hd will actually make a difference?

My bios is Phoenix as well.  I'd love if you found an answer to alert me...

Also, when I try and read the disc in windows xp (the desktop) it says that it's not a valid windows application. (but it says this on my vista machine (laptop) that works with the disc.

---

### Post by ByteJuggler on 2007-11-08
Try burning the CD at the slowest possible  (or at least a slower) burn-rate.  Maybe the drive on the one machine is having trouble reading the disc.

---

### Post by DoocesWild on 2007-11-08
> **ByteJuggler said:**
> Try burning the CD at the slowest possible  (or at least a slower) burn-rate.  Maybe the drive on the one machine is having trouble reading the disc.

I actually did this as well.  Burned at my drives slowest, 10x. 

My problem, I assume is that my drive won't read ANY disc.  I tried a number of factory burned discs, as well as some that I burned on my own, and in Windows, nothing worked.  I mainly use this box as a host for all of my files, as I have hundred of gigabytes on this, and very much fewer on my laptops.  I hadn't used the DVD drive in my desktop in ages.  Looks like it finally bit the dust.  

I'll replace it and let you guys know if it worked.

---

### Post by twiceasworn on 2007-11-08
Sounds like that drive is definitely dead dead dead.

---

### Post by DoocesWild on 2007-11-08
Yeah, It just spins for a while, then stops.  I've got another drive, so that should probably work.

I know they say on gOS that there is no way to play audio or dvd.  Is this the case on Ubuntu as well?

---

### Post by ByteJuggler on 2007-11-08
> **DoocesWild said:**
> Yeah, It just spins for a while, then stops.  I've got another drive, so that should probably work.

I know they say on gOS that there is no way to play audio or dvd.  Is this the case on Ubuntu as well?

Provided your Sound hardware and Graphics card is supported, and provided you install the required libraries and codecs, Linux has no problem whatsoever playing audio and DVD.

---

### Post by Doggles on 2007-11-09
Yep that's right - I think Ubuntu doesn't have some of the necessary codecs installed by default because they don't like to involve users in "content protection" measures like DVD content scrambling, and also, believe it or not, mp3 is a "non-free" proprietary format. It's really easy to get these to work on Ubuntu though - it's just that if you want it, you have to ask for it by installing the codecs yourself - for instance, for DVD playback, look up "libdvdcss"

---

### Post by mudcow007 on 2007-11-09
i would disable boot from hdd and floppy so the only bootable device is the cd drive

restart with the ubuntu or windoze disk in the drive

ive had this with a few xp machines :)

---

### Post by DoocesWild on 2007-11-09
> **mudcow007 said:**
> i would disable boot from hdd and floppy so the only bootable device is the cd drive

restart with the ubuntu or windoze disk in the drive

ive had this with a few xp machines :)

I'll try this once I have a few minutes to try the new drive out.  Pretty sure it's just a dead drive.

---

