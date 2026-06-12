---
title: "Gutsy on VirtualPC - help on linux additions??"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by paradisebmk on 2007-11-10
Hi,

I haveGutsy installed on my PC as a VirtualPC guest machine--so far so good (but it really wasn't smooth because of stupid ATI graphics card).

I want to install virtual additions for linux but it downloads as a .msi (microsoft installer) file and I haven't a clue of what to do to get it to be an ISO  (if that's what I have to do)...as I mentioned I don't know where to go from here but I don't appear to be able to do anything with the .msi file.

It has to be run on the Gutsy guest machine. I can get the windows version ISO automatically onto my Gutsy guest machine desktop using the GUI provided but that doesn't do any good on linux...thanks Microsith. 

Does anyone know what to do to be able to install the additions for linux on a guest Gutsy linux machine? The forum posts give answers based on an ISO file and all I can find anywhere is the .msi download.

Any ideas would be greatly appreciated!!!!

---

### Post by P4man on 2007-11-11
I dont know virtualPC, but I would suspect you have to install the MSI on the windows host first.  MSI files are windows installables, they dont work in Linux. Then this would allow you to somehow install the additions on the client. 

I am doing the opposite running a Windows VM off an ubuntu/virtualbox host, to install windows additions, I have to click it in the VM menu, which then serves the windows VM with a virtual CD from which I can install the drivers and stuff in the VM. I suspect VirtualPC would use a similar approach.

---

### Post by Richard Hunt on 2007-11-20
Hello,

I am in the same boat but farther up the creek I think... (desperately looking for paddles)

This is my second and more successful foray into Ubuntu.  It is now installed and working well, with internet access, in Virtual PC 2007 running on Windows XP. It is slow, indeed slower without the VM Additions that VPC suggests. Also without the VM Additions, I cannot copy files across from the XP session to the Ubuntu VM or back.  However the VM Additions for Linux do not seem to be easy to install.  

I have downloaded the .msi file and run it under Windows.  It then installs, but you need to change the install directory to that of Virtual PC (in the Program files folder) not the Virtual Server directory it creates by default.  Once completed switch to VPC and Ubuntu and you can click on the VPC Action menu to activate the VM Additions.  They then appear as a virtual CD in Ubuntu but there seems no way to install them, particularly as they are not specifically written for Ubuntu.

However installation is a mystery and no one seems to have a really good beginner's guide to installing them.  It seems complicated as they are rpm files that apparently need to be converted to Debian format using something called Alien.

I found some guidance somewhere in these forums at ubuntuforums.org.showthread.php?t=43403.  You can Google on VM Additions in Ubuntu to come up with the full link.

I tried following the guidance but got as far as the first reboot and found Ubuntu would not, so had to re-install the VM.  I suspect it had something to do with the linux-headers bit which I shall omit if I try again.

It would be useful to have a step-by-step guide fur dummies, but always there seems to be some expected knowledge of how to use Linux.  For example I spent a long time searching for these files using Google.  If you use the Synaptic Package Manager you can simple click Edit > Search and enter the required name and it will find it and enable download and installation in one go.  Brilliant!

So if anyone else has any ideas, they will be gratefully received! [http://ubuntuforums.org/images/smilies/icon_smile.gif](http://ubuntuforums.org/images/smilies/icon_smile.gif)

---

### Post by P4man on 2007-11-20
> **Richard Hunt said:**
>  It seems complicated as they are rpm files

well, that of course is the problem. RPMs are packages for Red Hat and Fedora, converting them to  .deb packages needed for Debian/ubuntu/.; seems tricky at best. I didn't even know it was possible.

 If there are no other packaged extensions available for VirtualPC, I would seriously consider switching to Fedora Linux (which is basically the free Red Hat). It will look and act very similar to Ubuntu, and you should have no problems installing the VM extentions.

edit: of course, you could also consider doing the opposite, running XP in a VM under Ubuntu. It works quite well for me, as long as you don't need 3D acceleration or SMP support in Windows. It is also a  LOT faster than the opposite.

---

### Post by Richard Hunt on 2007-11-21
Thank you for your reply.  However, there must surely be someone who has done what we are trying to do and succeeded.  Your very plausible alternatives may work better but clearly require major surgery on the PC, and there is no guarantee at the end that my years of investment in Windows will be adequately maintained and work properly.  The risk is therefore too great.  I might be tempted sometime to try again with a dual boot configuration, but that went horribly wrong the first time I tried it and I was unable to connect to the internet in Ubuntu which defeated the purpose of trying.  It took 2 days of hard graft to restore my system afterwards.

So, I will try the guidelines again mentioned in my previous post and post the outcomes here.  Then I may try another distro (is that the word?  Curious.) as another VM.

---

### Post by P4man on 2007-11-21
> **Richard Hunt said:**
> Thank you for your reply.  However, there must surely be someone who has done what we are trying to do and succeeded.  

I've googled a bit for you, and I saw many miserably failed attempts. 

But in case you haven't seen this one, I won't stop you from trying this:
[http://ubuntuforums.org/showthread.php?t=434039](http://ubuntuforums.org/showthread.php?t=434039)

> Your very plausible alternatives may work better but clearly require major surgery on the PC, and there is no guarantee at the end that my years of investment in Windows will be adequately maintained and work properly.  

Yeah I hear you. Switching from Windows to Linux is not something you should do overnight if you use your machine for more than just browsing or email. I ran dual boot for 6 months.. actually, I still do, but now I don't boot windows more than once per week or so. But if the goal is to learn Linux, I'm not sure if running it in a VM is the best way.

>  I might be tempted sometime to try again with a dual boot configuration, but that went horribly wrong the first time I tried it and I was unable to connect to the internet in Ubuntu which defeated the purpose of trying.  It took 2 days of hard graft to restore my system afterwards.


Thats odd.. there should be no problem at all running both OSs in dual boot, but if you only have 1 harddisk, well, maybe you went wrong somewhere setting up the partitions? As for network not working, do you use wireless connection ? Best way to test if that works is just booting off the live CD. If it works there, it should work once installed. If it doesnt work on the live CD, it might take some trickery to get it working. What card do you have? 

> So, I will try the guidelines again mentioned in my previous post and post the outcomes here.  Then I may try another distro (is that the word?  Curious.) as another VM.


Yep, distro (or distribution) is the right word ;). As for another VM, I have no experience under windows, but I am very impressed with VirtualBox under linux, and they also have a windows version. Its free as well, and they do support Ubuntu as a client OS (and have native additions). Maybe giving that a try is the simplest way to proceed.  Check it out here:
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Richard Hunt on 2007-11-22
Thanks for your very positive reply.  I shall study your suggestions.  The link you mention is the one I am trying to follow.  

Yes, I am wireless, and had a chicken and egg situation under dual boot which, without networking, performed fine.  I obtained a new RALINK wireless USB card compatible with Linux as my USR one was, said USR, not compatible.  However the setup for Ubuntu required I perform Ubuntu system updates before installing the card (with a hard wire connection I do not have.) Hmm. Not easy.  So I tried to get it to work anyway and it ended corrupting Ubuntu, my hard disk and all (probably my own fault the latter).  Unpleasant.

However I have got it to work in the VM under Virtual PC.  I shall try your suggestion of using the live CD in the light of this experience.

I am still working on the VM additions. I took a look at Microsoft's Virtual Server 2005 yesterday but I think that is overkill and anyway it didn't work (Oh surprise!).  I'll take a look at VirtualBox.

It's a good thing I am retired and have PLENTY of time... :-)

7 hours later I have abandoned Virtual Server. I got it to work but it is really not a home/dekstop application.  I downloaded VirtualBox and have installed Ubuntu now.  It really is a) faster than Virtual PC b) easier and c) the Additions loaded beautifully after 88 system updates came down automatically.  To anyone trying Virtual PC still: Don't. VirtualBox does the biz.

---

### Post by Brian4 on 2008-01-05
I must wholeheartedly concur with Richard, above.  Ditch VirtualPC and go with VirtualBox! =)

I give thanks all the people who got me far enough in VPC to at least get something working, but I couldn't get past the problems with the screen resolutions.  First off - I am a newbie to Linux.  I came into the computing world with the Commodore 64, then the Amiga, then Windows XP.  I liked the liveCD of Ubuntu (it kinda reminded me of the Amiga), so I wanted to try it while continuing to use my normal install of Windows XP with all my current creature comforts while I possibly make the transition to full Linux..

I learned that VirtualPC used to be cross-platform until MS bought it - after which they only offered MS versions (hmm.. I wonder why).  After learning that and hearing of VirtualBox, I decided to give VirtualBox a try - after all I found that it is mostly open source under the GPL.

Installing Ubuntu with VirtualBox (as compared to VPC2007):
You do NOT have to worry about the graphics, nor the mouse, nor the networking, nor the screen resolution.  It ALL installs perfectly fine!  And to top matters off, I can also use the scroll wheel!!  And if THAT wasn't enough - it seems to run far, FAR faster than it did under VirtualPC - which is weird considering that it ran MS's Virtual server 2003 fairly fast.

Well, I'm convinced!  Now HERE is a situation in which I can learn Linux while still using XP with hardly any degradation is speed or functionality.  I also notice that VirtualBox seems to be MUCH more professional than VirtualPC - hands down.

---

