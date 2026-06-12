---
title: "Installing Method Help"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-07-09
I've tried the Ubuntu 7.04 LiveCD and now I am hooked. The issue is my 40 gig hard drive doesn't contain
enough space for a real useful  Ubuntu installation.

I was thinking of doing this and wanted everyones opinion to see if it would work.

I have an extra 80 gig hard drive laying here and was thinking of Blasting my XP
image onto it with some Ghost BackUp images I have made.  Then I could install
Ubuntu on all that left over space that hasn't been formated yet.

What I am wondering is how Ghost will handle it.  If I have made a Backup
of my C and D partitions on a 40gig drive what will happen when I blast that
image onto an 80 gig drive.  Will it just blast the image and leave all that space
unformatted.  I plan on just taking the 40 gig out and leaving it just as is
and putting everything onto the 80 gig.  That way if I mess up and can
just put the original drive back in.  

Also, do you think that this would make the WinXP Activation come up?
It may see that it's on another HardDrive....


Will this work...... Thanks guys

---

### Post by steve.horsley on 2007-07-09
I don't know about the wisdom of doing that. Even if Windows didn't throw a blue fit, you will probably wind up with an 80G disk that thinks it's a 40G disk.

Why not add the other drive as a slave/second hard drive and install Ubuntu on that? Maybe leave some space to make a Windows D: if you want.

---

### Post by Orbital75 on 2007-07-09
Steve..... I agree that would be a better idea but I have 2 Hard drives currently in my system on IDE1.
I also have 2 optical drives on my IDE2.

What kinda of trouble would I be looking at if I decided to take out one of the optical and throw it on the Slave
of IDE2.  I've always heard to keep Hard drives on one channel and Optical drives on the other.

---

### Post by steve.horsley on 2007-07-10
I think it may lead to performance issues like trouble doing high-speed CR burning because it's reading the data from a drive on the same cable, doubling the traffic on the cable. But if you're just trying out Ubuntu, I don't see the harm in doing that.

Be aware that installing Ubuntu will replace your bootloader with one that relies on support files on the new hard disk - you would have to replace GRUB bootloader before disconnecting that new drive again.

---

### Post by annda on 2007-07-10
if your BIOS can boot from USB, you could get a cheap external case for the drive and also put GRUB there, so that you won't have trouble when booting without the disk conncted.

---

### Post by buzzmandt on 2007-07-10
i currently have a 40g  drive for windows hda1

and a 180g hard drive with pclinux on hdd1, and ubuntu/kubuntu on hdd3 (hdd2 is swap), works great

---

### Post by Orbital75 on 2007-07-10
> **annda said:**
> if your BIOS can boot from USB, you could get a cheap external case for the drive and also put GRUB there, so that you won't have trouble when booting without the disk conncted.

You know, I believe that would be the easiest solution.  That way it wouldn't even mess with my windows installation at all.  I plan once I get use to Ubuntu to switch permanently.  I just need to learn some of the programs and become fluent in them.  There are some great replacements for programs that are very similar to what I use.  ex. GNUcash, xmms, Gimp, ect...... 

I went into my Bios and looked in the Boot section.  I have an option to boot from removable media.
There is a list to choose from such as USB FDD and USB ZIP..... I **didn't** see one that said USB HDD.
Does that mater ? Can I just choose any of the USB's and it will boot from it once Ubuntu is installed and ready?

---

### Post by Orbital75 on 2007-07-11
If I do get one of these working, How would I install Ubuntu to the drive?  

Would I plug the drive in first
Run the Live CD
Install the Live CD to what ever it see it as?
Then go into the Bios and tell it to Boot from the USB?

---

### Post by annda on 2007-07-11
> **Orbital75 said:**
> If I do get one of these working, How would I install Ubuntu to the drive?  

Would I plug the drive in first
Run the Live CD
Install the Live CD to what ever it see it as?
Then go into the Bios and tell it to Boot from the USB?

exactly. just make sure you install GRUB on the external drive as well (you will be asked about it during installation) - this is important! otherwise you won't be able to boot when the disk is disconnected: GRUB will complain about a missing partition.

---

### Post by Orbital75 on 2007-07-11
Thank you.......  I'll prob attempt it this weekend.....  :-)

---

