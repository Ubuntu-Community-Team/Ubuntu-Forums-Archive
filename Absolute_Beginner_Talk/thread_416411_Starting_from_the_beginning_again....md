---
title: "Starting from the beginning again..."
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by BrewsterPilot on 2007-04-21
Hi,
as I've been messing around with dual booting XP & Feisty, I've now managed to make XP completely inaccessible. That doesn't matter too much, since I've got copies of all my important files on USB memories. Now I believe time has come to leave XP completely; as I'm very happy with Ubuntu. So, my main problem is; where can I completely wipe out all that ever had with XP to do? I'd like to let Ubuntu use my entire hard drive, not just a part of it. Should I format everything (how?) and then just boot from the Feisty CD? 

Thanks,
BrewsterPilot

---

### Post by avik on 2007-04-21
Just reinstall Fiesty from the Live CD, and when it asks, tell it to use the entire hard drive.

No need to format; that'll be taken care of during installation.

You're making the right choice!

---

### Post by GSF1200S on 2007-04-21
> **BrewsterPilot said:**
> Hi,
as I've been messing around with dual booting XP & Feisty, I've now managed to make XP completely inaccessible. That doesn't matter too much, since I've got copies of all my important files on USB memories. Now I believe time has come to leave XP completely; as I'm very happy with Ubuntu. So, my main problem is; where can I completely wipe out all that ever had with XP to do? I'd like to let Ubuntu use my entire hard drive, not just a part of it. Should I format everything (how?) and then just boot from the Feisty CD? 

Thanks,
BrewsterPilot


You can use gparted to make the NTFS partition an EXT3 partition. If you do it this way, you wouldnt loose all your progress with Ubuntu. You can get gparted from the Synaptic Package Manager, or type:

sudo aptitude install gparted

or-

sudo apt-get install gparted

The top command may deal with dependencies a little better- I still dont know if this part is true...

I might ask if you are sure you cant boot windows? Is it that you cant select Windows from the grub menu or does it just freeze when trying to boot. I understand you love linux and all, but think twice about whether or not you may need windows application base..

---

### Post by BrewsterPilot on 2007-04-21
> **avik said:**
> Just reinstall Fiesty from the Live CD, and when it asks, tell it to use the entire hard drive.

No need to format; that'll be taken care of during installation.

You're making the right choice!

Thanks, worked perfectly!



> **GSF1200S said:**
> You can use gparted to make the NTFS partition an EXT3 partition. If you do it this way, you wouldnt loose all your progress with Ubuntu. You can get gparted from the Synaptic Package Manager, or type:

sudo aptitude install gparted

or-

sudo apt-get install gparted

The top command may deal with dependencies a little better- I still dont know if this part is true...

I might ask if you are sure you cant boot windows? Is it that you cant select Windows from the grub menu or does it just freeze when trying to boot. I understand you love linux and all, but think twice about whether or not you may need windows application base..

Hi, I hadn't yet flavored Ubuntu to my personal preference, so the complete format worked well in this case. I'll remember those commands if I need them later, thanks!
Why I can't boot Windows? Because it locks up at the welcome screen and you have to reboot, after which  it still won't work. System recovery the only way out. Not the first time this has happened though, I encountered it long before I ever heard of Ubuntu, and that's why I always keep backups...

I'm quite sure that I'll be perfectly happy with Linux; we've got it at school and so far works seamlessly. My current computer couldn't run many games anyway, and since Photoshop is rather expensive I've been using GIMP for some time now. Excellent program! We'll see about the future though, as I'll be building a new rig in July which will have no problems with games, so I'm probably going to switch back to dual-boot then. Really, that's the main feature IMO that holds Linux from becoming more popular, if it only would support more games.

-BrewsterPilot

---

### Post by GSF1200S on 2007-04-21
> **BrewsterPilot said:**
> Thanks, worked perfectly!





Hi, I hadn't yet flavored Ubuntu to my personal preference, so the complete format worked well in this case. I'll remember those commands if I need them later, thanks!
Why I can't boot Windows? Because it locks up at the welcome screen and you have to reboot, after which  it still won't work. System recovery the only way out. Not the first time this has happened though, I encountered it long before I ever heard of Ubuntu, and that's why I always keep backups...

I'm quite sure that I'll be perfectly happy with Linux; we've got it at school and so far works seamlessly. My current computer couldn't run many games anyway, and since Photoshop is rather expensive I've been using GIMP for some time now. Excellent program! We'll see about the future though, as I'll be building a new rig in July which will have no problems with games, so I'm probably going to switch back to dual-boot then. Really, that's the main feature IMO that holds Linux from becoming more popular, if it only would support more games.

-BrewsterPilot

Yeah, youre right.. Thats why im running a dual boot on my system. This is really the only reason Microsoft has stayed on top for so long, and the fact that theyve made themselves almost a requirement in the computer world.

I would suggest keeping WINE and Cedega in mind when you build your new rig. I was looking through the platinum and gold list for wine, and I cant believe how many bada__ games work! I will keep dual booting, but im thinking about trying to get Diablo 2 LOD and Battlefield 2 running under wine... then I would HARDLY EVER boot to windows (still dont anyways). I would love to see Fable on the Gold/Platinum list...

---

### Post by BrewsterPilot on 2007-04-21
Yup, been following those two applications closely. The games I'd like to get working are Silent Hunter III&IV, IL2 1946, BF2+Special Forces, and Storm of War : Battle of Britain (due to be released Christmas -07). If that succeeds Bill G can wave goodbye to me.

-BrewsterPilot

---

