---
title: "UnPartition my hdd"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by Jack Hollister on 2008-05-27
I had ubuntu installed on my mac, and I partioned like I was told but now I cant reverse the partion
Please help as I want my mac back as 1 partion
Also the old partion is now "unallocated space"

---

### Post by sabamanga on 2008-05-27
I did this yesterday.. There's good news and bad news.
Good news is it's possible. That's about it for the good news.. Sorreh matey.
Bad news:
-You're going to need to back up your Mac before hand, because you're going to reinstall Leopard.
-It takes about 3 hours, so grab a sandwich... And a Nintendo DS or something.

You need to:
-Back up your Mac! Try not to take any shortcuts. It won't back up things like your wallpaper, and if you've changed any of the icons for the OS X system I'm afraid you're going to have to re-apply them. But everything else'll be safe. Even down to passwords on the internet.
IF YOU DON'T BACK IT UP, YOU'RE NOT GOING TO BE ABLE TO ACCESS YOUR MAC HOW IT WAS AGAIN, ALL YOUR FILES AND SETTINGS (AS WELL AS ANY APPS YOU INSTALLED AFTER YOU BOUGHT YOUR MAC) WILL BE LOST.
Back it up.. Please.. :)
-Put in your Leopard (I'm guessing?) Install Disk 1. If you're running Tiger it'll work exactly the same.. Apart from a tiny bit I'll tell you in a moment.
-Boot from your Install disk (Shut down, press the power button again, and hold down the option key or 'alt')
-Select OS X Install Disk 1, it'll boot into a window, with the purple aurora background. Don't press anything yet!

-At the bar at the top, you have a few dropdowns.. the Apple logo, and some other stuff I don't really remember. But one of them is called: Disk Utilities. For Tiger it's called something similar, Utilities or something. Or Maybe it's called Utilities for Leopard and Disk Utilities for Tiger. EITHER WAY: Choose that one :P
-I can't remember what the drop down options were, but they seemed pretty self explanatory... It doesn't really matter.. As long as you have Disk Utilities open in front of you.
-On the bar on the left, select your entire hard-drive. It's usually the first one on the list... Underneath it you should see all the partitions you've created.
-There are tabs in the centre of the Disk Utilities Window, one of them says something like unpartition, or repair disk. If you can't find it, just click along the tabs until you get a page where you can see all the partitions you've created represented in a rectangular diagram. Macintosh HD will be at the top.
-There's a button next to it saying restore to one, or repair. Click it, you'll be asked to rename your Harddrive; You'll see all the smaller partitions will be grouped into one big one, under the name you're about to type (Sorry, that was a bit poorly explained, I'm sure you'll get what I mean when you see it)
-Make sure it's formatted in the right way for a Mac... If it says something like 'Journaled' in the drop down menu in the Disk Utilities window, that's fine, leave it. It'll probably be set to the right one by default. But you don't want it saying FAT32 or anything like that, otherwise OS X can't install itself there.
-Confirm it (There should be some sort of go ahead button) And your harddrive is back in one piece. (If you've managed to stick with me and my ranting :P   )

Now you're going to have to reinstall Leopard. It's pretty straight forward, and does most of the work for you. All you have to do is stick the right Installation disks at the right time and try and be patient. It may check your install disk for 'consistencies' before installation, that's fine, don't skip it, just let Steve Jobs work his magic.

So once you're installed, it gives you the option of writing a previous back up back onto your hard drive. (That's why you backed up your machine before) If you didn't back up your machine, tough cohones, I'm afraid, you're just going to have to cope with a fresh machine. It's completely functional, it just doesn't have any of the your personal documents or applications you installed after you bought your mac.

That shouldn't take too long.. Less than the installation anyway.

That's it, you're all done.
Sorry about the long winded-ness. Does that help at all?

---

### Post by stueng on 2008-05-27
After you have backed up all your stuff and before you start installing again try booting up from the Ubuntu CD and see if you can use the partition editor to increase the size of the Mac OS X volume so it occupies the free space

I am not sure if Gparted can re-size HFS volumes or not... but if it can it will save you a lot of headache

Backup first!

---

### Post by stueng on 2008-05-27
Oh and if you created the partition with Boot Camp Assistant I thought Boot Camp Assistant had the ability to remove the new partition and revert the system back to a single partition??

---

### Post by Jack Hollister on 2008-05-27
@ sabamanga
Thanks for the info, my exteranl hdd wont let me back up :/ it says that its read only and I cant seem to change It, the only thing that I would want backing up is my music and my apps so Ive tried copy and pasteing but that didnt work. and time machine worked once but now it wont open up saying a error

---

### Post by sabamanga on 2008-05-27
To Stueng:
Neyy, it doesn't.. I wish it was that simple :P
Boot camp only panders to Windows in that respect... After you change the partition you created for Windows to anything other than an NTFS or FAT32 system, boot camp doesn't want to know.

and to Jack Hollister:
That's a bit of a bummer. I don't know why your back up is doing that.. Mine stopped working on Windows machines after I plugged it in and formatted it for Time Machine. I've not heard of it happening the other way around. If there's no backup, there's only a couple of things I can think of doing:
-Writing down your downloaded apps on a list (by hand), and reinstalling them after, tedious I know, but it's way quicker than burning them onto DVDs and all that fandango..
-If you have a spare PC, plug in your iPod (or mp3 player) and manually move all the music over.. Ie, opening the device in My Computer as a portable media device, and copying all the songs over to another folder on the Windows HD.
-Borrowing someone else's back up? Or a spacey memory stick to transfer your music? (Like 2GB plus or something... depending on how much music you've got.)
When I first got my mac, I was under the impression that you could just plug your iPod into the new mac, fresh installed, and it would read all your music.. I don't know why, but it doesn't work.
But seriously... Don't re-install until you back up :S

Unless someone else can think of another way to reformat your external hard-drive..?
Does it recognise it at all when you plug it into OS X?

---

### Post by Jack Hollister on 2008-05-27
If I can format the external hdd to the time machine format like you said I should be able to backup, But when I look for the format option there isnt one :/

---

### Post by sabamanga on 2008-05-27
Hmm... I'm just consultion my own external.. 1 sec.. I'm sure there's something you can do..
If it worked once I can't see why it won't work again.
What make is your external? You might be able to find OS X support for it outside this forum..?

---

### Post by sabamanga on 2008-05-27
> **Jack Hollister said:**
> If I can format the external hdd to the time machine format like you said I should be able to backup, But when I look for the format option there isnt one :/

I think I found it..
Good old disk Utilities.

Type it into spotlight, open it up, select your external hard-drive from the list.. It should have a different icon to all the other hard-drives..

Click on the first aid tab.. and press the 'verify disk' button. If it's not the right format, that's good (in this case), then you can just click repair underneath, and it should put it in os x journaled format for you..

Otherwise erase it, eject it, plug it in again, and see what happens?
I'm not sure if that'll work, if you've got important backups on there.. maybe it's not such a good idea :S

---

### Post by cyberdork33 on 2008-05-27
> **sabamanga said:**
> Boot camp only panders to Windows in that respect... After you change the partition you created for Windows to anything other than an NTFS or FAT32 system, boot camp doesn't want to know.

You can still use bootcamp, but it is is kind of a strange process... if all your Ubuntu partitions have been turned into free space, the bootcamp assistant should allow you to create a new bootcamp partition. Go ahead and create a very small bootcamp partition. After it is done and you have rebooted, start the bootcamp assistant again, and restore the disk to one partition again. This will cause it to fill up the remaining empty space as well.

you can also resize from the OSX commandline using 'diskutil resizeVolume', but that is not as user friendly

---

