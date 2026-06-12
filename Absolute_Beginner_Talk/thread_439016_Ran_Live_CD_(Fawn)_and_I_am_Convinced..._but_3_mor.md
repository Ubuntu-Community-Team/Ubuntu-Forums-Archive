---
title: "Ran Live CD (Fawn) and I am Convinced... but 3 more questions"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by benditlikebecker13 on 2007-05-10
Last night when I can home my Feisty Fawn disc was downloaded and ready for me.  When I booted from the live CD I was amazed that every piece of hardware worked to perfection (with the exception of iPod and Printer, forgot to check those).  Whenever I do something like this (new OS or Hardware) my heart sits in my throat while my computer is booting and I am fully expecting something to not work.  Well, way to go Feisty, you just made my nervousness look a little silly....  One thing that also impresses me is that Ubuntu was faster off the live CD than Windows is for me currently.  That only leads me to believe that once I install I am going to feel like I am in Super Computer Heaven.  I think this is going to help me get more life out of my aging CPU.

So now that I have made the decision to change from XP to Feisty I had 3 quick questions first.

1.  What is a good program to wipe out my hard drive to start my starting over?

2.  I am planning on doing two things with hardware, should I try to get it to work in Windows first, or is there no logic in that thinking?  I just want to get a 1gig stick of DDRAM and an adapter to turn my (currently external) SATA HD into an internal SATA HD w/ IDE host adapter (found some cheapies on eBay).  I know the memory will just work, not so concerned about that.  I am worried about getting the HD to work when making it internal.  My thinking on trying Windows first is that I am good at fixing problems in Windows, so if something goes wrong I can figure it out, then make the switch.

3.  Last question and this is probably just to expel my paranoia.  Now that I got the majority of my hardware to work in the Live CD environment, that is a guarantee that it's going to work once I Fdisk and clean install Ubuntu.  I assume that is the case, just have to hear someone who knows what they are talking about confirm.

Thanks for all the help; I am almost one of the family.

---

### Post by Inxsible on 2007-05-10
> **benditlikebecker13 said:**
> Last night when I can home my Feisty Fawn disc was downloaded and ready for me. When I booted from the live CD I was amazed that every piece of hardware worked to perfection (with the exception of iPod and Printer, forgot to check those). Whenever I do something like this (new OS or Hardware) my heart sits in my throat while my computer is booting and I am fully expecting something to not work. Well, way to go Feisty, you just made my nervousness look a little silly.... One thing that also impresses me is that Ubuntu was faster off the live CD than Windows is for me currently. That only leads me to believe that once I install I am going to feel like I am in Super Computer Heaven. I think this is going to help me get more life out of my aging CPU.
 
So now that I have made the decision to change from XP to Feisty I had 3 quick questions first.
 
1. What is a good program to wipe out my hard drive to start my starting over?
 
2. I am planning on doing two things with hardware, should I try to get it to work in Windows first, or is there no logic in that thinking? I just want to get a 1gig stick of DDRAM and an adapter to turn my (currently external) SATA HD into an internal SATA HD w/ IDE host adapter (found some cheapies on eBay). I know the memory will just work, not so concerned about that. I am worried about getting the HD to work when making it internal. My thinking on trying Windows first is that I am good at fixing problems in Windows, so if something goes wrong I can figure it out, then make the switch.
 
3. Last question and this is probably just to expel my paranoia. Now that I got the majority of my hardware to work in the Live CD environment, that is a guarantee that it's going to work once I Fdisk and clean install Ubuntu. I assume that is the case, just have to hear someone who knows what they are talking about confirm.
 
Thanks for all the help; I am almost one of the family.
 
1) GParted : Its right on the Live CD
 
2) If you want to set up the HD thing in Windows, you should. There will surely be a learning curve with Linux and it would be better if you don't add to it so early in the cycle.
 
3) If your hardware works in the Live CD environment, that is a very good sign. But its still NOT a "guarantee" that everything WILL work. You may have to be ready to tweak a few things here and there.
 
Welcome to Ubuntu !!!

---

### Post by Kobalt on 2007-05-10
1. What do you mean by wiping out ? You mean cleaning/defragmenting your windows partition ? If so, then you can you the windows defragmenter and its cleaner, plus maybe a few apps removal... If it's about partitioning, then GParted is all you need, it's in the LiveCD.
2. You can keep windows beside Ubuntu first, and not remove it all. That way you can get your SATA drive to work in windows if it doesn't in Ubuntu (which I doubt as of Feisty Sata is now quite well working) and get help on how to get it working over here.
3. If it works on the LiveCD, it should work (99% sure) once you made an install.

---

### Post by qpieus on 2007-05-10
Hello and welcome.
1. There's no need for a separate program to wipe your HD. The ubuntu installer will give you that option - to overwrite the existing HD if that's what you want to do.
2. Trying your changes out in windows first certainly won't hurt and if it gives your more assurance that the hardware is working properly then go for it.
3. In general, if your hardware is working when using the live cd, then it still should work after the regular installation. If not, it's probably a minor issue to fix and there's plenty of help here in the forums.

---

### Post by benditlikebecker13 on 2007-05-10
> **Kobalt said:**
> 1. What do you mean by wiping out ? You mean cleaning/defragmenting your windows partition ? If so, then you can you the windows defragmenter and its cleaner, plus maybe a few apps removal... If it's about partitioning, then GParted is all you need, it's in the LiveCD.
 

By wipe out I mean format and get rid of all the stuff that is currently sitting there.  I knew there was Gparterd, I just thought maybe there was something better.

I like the dual boot option, but part of me feels like if I don't go all the way with this (reformatting HD and install Ubuntu only) that I will rely too much on Windows and not take the time I really need to learn a new OS.  I am throwing that option around.

And thanks for the quick responses... I can equate this message board to the Amazon River.  You throw some chum (a message) in the river (the board) and the piranhas will get it faster than you can imagine with laser like precision (the people who respond to messages).  You guys (and gals) are awesome.

---

### Post by drowner on 2007-05-10
> **benditlikebecker13 said:**
> By wipe out I mean format and get rid of all the stuff that is currently sitting there.  I knew there was Gparterd, I just thought maybe there was something better.

I like the dual boot option, but part of me feels like if I don't go all the way with this (reformatting HD and install Ubuntu only) that I will rely too much on Windows and not take the time I really need to learn a new OS.  I am throwing that option around.

And thanks for the quick responses... I can equate this message board to the Amazon River.  You throw some chum (a message) in the river (the board) and the piranhas will get it faster than you can imagine with laser like precision (the people who respond to messages).  You guys (and gals) are awesome.

GParted would be perfect for your situation: There is nothing better in Linux-Philosophy.... GParted will easily wipe your XP drive, and thats exactly what you want it to do.

But also, you could reinstall, and use the default options, IE HOSE EVERYTHING

---

### Post by drowner on 2007-05-10
By the way, i have a dual boot, but only for emergencies (like playing Football Manager, or watching ONE internet stream that i just cant, for the life of me, get going).

But, i made a philosophical decision to use Ubuntu, and I love it.

---

### Post by Hewure on 2007-05-10
I'm pretty much a Linux Noob as well, but can answer all your questions as I've basically encountered all your queries...

1: the Fiesty installer (on desktop) has a Hard Drive Partitioner built in.
You'll have to make 2 partitions, one for Ubuntu itself, and another smallish one (2 or 3Gb) for Swapfile - like Windows Pagefile. It's pretty easy to use.

2: The RAM will be picked up in your BIOS. Needs no Software. The SATA Drive SHOULD be picked up by Ubuntu (I have a SiL3112 PCI SATA Card in my 2nd PC and it worked without Drivers or anything). XP required Drivers, and wouldn't boot from it, whereas Ubuntu boots from it fine!

3: Same as "Live". Generally just need Display Drivers - ATI or NVidia - for better performance. These are available through the  Package installer - ie  tick the box, it'll download & install, no  scary Terminal Commands needed!

Good luck!

I'm sold on Ubuntu now, after years of Viruses/Spyware in U Know What.

Cheers, Steve

---

### Post by derjames on 2007-05-10
before installing or wiping out your hard drive or even installing in a dual boot mode... consider installing Ubuntu in a virtual  machine... this will give you confidence before leaping ahead... use VMware server as the virtual machine and install ubuntu there... when your are happy with the way linux works then you can do a dual boot or even wipe out windows...

cheers

---

### Post by MOS95B on 2007-05-10
All i can comment on is the "Wipe the drive" part.  I just installed Ubuntu about a week ago, using the default instl (i.e. Just say yes to everythig) and it cleaned XP off and set up a nice clean Ubuntu install.

Unlike re-installing Windows (which I've done who knows how many times) there does not appear to be a need to start with a clean drive.

---

### Post by lamalex on 2007-05-10
> **Hewure said:**
> no  scary Terminal Commands needed!

scary terminal commands? I've never heard of such a thing! GUIs are the scary part of Linux *shudders*.. oh except maybe 'killall' that's kind of a scary one.

---

### Post by benditlikebecker13 on 2007-05-10
In doing my research, the CLI really doesn't seem so scary.  I used DOS a bit in my early years of Computer use, so I'm not afaird of text.

One other thing worth mentioning that I kinda forgot is the SATA that I plan to turn internal (from external) worked fine with the live CD, while in its current external state.  It actually worked better in Ubuntu than it ever has in Windows.  Sometimes in Windows I have to turn the thing on and off 3 or 4 times to get it to work.  Ubuntu recognized it right away.

---

### Post by Hewure on 2007-05-10
Scary for Noobs - well, me anyway!

I'm getting there though. only need 4 Diazepam per open Terminal :wink:

Seriously though, is there a printable list of common commands anyone knows of?

********************

So U are planning to run the SATA off an Add In PCI Card, or is it native to the Motherboard?
I can only vouch for the Sil card, worked without lifting a finger, and the GRUB booter allows me to boot from it, whereas Windows only let me use it as Storage {no facility in BIOS as SATA not native to MoBo}

---

### Post by benditlikebecker13 on 2007-05-10
> **Hewure said:**
> Scary for Noobs - well, me anyway!

I'm getting there though. only need 4 Diazepam per open Terminal :wink:

Seriously though, is there a printable list of common commands anyone knows of?

********************

So U are planning to run the SATA off an Add In PCI Card, or is it native to the Motherboard?
I can only vouch for the Sil card, worked without lifting a finger, and the GRUB booter allows me to boot from it, whereas Windows only let me use it as Storage {no facility in BIOS as SATA not native to MoBo}

My plan is to use something like this.  I plan to put my SATA as the slave on the IDE cotorller of the MB.

[SATA to IDE]("http://cgi.ebay.com/For-Host-IDE-TO-SATA-100-133-Adapter-Converter-P1_W0QQitemZ230126924116QQihZ013QQcategoryZ74941QQrdZ1QQcmdZViewItem")

---

### Post by benditlikebecker13 on 2007-05-10
[Then there is always this option]("http://cgi.ebay.com/4Port-PCI-Combo-SATA-RAID-IDE-ATA-133-Controller-Card_W0QQitemZ330117544703QQihZ014QQcategoryZ39968QQrdZ1QQcmdZViewItem").  I like option one because you don't need any drivers.  I worry about option 2, because if I get some cheap control card (and I am cheap) than I have concerns about getting it to work in a Linux enviro.

---

