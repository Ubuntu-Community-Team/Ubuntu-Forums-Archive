---
title: "Dual boot system, install fresh ubuntu questions"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by FreewareFan on 2008-03-27
I have spent quite some time reading old posts about doing a fresh install of Ubuntu, on a system that already dual boots.  I could not find any clear-cut, concrete answers, so I'm posting this thread...  

I already have WinXP and Gutsy installed, and dual booting fine.  This is my first experience with linux, and over the last few weeks, I have managed to really clutter up my installation of Gutsy.  So, what I want to do is to make a fresh install of Ubuntu, and still keep my WinXp ( for graphic reasons). I have just one HD, which has a partition for WinXP, and three partitions for Ubuntu( root, home, and swap).   

Here is my question:  What is the absolute proven way to do this?  I simply cannot chance doing anything that will mess up my WinXP system.  

I have read where it would be best to just delete the partitions that Ubuntu now use, then use the WinXP repair function and do a fixmbr to get things back to square one.  Then do the install of Ubuntu, just like I did the first time.

I have also read where I can just delete the old Ubuntu partitions, make new partions, and install Ubuntu.  In that installation process, the Grub will still recognize that I have WinXP on another partition, and will include that entry in the menu.ls ( or whatever) file.

What I would like to hear, is from someone who has actually done this, and what method is sure to work.  I would rather not hear opinions from someone who has heard from someone else, and it worked for their friend...  lol   What I'm looking for here is advice from people with firsthand experience.

Thanks much for anyone who can advise me on this!

FwF

---

### Post by kesman on 2008-03-27
I would simply put in the livecd and run the installer normally and when it asks about partitioning, set it to manual and check the boxes that format the partitions that contain Ubuntu. It then first formats those partitions and installs a fresh install. Also Grub is reinstalled, and windows will be detected.

Note that it prompts you if you want to install Grub or not. **In this part you may ensure that it really has noticed the precense of your windows installation.** If not, you might need to manually first restore the windows's default bootloader with fixmbr.

EDIT:**This really is the way I've done this couple of times, always worked.**

---

### Post by louieb on 2008-03-27
> **kesman said:**
> ...This really is the way I've done this couple of times, always worked**.**


:guitar:+1 - Thats the way I do it too. Haven't had a problem yet.

---

