---
title: "Ubuntu live CD and 680i Motherboard Problem"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by jestrange on 2007-11-28
Hey all.

First of all, thanks to the many posts regarding dual booting.  I did alot of searching and found some great information.

On to my problem:

I built my computer earlier this year (2007) and opted for the EVGA nForce 680i motherboard.  It has run excellent thus far.  I now want to dual boot Windows XP and Ubuntu;  I purchased an additional hard drive for this very purpose.  I downloaded and burned the Ubuntu live CD iso. 

Before installing my new hard drive, I was able to run the Ubuntu live CD and play around with the OS.  I had no problems at all and everything was great.  I was able to go on the internet, look at the system, etc.

I then installed my new hard drive and unhooked my old hard drive with Windows XP on it (my plan is to install on one hard drive, hook both up, and manually edit GRUB to include my XP drive). 

My computer passed POST fine.  However, after starting the boot process for the Ubuntu live CD, my motherboard started beeping continously.  I do not remember the number of beeps.  I looked inside and saw the error code '0E' on my motherboard, which according to my motherboard manual, the description of this error is 'Check the integrity of the ROM, BIOS and message'.  However, desipte the beeping, I was able to still boot into Ubuntu but with no mouse (I have a USB mouse) support (I was able to get the mouse to work after simply unplugging and replugging in the mouse).  After shutting down Ubuntu, the beeping returned until my computer powered down.

I then hooked up both drives and experienced the same issue as above, however with full mouse support this time.  I tried once more and did not receive the beeping until system shut down.

I know I should probably try again with just my Windows XP drive, however, I'm going to wait until I can explore this issue more.

I have yet to actually install Ubuntu and I'm still able to boot into Windows XP without any of the above issues.

My computer passes POST every time.  I've only experienced the beeping when loading up the Ubuntu live CD.  

1 - What would be the cause of the above issues?
2 - Has anyone here had similar issues?
3 - Has anyone successfully setup Ubuntu with the EVGA nForce 680i motherboard?

I appreciate you taking the time to read this post.  I'm interested to find out if this is a motherboard issue or a Linux issue.

Thanks!

Oh and if its helpful, my system specs:

Intel Core 2 Duo E6600
EVGA nForce 680i SLI (BIOS version: 25)
Corsair TWINX 2040MB DDR2 800MHz
EVGA GeForce 8800 GTS 640MB
Seagate SATA 320GB Hard Drive (2x now :))

Edit:  I guess it would help to know that I'm trying this with Ubuntu 7.10 (Gutsy).

---

### Post by njparton on 2007-12-10
Interesting... do you get beeping if you boot into windows with the new drive plugged in?

Is the drive faulty?  Have you tried plugging it into another SATA port? 

What are your SATA BIOS settings set to? Make sure nvidia SATA raid is turned off.  I have an EVGA 680i MB in my gaming PC and I know the onboard software raid has issues with the P30/P31 bios.

---

