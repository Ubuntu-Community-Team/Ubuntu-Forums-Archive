---
title: "Not enough ram?  Now what?"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by wekebu on 2006-11-26
I'm assuming my problem is not enough ram.  Here's what I have and what I did:

Pentium 3, 450 MHz, 256 MB ram, 8 GB hd. I can add only 128 MB of ram for a maximum amount allowed of 384 MB.

I had Breezy running just fine for 1 - 2 months.  I upgraded to Dapper.  That worked for another month until I tried to install a wireless router.  I never got the wireless to work and I'm sure I caused problems in the OS.  I decided to start fresh and install Dapper again. At least I think I did a fresh install, I got a notice that partition #1 of dev/hda as ext3 and partition #5 of dev/hda as swap will be formatted and I said okay.  I looked in the files afterwards and there weren't any of my old files, so it looked like a fresh install.

Yesterday, a week after this new install, I got a notice that there were updates available.  After they finished loading, the system rebooted and locked up.  It freezes at "Ok, booting to kernel" and/or "Kernel panic". I've tried control/alt/F1, alt/F1 and control/alt/backspace at these errors and it won't break out.

I've tried to boot to the install cd and request an install and it locks up at the same spots.  If tried to boot to the alternate cd, same results.

I'd like to do a fresh install of Dapper, but I can't seem to do that at this point.  Also, was I correct in assuming I did a fresh install a few weeks ago?

Is the basic problem that I have too little of memory? Or something else?  Will 384 MB do any good or should I go with Xubuntu's version of Dapper?  :-?

---

### Post by taurus on 2006-11-26
That should be enough RAM to run Ubuntu.  Why not install Edgy from fresh?

---

### Post by Rodneyck on 2006-11-26
I had that problem installing on a laptop with similar specs.  You would be advised to use Xubuntu instead. It is geared for older systems, even those running only 64mb of ram. It is fast on my old laptop, a great find.

If you do decide to go this route, get the Xubuntu CD that installs via text called the "Alternate install CD", not the live CD. People have installed Ubuntu and Xubuntu from live CDs with your specs, but they reported it took them 5 to 8 hours to do so, lol. 

[http://www.xubuntu.org/](http://www.xubuntu.org/)

There may be a similar Ubuntu CD that installs via text prompt, but I am not aware of it.

---

### Post by AndrewB on 2006-11-26
Usually, when I do a frsh install on a HD that had a previous OS. I will run DBAN [http://dban.sourceforge.net/]("http://dban.sourceforge.net/"). The quick protocol will give you a nice clean enviroment to install a fresh OS onto. It wipes the MBR as well.

---

### Post by jerrykenny on 2006-11-26
thats plenty of ram.  Definitely.

Slow processor 'though, and Xubuntu will ease the load on that.

try to rescue you current installation, boot of the install cd, and type <rescue> at the prompt.

youll get to a shell . . . . login as yourself, then try 

sudo apt-get update

sudo apt-get dist-upgrade

sudo grub-install hd0


In future, for a fresh install try manual partitioning

partition 1  128mb  ext2  /boot
partition 2  600mb  swap   swap
partition 3 (rest of space) ext3   /


cos maybe your bios is struggling to find the kernel, doubtfull, but above partions would work well.

Always use the grub boot loader, not lilo, as grub doesnt need manually updated.

---

### Post by wekebu on 2006-11-26
jerrykenny:  I'd love to try to rescue this os, but I can't seem to get to a prompt.  I've tried booting without cd's and booting to a copy of the Dapper's desktop cd and the alternate cd, all end up stuck at "Uncompressing Linux....Ok, booting to the  kernel".  It'll stay there all night if I walk away mad.  What's the magic keystrokes?  I've tried the ones I know.

Taurus:  Edgy?  Geeze, I'm just trying to crawl into Dapper!  Isn't Edgy, well, edgy?

AndrewB:  Thank you for the link to DBAN.  It looks like that program is exactly what I want and there's a floppy drive on that computer.

Rodneyck:  I have a satellite connection, so large downloads are out of the question.  I'll have my hubby download the Alternate Install CD tomorrow at his work.  I'm hoping that the install CD will allow me to get past the booting to the kernel error!

---

### Post by AndrewB on 2006-11-27
Hi, just a FYI, if you have multiple HD's on one computer and only want to wipe ONE of them. You must either remove power or the IDE/SATA cables from the remaining drives. DBAN will erase them all otherwise. 

OH how do I know.....:-k

---

### Post by wekebu on 2006-11-28
I was able to get into recovery mode and I can get into Dapper again. Thanks again for the help.

Problems with wireless card, but I'll do a new post.  This forum is the only reason I can stay with Ubuntu!

---

