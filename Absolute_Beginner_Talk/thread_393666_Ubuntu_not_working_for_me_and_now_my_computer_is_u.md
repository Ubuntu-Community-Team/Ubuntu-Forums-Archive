---
title: "Ubuntu not working for me and now my computer is unusable"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by dwightschrute on 2007-03-26
I recently got an Acer 3680 notebook computer which came with windows XP.  I mostly just goofed around with the laptop so nothing on it was very important.  I had considered trying linux on it because I heard good things about it, but never did.  However, after seeing a video on the web showing off ubuntu, I was impressed and figured what the heck lets give it a try.  This was the decision that made the next few days of my computer usage pretty miserable.

Anyways, when Acer ships out their laptops, they divide the hard drive into 3 partitions.  There is a 5 gb or so (hidden) partition for a restore, and then the remainder of your HDD is split in half.  One half has the OS installed on it, and the other half is supposedly for saving your own data or whatever you want to use it for (in reality it is just extremely annoying as I would have rather of had it all lumped together and I don't appreciate them splitting my hard drive in half on my behalf when I don't want it to be).

So when I went to install ubuntu, I basically just bit the bullet and removed those two main partitions and installed it on one big partition (and one small one for the swap file).  This can be referred to as mistake #1.

Once I got ubuntu installed, it was not and nice and easy as all those videos made it out to be.  My wireless network card didn't work, my sound didn't work, and I had errors all the time with an assortment of other things.  Also, installing drivers was extremely complicated, and after spending about 2 days trying to figure it out, I realized it was not worth it as everything seemed too problematic.

As an aside, one step in making it "more human" would be to make drivers much easier to install.  This whole idea of opening terminal and typing commands and assembling packages or whatever the heck it is is not easy and every time I followed any sort of readme file I wound up getting one error or another.  This sort of thing is not going to appeal to anyone outside of the realm of highly computer literate which sort of defeats the purpose.

Anyways, to make a long story short I wanted to get my computer back to how it was before.  I figured all I'd have to do would be run the recovery partition that was on my HDD.  Unfortunately, Acer is not the best company and the recovery tool (from what I can gather based on the problems that occurred) just tries to recopy your files like they were when it was shipped.  Since my partitions were all different and the filesystems on them were different, it didn't know what the heck to do.  Not much of a recovery program if you ask me.

So I deleted the new partitions and tried to run it.  It started to actually install, so I thought maybe it was working.  However, whatever it did didn't work.  Also, I kept getting GRUB errors (error 22) which from what I gather is a reminant from deleting ubuntu.

So ubuntu changed the boot sector on my HDD, which apparently the recovery discs do not bother with.  I am upset that Acer did not make a better recovery tool and I'm also upset that ubuntu would change so much on my computer without my knowledge (yes, in a way it is to be expected, but I am just irritated by the whole "its so easy" approach that is thrown at you when it is in fact not and does just as much hidden BS as the "enemy" microsoft).

Anyways, if anyone has any thoughts on what to do, let me know.  I know I'll probably have to send it to Acer and have them reimage it, but that is just gonna be one big headache. My theory is that the recovery is adding the proper files, but since the boot sector is screwy, it doesn't know what to boot.

Any help would be appreciated, and I wish I didn't type so much so sorry about that.

---

### Post by cowlip on 2007-03-26
To fix the boot sector, get a Windows recovery floppy that you can find from google, and boot it up .  Make sure your BIOS is set to boot from a floppy disk (aka, put it above the hard disks in the boot sequence).  Then you can type in "fdisk /mbr" or "fixmbr" to restore the Windows boot sector.  All the Grub error means is that the grub.conf or menu.1st file isn't found, which is true because you've erased Ubuntu's files.

Or, do the Acer restore cds allow you to press "CTRL + C" to escape out of their prompt?  Then you could run fixmbr or fdisk /mbr from that cd.  i think it's awful that OEMs don't ship the actual operating system cd anymore.

I'm sorry Ubuntu didn't work out for you; closed, proprietary drivers have loads of problems so it's no surprise I guess.  Open drivers automatically come with Ubuntu, but if hardware manufacturer's either don't open their driver specs, or don't write open drivers, then it can be hard to get working.  However, if you installed an original CD version of Windows XP--not your OEMs recovery disk-- onto your laptop, you would probably have the same driver problems as in Linux.

The Ubuntu laptop testing team shows you what problems people had with laptops and what worked, here, maybe you could add your experience: [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam) [https://wiki.ubuntu.com/LaptopTesting](https://wiki.ubuntu.com/LaptopTesting) I have done some quick searches of your laptop on this forum and it seems some people have gotten things to work, but of course it may have required ndiswrapper..

---

### Post by freebird54 on 2007-03-26
Sorry about your experiences.  I find that the newer your system is, the more likely you are to run into a driver issue - and you got caught in the middle.  It normally takes a year or two to get p**d off with MS to switch - so most people find it pretty easy to switch... but that doesn't help you right now.

what you need to run is a recovery floppy from a friends system - in particular you need fixmbr (which 'fix'es the Master Boot Record.  If you don't have a floppy, the I guess a bootable CD is required.  I share your disbelief that their 'image' fix doesn't do this!

A Google search on fixmbr might come up with other scenarios of how to get it done, but I'm afraid I haven't tried to go back, and so I haven't done it enough to give more detail...

BTW - if the OS was VIsta, I think they changed the name of fixmbr to fixboot or something... check that if necessary!

Again - sorry your experience wasn't better.  Maybe try again when your hardware is 'more experienced'??  Bye for now..

---

### Post by NyteGeek on 2007-03-26
> **freebird54 said:**
> 
BTW - if the OS was VIsta, I think they changed the name of fixmbr to fixboot or something... check that if necessary!



Fixboot and fixmbr are separate programs with different functions.

---

### Post by freebird54 on 2007-03-26
Perhaps the new name is bootfix then.  I'm sure I saw it was renamed - but I have not tried Vista myself.

Do you know if Grub can be set to boot XP only?  From what I know of how it works, I doubt it - but it might not hurt to check... :)

---

### Post by dreadlord_chris on 2007-03-26
> **freebird54 said:**
> Do you know if Grub can be set to boot XP only?  From what I know of how it works, I doubt it - but it might not hurt to check... :)

Sure it can - just remove all other boot options from /boot/grub/menu.lst

problem is - that file's gotta exist for grub to know where boot images are...

---

### Post by freebird54 on 2007-03-26
Yeah - that's what I meant.  No way to tell it anything about chainloading... oh well.

---

