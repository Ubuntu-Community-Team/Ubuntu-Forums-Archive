---
title: "Can I &quot;Make My Own&quot; recovery CD's?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Beazel on 2007-04-10
Hi there folks,

    I appologise in advance for posting a rather a daft query, but I'm new this Linix stuff!

Before I try to install UBUNTU I thought it might be a good idea to make me some backup disks. Can any one suggest some decent software to do this in windows? I just want to take an image of the hard drive "AS IS" and end up with a cd set that puts me back where I started Should it all go wrong!

Many thanks in advance,

(Hopefully!) A New UBUNTU user.

---

### Post by inchaos on 2007-04-10
This depends, my first question is are you looking to dual-boot Windows and Ubuntu?
If not, then recovery discs will only be able to help you reinstall Windows should you decide to ditch Linux.

If you are looking to dual-boot, then recovery discs are a good idea.  Making them, however, depends on the type of computer you have.  Some computers have a built in feature, my laptop prompted me to create recovery discs after I'd had it for a few weeks.  Your computer may also have a built in recovery partition, in which case, recovery discs aren't all that necessary since the recovery partitions contain a bootable mini NT version of Windows that allows you to restore your computer to its previous state.  

I've never heard of recovery discs that are just HD images, they are typically just reinstall/restore discs that will either wipe your HD and reinstall Windows or will attempt to recover Windows by allowing you to boot from the disc should your boot files/.dll files/registry files become corrupt.  

So I guess my questions are:
1. Dual-boot or only one OS?
2. What kind of computer and how old (HP, Dell, etc.)
3. Do you have a recovery partition (Typically about 8 GB, shows up in 'My Computer' but all files are hidden)

Lastly, you usually need DVD's for recovery discs, mine took 4 DVD's to make.

Hope I can help!

---

### Post by inchaos on 2007-04-10
Actually, I guess you can make HD images and make them bootable...
So I guess I'm a little dense.
I found this site:
[http://www.drive-image.com/](http://www.drive-image.com/)

It claims to have a fully functional 15 day trial version, it should let you make your image like you want, though I've never tried it so I can't profess to know how it works.
:)

---

### Post by stoer on 2007-04-10
Hi Beazel,
Maybe this is what you're looking for, 
I was searching for the same sort of thing some months back and was given the following advice...

SystemRescueCd
"Description: SystemRescueCd is a Linux system on a bootable CD-ROM for repairing your system and your data after a crash. It also aims to provide an easy way to carry out admin tasks on your computer, such as creating and editing the partitions of the hard disk. 
where to get System RescueCD..."

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Next info on using partimage from Sysresccd.


[http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)

and

[http://www.ubuntuforums.org/showthread.php?t=287522](http://www.ubuntuforums.org/showthread.php?t=287522)

Hope you find something usefull here.
Success,

---

### Post by Beazel on 2007-04-10
Thanks for so many replies already folks, I'm checking stuff out as I speak.

inchaos: I'll try to answer as best as I can!

*1. Dual-boot or only one OS?*
I reckon I'll have to go dual boot for the first little while, Once I'm a bit more used to Linux I'll get rid of windows for good. What a day that'll be! 

*2. What kind of computer and how old (HP, Dell, etc.)*
It's a Toshiba Equium A100 306.  It's relatively new, (to me anyway) and has the dreaded Intel Pro Wireless 3945abg card in it...  That's a problem for another day though.

*3. Do you have a recovery partition? *
Pretty sure I haven't, I've just had a good look around and found nada.  Just got the bog standard "Recovery Media" that came with it.  I don't seem to have any tools to make my own backups either.  I can get back to factory settings pretty fast, but Re installing all the "bits and bobs" programs is a proper hassle.

Many thanks so far folks!
Beaz

---

### Post by inchaos on 2007-04-10
I know what you mean, reinstalling Windows is a pain in the butt.  

Toshiba isn't too fantastic on the 'customer support' end, they don't have recovery partitions and don't usually have a way to create recovery discs either.
Fun stuff, eh?

So, a third party disc creating program is probably what you're looking for.  

Still, I'd make sure you back up all of your music, pictures, etc. just to be sure...find a friend with an external HD and see if they'll let you borrow it for a few days.

All in all, you should be fine.  Ubuntu will allow you to repartition your HD, simply making your Windows partition smaller.  It's a pretty safe move.

I have the good 'ol Broadcom wireless card problem and so I have to keep Windows if I want wireless capabilities.  :(

---

### Post by boudreaujr on 2007-04-10
I've used Norton Ghost on my windows machines with great success many many times.  I think this is what you are after before you start dorking with your hard drive.  It's pretty easy to use and will make a bootable set of cdrom or dvd image disks that you can reinstall to your disk and have your system back the way it was before you started.

Good Luck.

Denis

---

