---
title: "New install of Xbuntu on laptop won't load"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by chrish670 on 2007-02-13
Hi all...  I'm new to Linux, and I selected Ubuntu on the recommendation of another person, over at Bleepingcomputer.com forums.  My system is a Toshiba Satellite that formerly had been running Windows ME.  It has a P3 770mhz CPU, 128 mg of ram, a 60GB harddrive, sound and graphics are on the motherboard, as are the 56k modem and ethernet. 

I downloaded the ISO for Ubunto 6.10 and burned a disk.  When I tried to install it nothing happened in safemode.  So I came back to these forums and found a post with a link for mini.iso  Downloaded that, and burned to a disk.  After a couple of hours, my installation is done, but when system reboots - I log in and provide my password only to be met with another prompt

 [login@self-[drivevolume#]:~$

Suddenly, I realize I have no idea how to get to a desktop or to get Xubuntu to load onto a desktop. I hope I don't have to do this everytime I want to use xubuntu.  Where do I go from here??

---

### Post by siucdude on 2007-02-13
ok here is what you need to do. first you have to look at what version you downloaded.

ubuntu has more then one.  most likely you have a live-cd.  if that is the case then need to load ubuntu and once in the open screen there will be a icon for install, follow the prompts and work your way thourh it.  hope this helps.  

let us know.

---

### Post by shadowboxer_k on 2007-02-13
i think you might have to use the alternate install CD if your live CD won't work.

 go where you downloaded the live CD image and look for the alternate version. it should be there. download it, put it on a cd and give it a go.
 an alternate install takes up a lot less memory than the other way, since it is text based only, and i'm pretty certain that this is your case, with 128MB RAM (my laptop has the same RAM and i had to use the alternate CD).

good luck. let us know how it went. :)

---

### Post by chrish670 on 2007-02-13
> **shadowboxer_k said:**
> i think you might have to use the alternate install CD if your live CD won't work.

 go where you downloaded the live CD image and look for the alternate version. it should be there. download it, put it on a cd and give it a go.
 an alternate install takes up a lot less memory than the other way, since it is text based only, and i'm pretty certain that this is your case, with 128MB RAM (my laptop has the same RAM and i had to use the alternate CD).

good luck. let us know how it went. :)
Thank you both for your replies.   I could not use the Live CD of Ubuntu 

Well, I'm back to square 1.  I had used the alternate CD to get to the point where I was when I first posted.  I got to poking around in the forum here - and found another post in the installation section recommending to type in "sudo aptitude install xubuntu-desktop"   that seemed to work for awhile.  Then it started to run into errors during installation of the various packages that had downloaded.  Now because I'm not root I'm locked out with a hanged installation.  On my screen is **" logd [1755]: Error occurred while writting to log file: no space left on device."  **  I've put 6 hours into getting my laptop to this point.

---

### Post by chrish670 on 2007-02-14
I don't exactly know what I did wrong yesterday, but as of 45 minutes ago, I got ubuntu desktop installed on my laptop.  Instead of taking several hours,  it took about 3.5 hours using the mini.ISO file I downloaded.  I had to re-burn it to a new disk.  The Alternate install CD I downloaded today didn't work. Despite the MD5sum's matching, and the disk integrity being good,  what should of been a 25 min install, hanged.  (cd drive or memory are suspect to me)

Here are some things that I believe made a difference.   

Yesterday,  I selected that I wanted to install Xubuntu to an existing fat32 partition. Thinking back on it now - this was probably an option you would select, if you had Win9x installed and didn't wish to lose that.   The download seemed like it took hours to complete, and once the software was installing (about 7:00 pm lastnight, ) all sorts of errors began to occur.  The last post I did contains the sum result of Yesterdays fiasco. 

Today, I selected to wipe out the existing fat32 partitions I created using a Windows 98 bootdisk, reformed them, and then elected to allow ubuntu to use EXT2 or 3.  This seemed to work out much better (since the harddrive contained no OS.)  In a little over 3 hours, the installation completed.  :guitar:  I am now an official ubuntu user.  

The moral of this post is:  Make sure you understand the options being presented to you during set up.  Make sure you're using the right method to install Linux - based on the configuration of your hardware . And finally, to keep in mind that Linux is nothing like the Windows family of OSes.

---

### Post by Maestro23 on 2007-02-14
Glad to hear you got it installed man.  You are right about switching from Windows to Linux:" You must unlearn what you learned"  That is one of the biggest problem I see on the boards from new users.

Welcome to the community man.:)

---

### Post by chrish670 on 2007-02-14
I know Windows up to XP like the back of my hand.  I'm too used to getting around the problems  Uncle Bill and his merry band of $$$ grubbing (expletives... chose one you like best) in Redmond have created for the Masses.  In Fact Vista scares the *$&# out of me. 

Absolutely nothing prepared me for Linux.  I'm really happy and very impressed with it thus far. Thanks for the welcome to the community.

---

