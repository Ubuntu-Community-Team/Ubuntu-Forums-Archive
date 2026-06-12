---
title: "BLACK screen of death on boot"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by jakc on 2007-02-20
my sata drive installation has fallen over at first hurdle.

Currently have one 250GB sata which was workin fine with xp on it. Just put in a 2nd 750gb sata plugged it in, booted up, got through BIOS but didnt seem to register it, got to windows screen, then hung for a bit and then restarted, only 2nd time it only got to a black screen.

Whats up? Everything seems to be connected inside, ive now taken the 2nd 750 drive out and still no joy.

Help, i need my computer for my job and want to get ubuntu on 2nd drive

---

### Post by GameManK on 2007-02-20
(random guess)
Are you sure you didn't plug it in somewhere where it's trying to make it into a RAID array?

And, of course, are you sure you plugged in both cables? ;)

---

### Post by jakc on 2007-02-20
i dont even know what that means, i just plugged it into the sata 2 port

---

### Post by dwblas on 2007-02-20
Try booting from the live CD or Knoppix.  If everything goes O.K. see if you can mount the drive.  That will tell you if the drive is the problem or something else.

---

### Post by Velotix on 2007-02-20
Supposedly Windows doesn't like SATA drives very much. D:

A quick bit of info on RAID arrays: they allow multiple hard drives to be detected as one huge hard drive, like partitioning in reverse. Supposedly because you have multiple hard drives running at once it significantly improves the read/write access speeds.

Anywho, you weren't quite clear in your post, which understandably was made in a rush: were you just trying to plug in the drive and see if it worked, and it didn't?

As was suggested earlier, you may have had RAID support enabled on your motherboard without even realising it, and getting RAID to work properly is very difficult. Try searching around in your BIOS for an option to enable/disable RAID support, turn it off and see if the computer continues to boot.

There is of course the possibility that when you added the second hard drive Windows tried to update its MBR - if it had tried to make the drives a RAID drive then it's essentially merged the two drives, so now you've taken out the second drive three-quarters of that drive is absent and it's going to hate that! XP

I really hope you backed up everything before trying this one. Anyway, if you have a Windows install CD lying around, there's a tool on it that allows you to fix the master boot record, which is probably what you need to do - this sounds very familiar to a problem that I once had, though at the time I was clueless as to the solution.

I take it that now, the BIOS runs, does all its checks, and then should hand things over to Windows - and at that point the screen goes black and stays black? If so, then Windows nuked its own MBR. Lousy Windows.

**EDIT:** If you fix the MBR, make sure the second drive's plugged in, or you'll probably screw Windows up again the next time you plug it in. It shouldn't be doing this at all, but that's Windows for ya! :P

---

### Post by GameManK on 2007-02-20
> **jakc said:**
> got through BIOS but didnt seem to register it

I think that's the important part here.  It is not detected in BIOS?  If you go to the CMOS settings, it doesn't show up anywhere (assuming it has a listing that lists the other drive)?

---

