---
title: "New user with questions"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Bungo Pony on 2007-03-23
Hey all! First post here, and I've got a few questions. First of all, I haven't installed yet. I'm getting a new PC (hopefully tonight) with Vista installed on it. I plan on wiping Vista because I'm tired of using buggy Microsoft products, and the reviews I've read haven't done any justice for Vista. I've been able to try out the Edgy Live CD, and it seems quite nice.

So, here's what my plan is: I'm going to be dual booting Ubuntu Edgy with Win2k. From what I've read, the easiest thing to do is format both hard drives using FAT32. I'm going to have a 20G hard drive and a 160G hard drive.

First question: which drive would be better to use for each OS? I was thinking of putting Win2k on the 20G drive.

Second question: Feisty gets released next month. How easy will it be to upgrade from Edgy to Feisty? Since I've never really used Linux, I don't know if you have to re-install software, re-format your drive, backup all your files, etc.

---

### Post by mahy on 2007-03-23
FAT32 is the WORST option imaginable. Just install win2k on the first drive (with ntfs), and then Ubuntu Edgy to the second one (my FS of choice: ReiserFS), putting GRUB to the Master Boot Record.

EDIT: Update should be quite smooth, but don't you worry about it at the moment.

---

### Post by Bungo Pony on 2007-03-23
My biggest worry is pulling files from each hard drive. I'm a musician, so I'll probably be spending time in Windows for that sole purpose, but I can see the need for me transferring files to and from each drive.

Would NTFS and ReiserFS conflict with each other?

---

### Post by Blutack on 2007-03-23
If you need to transfer stuff use ext3, as there are drivers available for windows to allow it to write to ext3.  To go the other way, I'd agree with the other chappy (having recently lost 100gb of movies to a corrupt fat32 drive...).  Linux can read NTFS just fine, and if neccesary you can write to it (although that involves a bit of extra configuration).

---

### Post by mahy on 2007-03-23
> **Bungo Pony said:**
> My biggest worry is pulling files from each hard drive. I'm a musician, so I'll probably be spending time in Windows for that sole purpose, but I can see the need for me transferring files to and from each drive.

Would NTFS and ReiserFS conflict with each other?

You can teach windows to read ReiserFS (using Total Commander) and you can teach Linux to read/write to ntfs.

Linux CANNOT be installed to a FAT32 partition. Win2k can, but it's a very bad idea.

---

### Post by joshkidd on 2007-03-23
I agree with Mahy with regards to filesystems.  You should take his advice.

As for disk space, which OS do you see yourself using more?  Neither OS is very large in itself.  Do you see yourself using a lot of digital media with one OS over the other?  That OS should have the larger drive.  Maybe you want a third partition that would be a data partition for both operating systems.

Also, Ubuntu upgrades in the past have been pretty painless.  No reformatting required.  Lots of software reinstallation, but that's handled automatically by the update manager.  As for backing up your files... that's up to you.  But I've not yet needed to restore from a backup after upgrade.  But anything can happen.

---

### Post by Bungo Pony on 2007-03-23
> As for disk space, which OS do you see yourself using more?

Currently, it's Windows until I find out how much of my software will run in WINE.

Perhaps putting Windows on the larger drive is a safer bet, although I'd love to get away from Microsoft as much as possible. I guess only time will tell how much I can completely switch over to Linux.

Also, is there an online list of terminal commands, what they do and how they work?

---

### Post by mahy on 2007-03-23
> **Bungo Pony said:**
> Also, is there an online list of terminal commands, what they do and how they work?

Nothing i'm aware of. As a newbie, you don't have to rush headlong to terminal. If in doubt, ask here. Otherwise you'll probably be fine with GUI. Remeber, <Tab> is for file name and path completion, and almost every program's got a "man page". E.g. 'man wine'.

---

### Post by dhtseany on 2007-03-23
Look on <snip> or <snip> for "Ubuntu Linux Bible". I've learned alot from that book.

It includes a ton of stuff you'll want to check out.


Hope it helped.

Sean

---

### Post by Bungo Pony on 2007-03-23
> As a newbie, you don't have to rush headlong to terminal.I'm aware of that, but after using DOS and working on a Commodore 64 for years, I'm not intimidated by my keyboard ;)

> Look on <snip> or <snip>  for "Ubuntu Linux Bible". I've learned alot from that book.Cool! I'll definately look into that.

---

### Post by Zzl1xndd on 2007-03-23
My advice would be to use 20 gigs for W2K, make a partition for Ubuntu that is also 20gigs, and format whats left as a Fat32 drive that they can both read.

---

### Post by jhenager on 2007-03-23
Man pages aren't always easy to read, but can provide helpful information. I can offer some advice re: migrating from Windows to Linux.

First of all, use the GUI and apps like Synaptic as much as possible for customizing, adding, tweaking, etc. Terminal is powerful, but you may want to ease into it.
Second, WINE is a great help, although some programs won't install or run right under it. I would recommend looking for native Linux apps instead of trying to run Win32 programs under WINE.
[http://www.linuxeq.com/](http://www.linuxeq.com/)
is a good source of information on programs that provide comparable functionality to the Windows world. Good luck, and have fun.

---

### Post by Bungo Pony on 2007-03-23
> I would recommend looking for native Linux apps instead of trying to run Win32 programs under WINE.

I've already looked into a lot of that. Many of the programs I use will work in Linux and there's alternatives for the ones that won't work, but there's the occasional one where there is not alternative (unless someone can find a nice flexible drum machine simulator)

---

### Post by jhenager on 2007-03-23
> **Bungo Pony said:**
> I've already looked into a lot of that. Many of the programs I use will work in Linux and there's alternatives for the ones that won't work, but there's the occasional one where there is not alternative (unless someone can find a nice flexible drum machine simulator)

Hahaha, ask and ye shall receive.

[http://www.hydrogen-music.org/](http://www.hydrogen-music.org/)

Don't know if it fits the bill, but just about every time I have thought there wasn't something, google turns out to still be my friend.

---

### Post by Bungo Pony on 2007-03-23
That's excellent! It looks like it might be better than what I'm currently using. Thanks a lot :D

---

