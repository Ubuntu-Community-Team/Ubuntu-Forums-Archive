---
title: "Warning - noob cannot install Linux"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Bowtie001 on 2007-03-21
OK everyone - sorry for being an idiot ahead of time.  I am generally pretty computer literate, but this is my first venture into a non-MS environment.  I am trying to install Ubuntu on a new partition of my one hard drive machine (Shuttle PC with athlon 3300 and 512 mb RAM older ATI radeon 9200 (or something like that)).  Here is generally how it went:
Booted from LiveCD.  Waited - waited - waited some more.  Nothing but a blank yellow screen for around 15 minutes.  Turned her off, booted again... same thing.  OK
Booted from LiveCD into safe graphics mode OK there it is.  Nice.

Dbl click install, go through the motions, choose new partition, click OK, walk away to go talk with the wife.  Come back half hour later it's at 27%.  Hmm, that seems slow... oh well.  Walk away again for 15-25 min, come back and it;s at 27%.  ARGG!

Turn it off, reboot.  whoops, It can't reboot because it partially created the new partition and is now trying to boot to it.  Cannot boot using the HD anymore, so I boot into Ubuntu (whoops, only the safe mode version) from the LiveCD, and try to install again, but I can't remember which partition is the new one and which contains all of the other stuff that I want to keep.. ARGG!

Go into the Ubuntu partitioner, give the 'boot' preference back to the original partition.  Reboot into XP, Here's a Blue Screen of Death for you.  Excellent!

Reboot back into XP and now it seems to be working properly.

So what did I screw up and how do I install it properly... was I merely impatient?  How long will it take to partition a 80Gb hard drive?

Frustrated

---

### Post by Obor on 2007-03-21
Usually ubuntu installs pretty quick so I don't think you were too inpatient. I would personally try to install from the alternate disk if you are having problem with the live cd... it seems to work better for some people.

---

### Post by mac.ryan on 2007-03-21
Hi,

   Preliminary questions, what version of ubuntu are you trying to install? What release (Dapper, Edgy...)? What installation CD (i386, AMD, other...)? Did you check the ISO image of the file you downloaded, and did you performed the CD test that is available on the starting screen of the Live CD?

> **Bowtie001 said:**
> Turn it off, reboot.  whoops, It can't reboot because it partially created the new partition  ....  Go into the Ubuntu partitioner, give the 'boot' preference back to the original partition.

It seems to me that the partitioning process might have gone more complex that required... If I understand, you have a primary master 80 Gb HD on which you have Window$ installed, and would like to achieve dual boot. In order to do this, normally ubuntu "shrinks" the win partition and created necessary additional partitions by itself (although you might intervene in order to achieve more complex/personalised configurations...).

AFAIK (but I am not a linux guru), ubuntu does not change what partition to boot from, but it simply install grub (the programme allowing you to choose what OS to boot in at the very beginning of the standard booting point.

As grub is installed at the very end of ubuntu installation, a broken installation should normally not interfere at all with the booting process (I am saying this, because if you experienced problems it might not depend from ubuntu...)

> Reboot into XP, Here's a Blue Screen of Death for you.  Excellent!

This is normal if you resized with gparted (ubuntu) the NTFS of windows: windows "understand" something has changed, and need to verify everything is still ok... It should be a one-time only operation, though.

> So what did I screw up and how do I install it properly... was I merely impatient?  How long will it take to partition a 80Gb hard drive?

On a system like yours I would guess the entire installation of ubuntu would take about 30 minutes, the partitioning/formatting should take about 1-2 minutes.

My suggestion is to:
[LIST=1]
[*]Check the CD for errors (see above)
[*]Install ubuntu in a as much standard configuration as you can: when time for partitioning comes, just delete all those created in the first installation attempt, then select "use largest space on disk..." and let ubuntu create partitions the way he likes.
[*]See what happens.[/LIST]My only concern is that if you have an issue with your graphic card during the installation, the same issue might be still there once the installation will be completed...

---

### Post by Bowtie001 on 2007-03-21
OK, more stupid questions... if I were to try the alternate CD, where might I find it?
Thanks

---

### Post by mac.ryan on 2007-03-21
> **Bowtie001 said:**
> OK, more stupid questions... if I were to try the alternate CD, where might I find it?
Thanks

[http://www.ubuntu.com/GetUbuntu/downloadmirrors](http://www.ubuntu.com/GetUbuntu/downloadmirrors)

---

### Post by Bowtie001 on 2007-03-21
Sorry, I replied before I saw the second answer.

Yes, I am trying to dual boot Edgy Efft.  I used "standard" as the option, because I don't have an Athlon 64 or anything.  I performed the CD checksum and it came out OK.

When I partitioned the drive, I let Ubuntu size it and left it at its default setting.  Is that different from using the largest space available?  I am not sure of the different options as of now.

As far as the video card, I was hoping that once it was installed I could get the correct drivers downloaded.  I may be optimistic, but let's get it installed first and I'll have to see then.

Thanks

---

### Post by Sef on 2007-03-21
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/") to install using the alternate cd.

> OK, more stupid questions

All your questions have been intelligent.

---

### Post by mac.ryan on 2007-03-21
> **Bowtie001 said:**
> When I partitioned the drive, I let Ubuntu size it and left it at its default setting.  Is that different from using the largest space available?

No, not really... what I meant is that choosing type, size, position, and mounting point of the various partitions can be a source of problems, so I wanted to get rid of it during the test installation.... any automatic option of ubuntu should just run fine.

I have no direct experience, but recently I read of people (using a laptop, though) who had their systems working under Dapper but not working under Edgy... Unless you solve your problems anyway else, you might wish to try Dapper (that comes with long term support) as an alternative.

Sorry I can't help more... :(

---

### Post by Bowtie001 on 2007-03-21
I appreciate all of the help given - hopefully tomorrow evening I can play again for a bit and I'll get this settled.  I am trying to say goodbye to windows before Vista becomes mandatory.  You've all helped me do that.  It's appreciated.
-Brian

---

### Post by Bowtie001 on 2007-03-22
So I tried again tonight.  The LiveCD would not boot first time, so I dove into the alternate installation.  I went on and on all the way through the partition maker.  I at first used the old partition that Ubuntu created last time and just rewrote it while leaving the Windows one.  I kept on going only to get caught by the "selecting and installling software" or whatever step.  It got stuck at 6% and told me that it got stuck, so I deleted all other partitions and let it put everything in a brand new one and went through the steps about the same way and got the same result.  Then of course, I deleted the partition, booted several time until the LiveCD worked and changed the Windows partition to 'boot' flag, because for some reason Ubuntu keeps taking the boot preference even when I clearly terminate the installation properly.

So I have to add another variable that I just thought of.  When I built the Shuttle a year or so ago, it used (forgive me if I get the acronym wrong) SATA instead of the older hard drive format (the little plug instead of the older big one) but I didn't have that type of drive, so I just plugged into the optical cable.

AND... I had issues with the original windows installation on this same hard drive in another PC, and I reused it even though I probably shouldn't have.  Is clearly spins up and down a lot for little or no reason.  But the current windows installation has no issues.

Those things may be red herrings - I'll let better minds figure that part out.

This is beginning to be more trouble than it is worth, but I do have a spare 'old style' hard drive to try but it means work.

Any ideas??

Thanks
-Brian

---

### Post by euler_fan on 2007-03-22
I had a machine do that to me (an older one and I was trying to install 6.06, so . . . ) and a clean re-install of windows followed by using the live CD worked fine. Not sure why the problem magically disappeared, but it did.

I know a re-install of windows is a real pain, but depending on how long it has been since you last re-installed, it may be worth it for windows-related reasons as well as easing dual boot.

Hope that helps.

---

### Post by Bowtie001 on 2007-03-26
OK everyone, you will all undoubtedly be glad to hear that Ubuntu is presently installed on my system.  One more liveCD that wouldn't boot and one alt CD that had a bad checksum, that's four CDs total if you're keeping score at home.  I also used the backup hard drive that wasn't having problems.  Now I still have to get XP installed and figure out the dual booting thing so I can put my computer back together (not enough ports to run two hard drives, have to hack it together).  I also have to figure out how to run things and get Beryl to work.  

Wish me luck - I am sure it will be an interesting journey to linux-hood.

-Brian

---

### Post by seshomaru samma on 2007-03-26
[this]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")  and  [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") 
might be of help

good luck

---

### Post by mac.ryan on 2007-03-26
And in case of troubles (wish you not!), [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") has a pletora of option for making the dual boot work...

Best luck! :)

---

### Post by glotz on 2007-03-26
You've sure had your share of problems! Welcome to the light side! And to the forums.

---

### Post by Bowtie001 on 2007-03-28
Thanks to all for the responses.  I have Edgy and Beryl installed now, and it's great.  I have a few outstanding issues to take care of before it can totally take over:

Firefox is slow.  I've tried lots of speed up tricks in about:config found here to no real avail

I have a VGA cable hooked to my digital monitor.  I have the latest driver and everything, I just cannot figure out how to get Ubuntu to use the DVI.

I really need to figure out how to get a good media player that doesn't suck... there are too many to choose from.

Other than that and a few other minor things, I am there.

Thanks again
-Brian

---

### Post by glotz on 2007-03-28
Here's some explanation on the Firefox connection settings
Firefox Tuning
[http://forums.mozillazine.org/viewtopic.php?t=53650](http://forums.mozillazine.org/viewtopic.php?t=53650)
Summary of the thread above
[http://216.239.59.104/search?q=cache:http%3A//www.tweakfactor.com/articles/tweaks/firefoxtweak/4.html](http://216.239.59.104/search?q=cache:http%3A//www.tweakfactor.com/articles/tweaks/firefoxtweak/4.html)

---

### Post by arbulus on 2007-03-28
I'm glad you were able to finally get your system going. 


A media player that I enjoy is Songbird.  It was built by some folk from the Mozilla team. It's currently only in development, but it's actually a really sound (great pun, eh?) music player.  You can download it right from their website.  I believe that it can play pretty much any format and also has great tools for browsing the web in search of music, and a great list of extensions that are set for release soon.  It can also sync your iPod, if you have one.

---

