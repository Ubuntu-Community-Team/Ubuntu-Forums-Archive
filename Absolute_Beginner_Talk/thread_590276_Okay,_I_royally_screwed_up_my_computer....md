---
title: "Okay, I royally screwed up my computer..."
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by taco89 on 2007-10-24
Okay, before I begin let me say that I am a complete newb when it comes to OS and anything Network/Hardware/Firmware/etc. Having gotten that clear, I have a major problem.

After I burned Ubuntu 7.10 Gutsy Gibbon onto my CD and rebooted the computer, initiating the install sequence, I began to follow the installation course. I clicked Install, selected language, all that good stuff. But when it got to the point of Selecting if I wanted to partition my drive to a specific amount, do a complete wipe of the hard drive and install, or manually set things, I knew I wanted to partition. However I didn't know the amount to partition. Being the dummy I am, I clicked Forward and it began to partition, but I canceled it about 30 seconds in. Therefore I took out the CD, rebooted the computer, got back onto Windows XP and asked my friend about it. Deciding to go for around 25% partition, I put the CD back in, rebooted and began to repeat the process.

BUT, when I got to the stage where it asked me to partition, I no longer had the option of partitioning my drive to a certain percentage, only giving me the options of complete guided installation or manual. Yet, I clicked Forward before I noticed this (a bit too excited to get Ubuntu I suppose) and it started to go through with the entire installation. Taking quick action I canceled it about 15 seconds in. Now is where my problems become severe.

Deciding to just forget about Ubuntu for now, I take out the installation CD and reboot so I can go back to Windows XP. However, I am met with an unusual error (sorry, I don't recall exactly what it said) but I suppose it mentioned something about a file having been altered or deleted in some way. This kept me from starting up Windows XP. I tried pressing F11 for Help, but nothing happened, even with F lock on/off.

So with no way to get into Windows XP, I decided to go ahead and finish doing Ubuntu so I could at least get my Internet access back and try to recover my files. Not wanting to risk completely destroying everything (which I believe I may have anyway) I selected Custom Partition this time. Needless to say all the following technical mumbo jumbo came soon and I just blindly clicked my way through, making a new partition with the mount set to "/" and giving it a few gigs of space.

So when I finally get to my Ubuntu desktop, I don't have Internet access (even after I set up my account). I tried everything I could find in the Help files located on the computer and nothing worked. It just refuses to read the wireless signal from my Linksys router. Not only this, but I have no clue how to see anything that was on the Windows XP OS, if they are even still there, which I doubt.

And I type this as I gather my Windows XP CD's so I can reinstall Windows XP if need be and start from scratch, but I don't want to do that. I want my old files, the non-backed up ones (I know, bad move on my part). If there is any way to save my Windows section on my now Ubuntu controlled computer, please tell me. Thanks!

---

### Post by Onay on 2007-10-24
Well, I guess the moral of the story is this: Read what the installer says. My guess is that when you "blindly clicked" forward, you selected the option "use **entire** disk --", or in other words, format everything and make a new ubuntu install.

If you can give us the error from the windows install, we may be more successful. Did it say something like "NTLDR is missing" or "Partition Table Corrupt" or "No Operating System Found"? Some of these problems are fixable as long as you have the patience.

---

### Post by reza81 on 2007-10-24
this kind of thing you do once! 

I once deleted my whole windows system with fdisk 10 years ago... but I learned how to work with it & won't make the same misstake. 

If your dont sure of something, look it up or ask questions here. We will help you. 

Goodluck

---

### Post by Onay on 2007-10-24
> **reza81 said:**
> this kind of thing you do once! 

I once deleted my whole windows system with fdisk 10 years ago... but I learned how to work with it & won't make the same misstake. 

If your dont sure of something, look it up or ask questions here. We will help you. 

Goodluck

Me too :) . At least I have the experience to be able to help other people who this happened to. My problem was that my windows partition mounted in the middle of partitioning, what a mess. I could care less now, since I'm sick of windows, and my Gutsy install fulfills all of my needs and more.

---

### Post by taco89 on 2007-10-24
> **Onay said:**
> Well, I guess the moral of the story is this: Read what the installer says. My guess is that when you "blindly clicked" forward, you selected the option "use **entire** disk --", or in other words, format everything and make a new ubuntu install.

If you can give us the error from the windows install, we may be more successful. Did it say something like "NTLDR is missing" or "Partition Table Corrupt" or "No Operating System Found"? Some of these problems are fixable as long as you have the patience.

Now that you mention it, I believe it did say "NTLDR is missing". In fact, I believe it looked like this:

[IMG]http://www.evilape.biz/pics/NTLDR.jpg[/IMG]

The only exception being that I had "Press F11 for Help" above it.

Thanks for replying everyone, and I hope to resolve this without a complete re-installation.

And as said before, this will definitely be a mistake that only happens once ><


Bonus Note: I've never done anything with Linux and my stupidity hasn't eased me into a successful introduction.


[EDIT]

Okay, I decided to check my BIOS and see what it said. After rebooting, I went to both BIOS and Boot Menu and saw the same screen. The choices I have are:

> 
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+
Other operating systems
Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda1)
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda1)
Ubuntu 7.10, memtest86+ (on /dev/hda1)


Noticing that there is no Windows choice, I clicked "Other operating systems" and got this:

> 
Error 11: Unrecognized device string
Press any key to continue...


Any clues?

---

