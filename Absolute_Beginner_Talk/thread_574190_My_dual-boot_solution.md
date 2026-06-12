---
title: "My dual-boot solution"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by rock-hopper on 2007-10-12
Hello everyone.  I'm about to take the somewhat foolish step of teaching my grandmother to suck eggs and I don't suppose it will win me too many friends with the old hands here!

However, I am really quite pleased with what I have managed to do over the last few days (with a lot of help from the forum) and I would really like to help out anyone who might be thinking of installing Ubuntu as a dual-boot - the fact that it gives me a tiny opportunity to boast hasn't occurred to me! :lolflag:

All right - you have been using a live Ubuntu disk for a week or two and you like what you see.  It's time to dual-boot! :guitar:

The usual advice is to resize your Windows partition to accommodate Ubuntu and to select your Operating System from the GRUB menu at Start-up.  While this is a perfectly sound and tested way of going about things, I think a better, if more expensive solution is to install Ubuntu and GRUB on a separate Hard Disk Drive.

This is a very simple procedure and the low cost of Hard Disk Drives is a real incentive to go this way, and has the advantage of keeping your Operating Systems entirely separate - should one Disk die - and it does happen, I can tell you - it's happened to me - you'll have a working installation from which to start again, downloading .iso files and all the rest of the fun and games!  Of course, if they should both die at the same time.  :(

OK then.  Start up your computer and see if you can find an 'F' key to call up a Boot Menu.  If all else fails, read the fine manual!  On my machine, with an Asus mainboard, this is done by tapping the F8 key at Start-up, but this probably varies from PC to PC.  If you don't have this kind of access, you will have to use the BIOS directly, usually by tapping 'Delete', 'F2' or something or other.

Start your PC, insert the Ubuntu CD in the tray, close it and shut down.

Taking the necessary precautions about static charges, fit your new Hard Disk Drive into your case and disconnect the existing Hard Disk Drive.

Start your PC with the Ubuntu CD and wait for it to load completetly, then follow the installation procedure using the option to manually partition the Hard Disk Drive, setting up partitions for root "/", "swap" and "/home".  On my PC I used about 16 GB "root", 2 GB "swap" and the rest as "home".  This was on a 160 GB Maxtor SATA II Hard Disk Drive which cost £30 new from a local supplier - you could probably get a better deal on a well-known auction site.

There are a number of Screencasts by Alan Pope et al which cover this procedure in some detail and are well worth viewing.  Do a search for Ubuntu Screencasts if you would like to see them.

When the procedure is finished, eject the CD and shut down your PC.  Again taking appropriate precautions against static charge, reconnect your original Hard Disk Drive and start your PC, tapping the key to access the Boot Menu and selecting your Drive and its OS.  

You will find that you now have access to both Windows and Ubuntu and that you can browse your Windows folders in Ubuntu.  If you want to you can make these capable of being written to as well.

Congratulations - you now have a dual-boot Windows/Ubuntu machine with no GRUB/MBR problems!  :KS

Best regards,

rock-hopper.

---

### Post by Joeb454 on 2007-10-12
Or the cheaper way - the way I took:

Install Windows, then boot up the LiveCD. Open GParted, and partition the drives. Then Install Ubuntu using the Guided method to use the largest continuous free space, and then just let Grub choose, it's not hard to change the default boot option either, so you could even hide Ubuntu from other users :p

---

### Post by SteveHoffmanUK on 2007-10-12
For non-UK English speakers, a translation/explanation of Rock-hopper's first sentence from an American who lives in the UK:

The peculiar UK English expression "to teach your grandmother to suck eggs" means to give needless assistance or presume to offer advice to an expert. The first time someone said that to me here, my jaw dropped and I thought I must have misheard or lost my mind.:)

---

### Post by Pumalite on 2007-10-12
'Bringing coal to Newcastle' I like better.

---

### Post by chlorinekid on 2007-10-12
im pretty sure i just booted the live cd and double clicked install. ubuntu did the rest. it duel boots and it works. where's the hard part?

---

### Post by -grubby on 2007-10-12
> **rock-hopper said:**
> , I think a better, if more expensive solution is to install Ubuntu and GRUB on a separate Hard Disk Drive.


That is definatly easier. I usually do that if I have to set up a dual boot(I don't have any right now)

---

### Post by rbc on 2007-10-13
I've done the dual boot (same hard drive, different partitions) but wanted to try rock-hopper's method for the heck of it. i followed instructions, at least I thought I did, but when I tried to install, Gparted did not see the drive. Could someone be more specific about what needs to be done in BIOS?

---

### Post by rock-hopper on 2007-10-14
Hello rbc.

I'm sorry that your following my instructions didn't lead to success; I didn't experience any trouble with the Partition set-up using the Ubuntu Live Disk.  

I know this is crazy and probably insulting - it's not meant to be - are you sure you disconnected the right drive?

Is it possible you accidentally disconnected the new drive when exiting your case - I know things can be a bit cramped and I have accidentally uninstalled modems and floppies in the past!

Otherwise, I can only suggest you try again and ask someone with more experience than me if it doesn't work.

[COLOR="Blue"]That should teach me to keep my mouth firmly closed in the future :([/COLOR]

As the old saying has it:  'It is better to remain silent and be thought a foll than to speak and remove all doubt'.

Sorry again and better luck next time.

rock-hopper.

---

### Post by Pumalite on 2007-10-14
'It is better to remain silent and be thought a foll than to speak and remove all doubt'

No, it's better to be an ignorant one second, and wise the rest of your life.

---

### Post by Sbarton on 2007-10-14
Hi! rock-hopper, don't worry to much about winning friends, you seem to have made a genuine effort to help out and I am sure some folks may find your post helpful.
regards

---

### Post by rbc on 2007-10-15
There are obviously more serious issues to be solved but it's bugging the daylights out of me that I can't solve this. By the way rock-hopper, no offense taken. It's always good to check the basic first. Here's the situation now. The IDE ribbon has a connector for HDD1 and HDD2. I can get Gaprted to see the new drive if I connect it using the HDD1 connector. I thought maybe the ribbon is bad, so I tried a different one but same result. Do the jumper settings have something to do with it?For now, I only have one drive connected at any given time

---

### Post by usarmykr on 2007-10-15
> **Joeb454 said:**
> Or the cheaper way - the way I took:

Install Windows, then boot up the LiveCD. Open GParted, and partition the drives. Then Install Ubuntu using the Guided method to use the largest continuous free space, and then just let Grub choose, it's not hard to change the default boot option either, so you could even hide Ubuntu from other users :p

The easy way I thought I would take as well, until the bugged installer decided it would be best for me to delete all of my partitions instead of resize my windows partition.  I would recommend using a program in windows to resize your partition and them use the LiveCD to manually set up your partitions.  Much safer that way IMO or, just go through hell and completely drop your windows, and spend hours trying to get your games running in wine :D It ends up good though I promise, and linux > windows once you get it all set up.

---

### Post by rock-hopper on 2007-10-15
Hello again rbc. 

 I'm sorry you're still having problems and I'm pleased that you didn't take what I said the wrong way.  I honestly don't know how to solve your headaches as, when I did it, I was dealing with a (reasonably) new PC that had SATA drives; perhaps that's the answer, or perhaps another, more experienced member might be able to offer some more help.

I accept that I know little about computers and next to nothing about Linux but I was a little disappointed to experience the air of superiority shown by some members here.  

To quote again, Galileo this time: I never met a man so ignorant I couldn't learn something from him.

We were all beginners once; some of us are not too self-obsessed to admit our ignorance.  In fact we are all ignorant - we just specialise.

rock-hopper.

---

