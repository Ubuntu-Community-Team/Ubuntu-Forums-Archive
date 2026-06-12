---
title: "[SOLVED] Installing Ubuntu on a seperate HD"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by clanky on 2008-03-24
OK, I know there are a couple of similar threads to this, but none of them answers my question.

I have an HP pavilion laptop with 2 separate 100Gb hard drives, I presently have the computer set up to dual boot using grub from the same HD,  I am having problems with the laptop and I suspect they may be related to the hard drive.

What I want to know is this.

1. Is it possible to install Ubuntu on the other hard drive?

2. Could i still use grub to boot from either Ubuntu or XP, or alternatively could I go into BIOS and change the boot order on the odd occasion that I want to use XP without doing any damage?

3. How do I do it?  I still have the original desktop DVD which I used to install Ubuntu on the partition, can I use that to install on the other HD or would I need to download a different DVD / CD, and would someone by prepared to guide me through the process?

Thanks in advance,
Paul.

---

### Post by waspbr on 2008-03-24
No this is going to produce a catastrophic chain of events which could lead to the end of peanut butter as we know and love today (I don't like peanut butter).

but seriously, yeah ya can you can just go ahead and run the live CD and install ubuntu on another HD, you have a choice to choose at the end to install grubb again, making you new installation in charge of grub or just chose not to install it which should not make a huge difference, grubb should be able to "see" the other OS as you reboot(which is nice). 

If you are installing the same version that you had before, then if may be a little difficult to distinguish which one you are selecting in grub menu, I suggest you pay a visit to 

/boot/grub/menu.lst

and do something to distinguish the two OS'es a little better, but that is completely optional

remember the golden rule, if you are going to play with your OS back up your essentials

good luck

---

### Post by clanky on 2008-03-24
I can't really remember the install process much, is there a stage where you can decide which drive to install on?  Is it fairly idiot proof?

Is it best to format the drive before I do the install or is there an option which will do this anyway, during the process?  I have some stuff on there at present, but nothing which I really want to keep.

---

### Post by clanky on 2008-03-24
> **waspbr said:**
>  suggest you pay a visit to 

/boot/grub/menu.lst

OK, complete noob here, how do i do that?

---

### Post by kolisikepu on 2008-03-24
ok... here's an idiot to rescue you Paul, being new to Ubuntu and all.  :lolflag:

During the installation, there is a Partition tool that will let you play with your partitions manually.  Doing it manuall, you can create, delete and reformat partitions AND even allow you to decide which drive you want to put it on.

At the end, it will ask you to either install Grub (for you, it will be "again") or you can leave your previous version of grub.

My suggestion, during the Partition part of the installation... delete your old Ubuntu installation (if you can) and install your new Ubuntu on your 2nd disk and Grub on the 2nd disk as well.  It is very simple and like I said, I'm an idiot too when it comes to Linux, but with the Ubuntu is... it was simple for me.  ;)

---

### Post by Tews on 2008-03-24
I have dual drives on my laptop and when I installed Ubuntu, I specified my 2nd drive as my installation drive.  I have Vista <spit> on the first drive for those few programs that wont run under Wine.  The install went just like it should with Grub setting up the Dual Boot option. :p

---

### Post by kolisikepu on 2008-03-24
[QUOTE]> **waspbr said:**
> 

OK, complete noob here, how do i do that?

Don't bother with that... as I suggested, if you can get rid of it, remove your previous version of Ubuntu by deleting the partitions that it sits on via the Partition tool during setup.

When your Ubuntu is all setup, then you can mess around with 'menu.lst' in /boot/grub/ directory.  Again... an idiot like me find 'menu.lst' easy to understand and I'm sure you'll have no problems.  Just search 'edit bootloader' in the forums and you'll see HEAPS of help for editing your bootloader.

---

### Post by waspbr on 2008-03-24
Yep, it is fairly idiot proof, I can relate to the fact that at the beginning this is all new and intimidating, but all you need to do really,  go on the live CD press on the install icon, select the timezone, language and keyboard.

then you select the space you wanna have ubuntu installed add the "/"as instructed. Then says yes to everything else and BAM (i can't  believe i just wrote that) you should be done. The default settings are going to install grub but you won't notice the difference, it should present windows and everything else u have installed anyway.

The other thing I was talking about involved modifying your menu.lst file. 

perhaps you should wait until you are a little more experienced on this. let us know if everything goes well (or not, but it probably should go well, I mean it could happen that the electric grid goes down while you are installing but that's a pretty big if)

---

### Post by clanky on 2008-03-24
Thankyou guys, worked fine.

Have the ATI drivers installed, got my broadcom wifi card up and running, just installing all the updates etc. and then it's all down to customising etc. and downloading a few application from the repositories.  I am quite lucky in that I have tried a few things that I didn't like so i can now only install what I know I want on my shiny new Ubuntu.

I have marked the thread as solved, thanks again for all your help.

---

