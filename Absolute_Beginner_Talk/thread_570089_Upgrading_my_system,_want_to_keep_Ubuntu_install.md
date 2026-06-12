---
title: "Upgrading my system, want to keep Ubuntu install"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by limberlegs on 2007-10-07
Hi, all.

My apologies if this is a really stupid question.  I'm going to be upgrading my CPU, motherboard, and RAM on my desktop (yay!).  I'm presently running Ubuntu Gutsy, and I'd like to keep that install.  Will the replacement of these parts affect that in any way?  I'm keeping the hard drive, so my first guess is that it wouldn't, but I've never done a serious upgrade like this before, so I thought I'd ask before doing something stupid.

Thanks for your help!

---

### Post by Sayers on 2007-10-07
Your going to want to do a new install

---

### Post by limberlegs on 2007-10-07
Really?! That sucks.  Luckily I just did a fresh install and have most of my stuff backed up already.

Is there no way around this?  What would happen if I just set everything up and tried it?  I guess Ubuntu would freak out because all the hardware would be different?

---

### Post by oilchangeguy on 2007-10-07
> **limberlegs said:**
> Really?! That sucks.  Luckily I just did a fresh install and have most of my stuff backed up already.

Is there no way around this?  What would happen if I just set everything up and tried it?  I guess Ubuntu would freak out because all the hardware would be different?

i've not tried a true upgrade of a computer. but have taken the hard drive from one and placed it in another (so this should be almost the same thing) and after windows (not tried with ubuntu) went thru the found new hardware (quite a few times) it worked. the same should be true with linux.

---

### Post by julian67 on 2007-10-07
It might work fine. Linux detects the hardware on boot and loads the right modules so there's a good chance it will go smoothly. You will have problems if you have compiled drivers such as nvidia or ati and you are switching processor types like from intel to amd or from 32 to 64 bit. I set up Edubuntu LTSP on a desktop for someone and he later cloned the drive onto his laptop. The only thing that didn't work was the 3d acclerated graphics, but he had 2d no problem. 
But the most important thing is to back up your data before you begin and then it's safe to try anything.

---

### Post by limberlegs on 2007-10-07
Thanks for all of the tips!  As I said, I will definitely back things up.  I do have a nVidia card that requires extra drivers, and I am switching from Intel to AMD, so thanks for the warning.  There should be no reason to worry, right?  The worst thing that could happen is I'll have to do a fresh install? (right?)

---

### Post by julian67 on 2007-10-08
> **limberlegs said:**
> Thanks for all of the tips!  As I said, I will definitely back things up.  I do have a nVidia card that requires extra drivers, and I am switching from Intel to AMD, so thanks for the warning.  There should be no reason to worry, right?  The worst thing that could happen is I'll have to do a fresh install? (right?)

Yes. It should be very unexciting. Good luck :)

---

### Post by hyper_ch on 2007-10-08
Oh well, you could to the following:

(1) Backup your /home folder or if you have it on a seperate partition then it's good

(2) Generate your list of installed packages:

```

ls -1 /var/lib/dpkg/info/*.list|sed 's/.*\///;s/\.list$//'

```
Thx goes to *sysdef* from the German Ubntu channels on irc.freenode.org

(3) Install a fesh gutsy with a seperate home (and mount it if you have it already on a seperate home or copy it back)

(4) install those packages from the list that you got from step 2

---

### Post by limberlegs on 2007-10-10
Sweet! this is great.  Thanks to all for the suggestions!  New gear comes tomorrow!

---

