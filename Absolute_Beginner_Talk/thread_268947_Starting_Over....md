---
title: "Starting Over..."
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by nickaster on 2006-09-30
Hiya - I had an old Ubuntu disk (warthog) and tried to get started that way - totally eliminated windows and got it going fresh.  Then I realized a new version of Ubuntu would probalby be better (duh!)

So I donwloaded the ISO file, made a disk, and it installed perfectly!

Problem is, the OLD version of Ubuntu is somehow still there!  In fact, its that old warthog version that loads when I boot.  How the devil do I get rid of this???

Really, I'd love to wipe the hard drive again and start over, but for the life of me I cannot figure out how to do this!  The new Ububtu CD does not seem to have an option to delete partions or anything like that.

This is a DELL inspiron... can't I just tell the stupid thing to self destruct and start over? 

Thanks!!!

---

### Post by white on 2006-10-01
When you were installing from the Live CD did you choose to erase all disk, or to use largest continuous space when the partition editor came up?

---

### Post by Nut on 2006-10-01
This sorda happened to me, this is what I did:

1. Installed my original operating system (Windows XP) with the cooperation of a Dell representative.
This is what you need to tell the representative, tell him or her that you have tried to install Linux and that it won't be erased from your hard drive (basically tell them you want your hard drive erased). They will then take you through some sort of wierd thingy that erases the hard drive.
2. Then, from there, let them guide you through the installation of your original operating system.
3. After it's installed, install Ubuntu Linux from a live CD.
(The reason you need live CD is for some reason from experience I've found that being on Linux while installing Linux helps.)

Eh, it may take you awhile to do all that, but you will fix your computer!

**Note** that they may have to send you some discs if you've lost the ones that came with your computer.

---

### Post by nickaster on 2006-10-01
oh skunko...

Well, I don't recall being asked to "erase all disk"., just a little aobt 4.x

---

### Post by nudnik on 2006-10-01
> Hiya - I had an old Ubuntu disk (warthog) and tried to get started that way - totally eliminated windows and got it going fresh. Then I realized a new version of Ubuntu would probalby be better (duh!)

So I donwloaded the ISO file, made a disk, and it installed perfectly!

Problem is, the OLD version of Ubuntu is somehow still there! In fact, its that old warthog version that loads when I boot. How the devil do I get rid of this???

Really, I'd love to wipe the hard drive again and start over, but for the life of me I cannot figure out how to do this! The new Ububtu CD does not seem to have an option to delete partions or anything like that.

This is a DELL inspiron... can't I just tell the stupid thing to self destruct and start over?


Download a free DOS program called "KillDisk" from the Active software site. I would recommend the bootable CD version. 

Boot from this CD as you would an OS install CD like Ubuntu or Windows.

Use the program to erase the entire hard disk. The process will take some time, but will ensure you get a truly clean install.

Use a Windows CD, or DOS utility to restore the Master Boot Record to ensure the Warty GRUB is wiped. Then install from your Dapper ISO and all should be well.

Remember....this ](*,)  isnt the mascot for nothing! Just hang in there:mrgreen:

---

### Post by petri on 2006-10-01
Why not just install **Gparted** with Synaptic when running livesession? 
With Gparted you can format harddrives :mrgreen: and then start install directly.

---

