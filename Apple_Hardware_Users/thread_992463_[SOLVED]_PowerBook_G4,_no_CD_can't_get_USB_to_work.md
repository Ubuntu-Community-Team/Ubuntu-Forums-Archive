---
title: "[SOLVED] PowerBook G4, no CD can't get USB to work..."
date: 2008-11-24
forum: Apple Hardware Users
---

### Post by el_heffe on 2008-11-24
I have a 12" powerbook G4 1Ghz, with 1g/100g/32MB.  The internal DVD drive has crapped out, again and I have no desire to change it out.  I have two external Firewire drives, one external USB dvd drive, and several USB thumb drives to my disposal.  The thing is I cannot get the computer to boot from USB anything, but I may be doing something wrong.  I have used Fink to install the hfsutils, and I believe I am formatting everything correctly, its just I am not sure.  The instructions on the website say to use mac-fdisk, but thats not a apple product.  There is also the idea of using HFS harddrives, IF mac would support that, which 10.5 does not.  I have created a 8g partition at the end of my internal drive and the FW drives are pretty much full, but can be reformatted without too much crying on my part.

I have tried to get the USB stick to work, and I have followed the directions, bent the directions, twisted the directions, google'd the directions, eaten crabcakes and sacrificed several uni-wing'd chickens to the cause.  All to no effect.  Does anyone have any ideas I haven't thought of?  

Tomorrow at work I am going to try grabbing a couple CD-R's and CD-RW's to see if I cannot finagle the USB drive to boot. Barring that I may take it apart and see if I cant hack it into one of my firewire enclosures... 

What I am asking is this- is there anyone who has had any success using 10.5 to format their USB thumb drives and gotten this to work for the install?

BTW- I have read through several threads, but it seems I am one of the few having problems with getting this USB stick to work in 10.5... but I am human...

---

### Post by el_heffe on 2008-11-29
OK, I have read what seems like hundreds of web forums, blogs, pages, wiki's etc.  I have gotten my internal DVD drive to work, and can now boot into the liveCD.  I cannot get it to install.  Using mac-fdisk I can create a boot partition, but being that OS X is installed on a partition prior to that, no such luck.  Essentially, I give up.  Thanks for all the fish.

---

### Post by tiresia on 2008-11-30
Can you please tell a bit clearly what are you trying to do? 
If your CD-ROM is working, which version of Ubuntu do you want to install,  where did you download the Ubuntu Installer-CD, how did you burn it, and how are you trying to boot it?

---

### Post by el_heffe on 2008-11-30
Using the 7.10 Live CD.  Booting through OPT key and the command I have been relegated to use is now:
live-nosplash break=top

it used to work with just live, but for some reason now i have to use the break=top in order to get it too boot.  Once it gets to the desktop(gnome) I select install and it goes through the normal process for the first 3 screens.  

At the partition screen it doesn't recognize the boot loader partition that previously exists and when I create a new one with mac-fdisk in the console it still doesn't recognize it.

Since I am not in my room right now I cannot tell you the exact partition scheme, but basically it goes like this:

OS X HFS+ ~90G
Ext3 ~8g
'swap' ~600mb

The ext3 is /  

At the partition manager for the installer it hangs after I select format the ext3.  If I boot into OS X and delete everything but the hfs+ partition it still hangs when I select use largest contiguous free space.  I am contemplating reinstalling OS X but it would be a lot of work considering I have no install CD here(I am deployed to Iraq).  That way my partition table might be able to be fixed.

---

### Post by tiresia on 2008-11-30
When you have time, can you please send us a more detailed partition map (with mac-fdisk hit 'p')
Maybe you do something wrong with mac-fdisk. Did you use 'w', to 'write' your new configured partition map?
**BE CAREFUL with mac-fdisk, you can delete the MacOSX partition**, and if you don't have any OSX Installer CD, you will loose it. Maybe you want to make a backup of the whole MacOSX partition (with CCCloner [http://www.bombich.com/software/ccc.html](http://www.bombich.com/software/ccc.html) or with the Apple Utility Disk)
Here is a link to know more about mac-fdisk
[http://penguinppc.org/bootloaders/yaboot/doc/mac-fdisk-basics.shtml](http://penguinppc.org/bootloaders/yaboot/doc/mac-fdisk-basics.shtml) 
&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;&#8230;
An easier and faster way, it's to use an alternate installer CD. You can install also Hardy (8.04) or Intrepid (8.10). See here the download links: [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
If you decide to install Intrepid (8.10), be aware of a small bug that you can solve so : [http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by el_heffe on 2008-11-30
I will post the map when I get back to my room.  As for writing the partition, yes I used 'w' to write the changes.  I already have 10.5 installed on an external partition so I plan to CCC it when I get back.  Last night I backed up the relevent files in my ~/ so hopefully it won't take too long.  I will go ahead and try the alt install cd.  It may take me a day or three to download it, but it is something I have read about on some other posts.

---

### Post by el_heffe on 2008-12-09
OK, after the tedious process of backing up my computer, wiping the HD and reimaging it using CCC it is now good to go.  I got 7.10 to install, after the second try(had to disconnect the external HD) and now its working super great!  I cannot wait to get the updates installed and start apt-get'ing new programs.  I am truly excited to see how it all works and am so far impressed with everything about it.  Thanks for your support!!

---

### Post by tiresia on 2008-12-09
Great! If you are planning to upgrade your system (but even if you aren't) I suggest you to backup every important file, at least your /etc/yaboot.conf and /etc/X11/xorg.conf
The last one is very important for your video, if you upgrade to Ubuntu Intrepid (8.10). If something goes wrong you can just take it back.

---

### Post by el_heffe on 2008-12-09
> **tiresia said:**
> Great! If you are planning to upgrade your system (but even if you aren't) I suggest you to backup every important file, at least your /etc/yaboot.conf and /etc/X11/xorg.conf
The last one is very important for your video, if you upgrade to Ubuntu Intrepid (8.10). If something goes wrong you can just take it back.
Thanks, I will do that when I get back to my trailer! :P

---

### Post by stream303 on 2008-12-10
Be sure to copy or print out your existing /etc/X11/xorg.conf file, and your /etc/yaboot.conf file for future reference in case you decide to upgrade to 8.04.

If you run into repository issues when updating things on 7.10, there is a fix, but I won't go into that unless you run into that problem.  Glad to hear that it is up and running!

---

