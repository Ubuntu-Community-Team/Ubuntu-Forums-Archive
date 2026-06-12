---
title: "[SOLVED] Installation failed?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by Phjil on 2008-03-26
Hello again.

Although I thought I'd solved all my issues (thanks for your help this morning chaps!) it seems all it not well.

After re-installing from the Cd once more, I'm now getting this message on startup

Grub Loading stage1.5.

GRUB Loading, please wait...
Error 15



And then everything stops. I've tried reloading the system without a bootloader... tried installing 6.10,  7.10, 8.04... and get the same thing every time.
is it broken?
Should I install windows over the top of this mess and start again?

---

### Post by thane1 on 2008-03-26
Ubuntu 7.10 Gutsy is a stable OS, but the new Hardy Heron is not yet (although from what I gather it should be in April).  I think you'll be happy with 7.10.  However from your post am I to understand, that you're installing or thinking of installing Windows after installing linux?  The normal way to install it is to install Windows first and then install Ubuntu.  Usually Ubuntu will pick up the Windows instl'n and give you a nice dual boot screen on startup.  Error 15 is for File Not Found, but other than identifying this, I've no idea, what file Ubuntu may be looking for. Possibly your cd is defective.  Did you burn an iso?   Cheers.

---

### Post by Phjil on 2008-03-26
Hi,

No, I don't want to install Windows at all... I'm trying to get rid of Windows! I did an install yesterday which went a bit wrong, but a fresh install seemed to fix it, but after a software update, my video driver went mad with something... so I thought a fresh install would solve it.

I load the LiveCD, run the Installer, and it's all good.

Reboot.

Error 15!

Every time. I'll be happy to have a working version of 7.10...

---

### Post by spiderbatdad on 2008-03-26
Hi. read your post from this morning. Not sure what to make of your issue. Could you post some specs of you computer and/or model. 

The CD you say was from a magazine. It was obviously not the latest updated version of 7.10, as you had so many update to go through, and probably a kernel upgrade as well.

I would recommend the latest Hardy Beta release, providing your system meets the minimum specs.
Download the image and burn your own ISO slowly.
[http://www.ubuntu.com/testing/hardy/beta](http://www.ubuntu.com/testing/hardy/beta)

[http://blogs.zdnet.com/hardware/?p=1570](http://blogs.zdnet.com/hardware/?p=1570)

---

### Post by SunnyRabbiera on 2008-03-26
its possible its a bad disk, I suggest you burn your own.
Sometimes those disks in the magazines get damaged

---

### Post by saratchandra on 2008-03-26
I had the same problem while installing gutsy, I followed the instructions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

Grub installed properly after that. I used alternate install CD for gutsy, so it was easy for me.

---

### Post by Phjil on 2008-03-27
Hello again,

My computer is an HP Pavillion Ze4100s
20Gb HF 1Gb RAM 1.6Ghz Intel

It's old, but until I started fiddling with the OS, extreemly reliable - nothing failed in five years of owning it.

The cover disk from the magazine was December's issue of Linux User (UK magazine)... so there's probably lots of updates since then.

I have an ISO of Hardy 8.04 that I downloaded yesterday, but I ran a diagnostic on the liveCD and it comes up with errors.

Hmm... I shall keep plodding on.

Many thanks
Phjil

---

### Post by rkd on 2008-03-27
Without knowing more details about exactly what you did on the reinstall, it's impossible to tell what happened to cause your problem.  All I can do is give some suggestions that might cover some of the mistakes you might have made.

As some of the others suggested, it probably would be better to download and burn your own CD.  If you aren't certain how to do that, there is a pretty good description here:

    [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

You said you had downloaded 8.04.  That version is still in test, so I'd advise you to not to use it.  Use 7.10.  

I know you have installed already, but things have not gone quite right, so it might help to look at this guide to installing:

    [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The Check CD for defects part is important to be sure the CD has good copies of everything, so don't skip that.  Since you mentioned running a diagnostic on your Live CD and getting errors, it seems you know about this, but I wanted to be sure about that.

If there is any doubt about the install dealing with existing stuff on the drive, something you could do after booting the Ubuntu CD but before clicking the Install icon is open a Terminal session and run gparted:```
gksu gparted
```
In gparted, delete all of the partitions it shows you.  Remember to click Apply before quitting gparted -- it doesn't do the operations as you enter them, but saves them until you click Apply.  Once you have deleted all the partiitions, quit gparted, then click the Install icon on the desktop.  When it gets to the partitioning part, it should see an empty disk and there should be no chance of it getting confused with something already there, so it ought to get the Grub stuff set up properly.

As you do the install, make notes of what each screen shows and what you selected and entered, so that if it doesn't go right, you can tell us in detail what you did.  That will give us a better chance of figuring out what to tell you to do to fix it.

---

### Post by Phjil on 2008-03-27
It's good.


I used gparted to clean up all the partitions I had on there... did a fresh install from the 7.10 liveCD... updated - well that nearly worked, but the computer lost connection with the server at about update 299... but that's fine. I'm sure it can be picked up again.

Otherwise.. it's all going fine.
Cheers!
Phjil

---

