---
title: "Hangs, but CD not the problem."
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by bjstabio on 2007-11-04
Can someone please help me with this!??  I've downloaded & burned Gutsy, both live CD and the alternate CD, and they both hang almost immediatly.  Neither one gets to the point where I'm asked for any input.  I'm thinking this may be a problem other than the CDs.  I say this because I have a commercial 6.10 DVD that I've used before with no problem.  But now, sometimes it will hang on the bar moving back and forth across the screen.  If it does launch and I install it, on reboot it hangs almost immediatly.  I'm using Puppy Linux to write this, but if save my settings in Puppy and reboot, I get 'kernal panic".  Please help!!!

---

### Post by Crafty Kisses on 2007-11-04
First, let's start out with your specs.

---

### Post by Arthur Archnix on 2007-11-04
1. Check the md5 checksum of the cd you downloaded.
2. Burn the cd at the lowest possible setting.
3. Restore bios to default, then ensure that it is set to boot from cd
4. Run a check for errors on the cd when it boots.

For more detailed info, please read this [thread]("http://ubuntuforums.org/showthread.php?t=583007").

---

### Post by bjstabio on 2007-11-05
I truely am a newbie & don't know how to restore bios to default.  I've done everything else you suggested and its all ok.  I just checked the bios and there isn't a magic button to restore default settings.  How do I do that?

---

### Post by Arthur Archnix on 2007-11-05
It's different for each bios. On mine its in the first menu. I've never seen or heard of one that doesn't have a restore button, so just explore a little through it. If you can't find one, c'est la vie. 

Another thing that occurred to me is to try a different cd media, like a cd-r as opposed to a cd-rw or something. 

Lastly, you can always order an ubuntu 7.10 cd for [free]("https://shipit.ubuntu.com/login").

---

### Post by candtalan on 2007-11-05
It does look a bit like a problem might exist in the machine. The 6.10 cd used to work but now gives problems for example.

If you can get to one of the boot menu items on a CD (Puppy??) some give an option to do a RAM memory check - all such checks are worth considering. A similar item to check the CD from its booting menu will maybe verify the CD drive can still read well.
Above all, consider what your data backup circumstances are - ensure your important data is backed up away from the PC asap, until you know more about the problem if one exists.

PCs are complex bits of kit and on rare occasions, items like hard drives or power supplies can go bad, processors run hot (dust clogs vents) and get confused, microscopic electrical joints break etc and weird things can happen until you find what is going on.

Good luck.

---

### Post by Arthur Archnix on 2007-11-05
Sorry, I misread the original post and thought that the OP was saying his 6.1 cd worked fine but the new ones didn't. Thus, I thought the problem was probably media related.

Last post is good idea, RAM test. 

Also, you may want to open the case and ensure that all connections are seated securely.

A bios reset is still a good idea if you can find it.

If the RAM test comes back without any problems, try disconnecting the hard-drive and then booting the live cd. Just to rule out hard-drive problems.

---

### Post by bjstabio on 2007-11-11
I looked again and found the bios reset on the exit page.  It worked.  Thanks to all who helped!

---

