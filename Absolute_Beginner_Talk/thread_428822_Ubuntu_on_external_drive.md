---
title: "Ubuntu on external drive???"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by sheva7 on 2007-04-30
Hi.  I have only been involved with Linux for a short time and I'm curious if a certain set up will work.  I hope this is not over complicated, but this is what i want to do.
I have a desktop pc running windows xp and a macbook with os x.  I want to put ubuntu on an external hard drive i have so that i can connect it to either computer and access the same ubuntu system and files from the drive on either one, while still leaving the other os's and hard drives alone.  I'm pretty sure this so far is possible, but the rest of what i want is what i'm really curious about.  I don't want to have to set the bios to boot from an external drive first ( I don't want to have to unplug the drive in order to boot from the os on the normal harddrive).  I would rather have a boot loader let me choose which os to boot whether or not the external drive is plugged in.  I also want to leave the mbr in windows and the os x equivalent in tact.  I hope this makes sense.  Is this a possible set up or am i hoping for something crazy? Thanks.

---

### Post by bobbybobington on 2007-04-30
I don't think what you describe can be exactly done. I know of no way of selecting an os without changing the boot order or the mbr. It couldn't be an installed system, because it would have to be reinstalled for new hardware. The closest thing would be setting the boot order to cd drive, pop in a live cd and have a usb stick/drive to save/access your files. :confused:  If anyone knows of a way please feel free to correct me.

---

### Post by starcraft.man on 2007-04-30
I believe that this may be possible (not certain so don't sue me if I am wrong :) ). I think that you can do this with the alternate CD, should let you do this very easily (I prefer it to the live CD). When you get to the partition section, partition your root and swap to the USB Drive (it should appear in the list). Then when your done I think GRUB should automatically detect all your OS (internal and external). 

Backup all your info before you do this, you never know what can happen.

I STRONGLY recommend that you read this page on the MBR and GRUB. 
[]("http://users.bigpond.net.au/hermanzone/p15.htm") 

I also think that you should get a hold of this program, called GAG, saw it on a tv show and its very useful incase your grub install goes bad. 

[GAG]("http://gag.sourceforge.net/")

Your aiming for something a bit advanced, read up before and good luck :)

Disclaimer: I haven't done this, I am pretty sure it can be done. And from what I saw the use of GAG I am fairly sure it detects all OS across external and internal drives, however, I think its best to try GRUB first since it will be there by default and should work. I'm also not responsible for messing up your installs please back up all your info and any other data you want.

---

### Post by Artstew on 2007-04-30
I totally agree with that last post, **Installing linux to an external drive is an advanced procedure**, unless you're already savvy with Linux systems. I don't have anything to add about HOW to do it, but I do want to post a disclaimer, from someone who attempted it and failed.
So this is my story. I went into this project thinking because i've been using computers for over 10 years, that this would be a piece of cake. Not... so much...
First thing I did was to repartition the hard drive using a windows application "Acronis Disk Director". (First mistake) Then when I went to the forums I found that it wasn't recommended to do that. (too late) So I had this ext3 partition and no room for a swap partition. I deleted the ext3 partition and rebooted with the LiveCD into Ubuntu live. The installation went fine... until I encountered the next problem, where to put the grub. I had no idea what the drive #s meant, so I picked drive 1, which ended up being my primary internal drive! So I had unintentionally overwrote my internal hard drive's MBR. *sigh* Luckily, I have an UBCD that I was able to use to repair the MBR.
After searching high and low, i found some instruction pages that told me how to **properly **boot from an external drive. Only one of the sites had a solution that would leave my MBR intact, and that one had a page of commands and functions to execute, many of them I was clueless to what they were actually doing.... I even started with that set of instructions, but quit because some of my commands were causing errors.
I say all that to say this. Sorry about the bold, but I feel this is worth saying.
**If you've never installed Linux before, don't start with an install to an external drive.**
Instead, start by creating an empty (non-allocated) section on the end of your internal hard drive, and install there. Dual boot using ubuntu's grub, because Ubuntu is going to pick up Windows easily... that's the best way to go for the "uninitiated". I'm looking forward to the day when I'll be able to have Ubuntu on an external drive, but I really want to know what I'm doing before I jump in head-first.
I would love if Ubuntu would script that process or something so that a newbie like me could install to an external drive... but so far I haven't seen anything that does that. There's basically no shortcuts...

And btw: I also hosed the boot sector on my external hard drive in the process, did I mention that? Yea, I did. I don't even know how! So, yeah, I've spent all week trying to figure THAT out. I'm not going to be sticking my neck out that far again (at least for a while.. lol)

---

### Post by bobplano on 2007-04-30
i don't think you can do this because mac and windows generally have different computer structures. even if they didn't it would still be hard as you would have to have all the drivers on the external drive, put grub on it and have both computer choose the external drive's grub.

---

### Post by Majiq on 2008-01-05
So I just installed Ubuntu on my external and it took me a few goes to get it right. I, myself, am a first time Linux user and this external installation was my first. This is my first post, and seeing as how you asked this over half a year ago, this may be foolish to even respond to, but in case you didn't get it by now, I'll lead you through how I did it.

This is my suggestion: First make sure that you don't have anything you want on your external, because that'll just make the whole process easier. Then, goto this website [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811) to solve all your problems. As a note, it's not entirely complete. For you, I would suggest doing it on the Mac because adding Windows to the bootloader is an easy one to lead you through, for me.

---

### Post by AKD on 2008-01-05
I have Ubuntu 7.10 running on my external hard drive just fine. I got it working the first try (besides a few sound problems which were my fault). It is not an advanced thing. I used vista to shrink the volume of the partition my external HDD and then install ubuntu from the liveCD onto the free space. There are a few problems. You cannot boot your computer if you do not have the HDD plugged in is one of them.

---

### Post by Majiq on 2008-01-05
Yeah, I had that problem at first. Actually, on my first two tries I had that problem. The key is to not let the bootloader touch your internal hard drive. 
My goal was this: Get the choice of Linux or Windows with the external in, and a no-boot-options Windows without the external. It took a little finagling, but how to do it depends on the distribution or CD you use. You just specify where to install the boot, in this case the external. At that point, you then have to change the GRUB files like it says in the link I posted, with a little addition of adding 

```

map (hd0) (hd1)
map (hd1) (hd0)

```

to the Windows boot options in /boot/grub/menu.lst.

If you can figure out how to restore your Master Boot Record on your internal, AKD, and figure out how to configure the Linux appropriately, I'm pretty sure it'd work for you, too.

---

