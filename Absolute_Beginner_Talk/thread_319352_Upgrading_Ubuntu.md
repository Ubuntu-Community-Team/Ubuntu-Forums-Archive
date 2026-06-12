---
title: "Upgrading Ubuntu"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by DevgruSeal on 2006-12-15
I've already got Ubuntu 6.06 downloaded and burned to a disk, and I was wondering if I could upgrade to .10 after I install it, or if I should scrap this disk, and download the 6.10 image and burn a completely new disk..

Another question of mine, is would it be possible to install kubuntu and ubuntu on the same partition, so I could switch between GNOME and KDE easily? (I've read posts here speaking of logging off GNOME then logging onto KDE.)

That brings another question. I'm planning on installing a second distro on a second partition. Which would then make a triple boot system (2 linux distros + Windows XP). Can somebody point me to a guide on installing multiple linux distros, and setting multiple boot devices?

---

### Post by raul_ on 2006-12-15
Yes, you can upgrade.

Yes it is possible to have both Gnome and KDE sessions in ONE Ubuntu installation. 

It works the same way. Create a partition and install whatever you want in there. Ubuntu Live CD has a partitioner included, so you can use it. I don't know if other distros have partition applications included, but the idea is the same

---

### Post by sailor2001 on 2006-12-15
> **raul_ said:**
> Yes, you can upgrade.

Yes it is possible to have both Gnome and KDE sessions in ONE Ubuntu installation. 

It works the same way. Create a partition and install whatever you want in there. Ubuntu Live CD has a partitioner included, so you can use it. I don't know if other distros have partition applications included, but the idea is the same

KDE is in synaptics.........to switch sessions, ctrl/alt backspace and click on the little menu button

---

### Post by DevgruSeal on 2006-12-15
So, I'll need to download and burn the kubuntu image, install it after Ubuntu (Or before, I guess it wouldn't matter), is that correct?

---

### Post by raul_ on 2006-12-15
No..just install ubuntu normally, and after it is installed come ask how to install KDE and i'll tell you (i just don't want to confuse you right now) :)

---

### Post by hoagie on 2006-12-15
I would reccomend you to simply upgrade using the upgraded manager, if you don't want to loose your data.

To do that type
```
gksu "update-manager -c"
```

---

### Post by DevgruSeal on 2006-12-15
Excellent, thanks you guys :)

It'll be sometime tonight when I can get my new hard-drive installed..:P Another question I meant to ask: The new drive is 250GB SATA, and I want to use a rather large portion of it to keep music, games, and other data/documents on, so around what size for each partition should I use? 

I had been thinking maybe 20gb;20gb;210gb (ubuntu;2nd distro for testing;storage), but wasn't sure if that was sufficient size for an installation and enough room for expansion..

---

### Post by PriceChild on 2006-12-15
1. The following will upgrade you from 7.06 to 6.10```
gksudo "update-manager -c -d"
```
2. [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

3. Install Windows first... AFAIK most linux distributions should then sort out the grub menu for you. If not, post back for help including your partition arrangement and current /boot/grub/menu.lst

---

### Post by DevgruSeal on 2006-12-15
Windows is on a completely different hard-drive, and I want to leave that drive alone, as far as installing another operating system on.

Edit: Nevermind, I see what your saying now.
Edit2: I realized I didn't mention it above, but I should've mentioned the two linux distros I plan to install will be on a secondary hard-drive.

---

### Post by DevgruSeal on 2006-12-15
After installing, it popped up a box that asked if I wanted to continue using LiveCD, or reboot. I chose to reboot, it unloaded the LiveCD, and ejected the disk. Took that out and let it reboot, but instead of showing a boot menu, it kept going on to Windows XP.

How do I setup a dual boot screen now? It's possible that the computer doesn't read it because the linux boot menu would be on the other drive, which would be booted after the first one boots.

Edit:

I pressed F8 (Boot Menu) after the mobo POSTs, and booted the ubuntu linux kernal from there, but I don't want to have to do that everytime I start up the computer, or will I have to?

Edit2: And how can I make my screen resolution larger? 1024x768 is my only option, and I use 1280x1024 in XP, so I know my monitor is capable of it. I read a thread about it on here, but I tried it, and it didn't work

---

### Post by rccharles on 2006-12-16
Here is an overview.  

You have two disks. Your windows disk has the MS loader on it. The MS loader only knows about windows.  I assume your bios points to the MS loader, so you are getting only Windows.  Your second harddrive has Ubuntu on it.  Ubuntu uses the grub loader. Since this disk doesn't contain Windows, I assumes Ubuntu didn't notice windows on the first disk.  

What you need to do is configure the Grub menu to include windows and then set up your bios to boot the second disk.

see:
[http://ubuntuforums.org/showthread.php?t=275728](http://ubuntuforums.org/showthread.php?t=275728)

[http://ask.metafilter.com/mefi/47609](http://ask.metafilter.com/mefi/47609)

[http://www.devhood.com/tutorials/tutorial_details.aspx?tutorial_id=405](http://www.devhood.com/tutorials/tutorial_details.aspx?tutorial_id=405)

Robert

---

### Post by kb9tua on 2007-01-30
I currently have 5.04 Hoary installed and a 6.06 Dapper cd from ubuntu shipit. I couldn't get 6.06 Dapper to install so I went back to 5.04 Hoary. How can I get Dapper installed or upgrade to it? I have a 2.6GHz Celeron D CPU, 2GB Memory, and 50GB HD space.

*    *   ****   *      ****
*    *   *        *      *    *
****   ****   *      ****
*    *  *         *      *
*    *  ****   ***   *         :guitar:

---

