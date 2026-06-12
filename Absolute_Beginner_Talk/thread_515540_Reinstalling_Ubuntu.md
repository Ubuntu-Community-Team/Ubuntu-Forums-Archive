---
title: "Reinstalling Ubuntu"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-08-02
Howdy!

I installed a dual-boot version of Ubuntu a few months ago, and since then have gradually succeeded in pretty much messing up my installed version to the point that I've decided to simply wipe the slate clean and start over from the beginning.  Being still very green in the ways of Ubuntu, I'm not sure how to go about doing that.

I assume I can start by using G partition from my original CD.  Do I need to  remove everything first or can I simply format over my original installation?

Thanks in advance for advice and help.

---

### Post by tashmooclam on 2007-08-02
I read here and there about emptying the trash, defragmenting the hard drive before doing an installation. 
I did this to XP Pro on this 5 year old compaq laptop. 
I then installed Ubuntu and it was fine.

---

### Post by charlesbrooking on 2007-08-02
If you run the Ubuntu installer and just select the same partition as last time, it will first format the partition and install over the top. Give it a go.

---

### Post by forestpixie on 2007-08-02
I assume that you are installing over your old Ubuntu installation - can I make a suggestion 

make a seperate /home partition then next time you'll just install the system to root and can keep your home folder

so you would need
/ for root
/home

and a swap

---

### Post by Mr. Svinlesha on 2007-08-02
forestpixie:

What are the advantages to doing it that way?

Can I follow charlesbrookings advice and just install over my previous installation?

---

### Post by forestpixie on 2007-08-02
yes of course you can just install over previous installations 

if you make a seperate /home folder - when you come to upgrade, or in the unlikely circumstance of having to reinstall because you've done something you shouldn't have (I reinstalled 3 times in 2 weeks :) ) you keep your old home folder with your docs etc and the reinstall doesn't affect them.

at the end of the day it's up to you :) _ i got fed up with having to put stuff back - this isn't though a reason not to have backups  ;)

---

### Post by Mr. Svinlesha on 2007-08-02
Right, so, I've gotten to the tricky part of the installation.  I've opened gparted and selected the option "Manually edit partition table".  Since I've done this before, the partions are already there.  But just to be sure I'd doing everything correctly, this is what I see:

/dev/hda1      NFTS                          78.13 Gib
/dev/hda2     extended                    70.91 Gib
        /dev/hda5       ext3                   9.77 Gib
        /dev/hda6       linux-swap         1.95 Gib
        /dev/hda7       ext3                 59.19 Gib   
unallocated                                       7.84 Mib


Now, if I hit the next button, and let gparted work, will I be correctly reinstalled after?

---

### Post by Mr. Svinlesha on 2007-08-02
Never mind the last post.  I've successfully reinstalled.

Thanks everyone for the help and advice.

---

### Post by forestpixie on 2007-08-02
excellent welcome back:)

---

