---
title: "Advice needed for iBook G4"
date: 2006-06-16
forum: Apple PPC Users
---

### Post by bogoliubov on 2006-06-16
I'm running Dapper on my PC and I'd like to dual-boot my iBook G4. But before  taking this step I have some questions that I hope someone here can answer.

Let me first explain what I'm using the iBook for. I use it for "normal stuff", such as browsing, playing some games, e-mail, etc..
I also use it for work, which means hanging around in terminals all day, plotting in xmgrace, calculations with octave, writing in latex and so on. So for work I need many *nix things. 

My main concern about OS X is that iTerm is the only decent terminal and it's darn slow (and a little buggy). I also dislike the lack of 3rd mouse button functionality.
Also, I think it'd be cool running Ubuntu on my Mac.

1. I have Tiger installed. Can I just install Ubuntu "on top", ie create a Ubuntu partition without formatting the HD? If so, can I later on remove the Ubuntu partition without formatting the HD?

2. If I have to format the HD (usually easiest), then is it possible to have one /home or /Users that can be shared between Tiger and Ubuntu? What filesystem should I use for that partition (or for any shared partition) ?
Also, which OS should I install first (my guess would be Tiger) ?

3. Can I run any 3rd party applications (for OS X) in Ubuntu?

4. How well does "Mac on Linux" work for Ubuntu on iBook G4? What about memory requirements?

5. What about 3d acceleration? I have ATI 9200...

---

### Post by autumnsweater on 2006-06-16
Well, I sort of have an answer for 1. You can indeed preserve your Mac partition by shrinking it, creating space for an Ubuntu partition. The way I did it was to first download the server install, since it has the text-based installer. I followed the instructions from [this thread]("http://www.ubuntuforums.org/showthread.php?t=89960&highlight=resize+hfs+parted"), and it worked fine, although I will say that mine took a good bit of time to resize (20-30 mins), while the posts here report it only taking seconds.

---

### Post by AlphaMack on 2006-06-16
I had qualms about dynamically resizing my partition especially after reading about the failures.

What I did for my PowerBook was the following:

- Backed up /Users to external.
- With the Tiger install DVD, I completely erased my HDD and zeroed all data.
- Created 3 partitions.  First one was for OS X and formatted as HFS+ journaled.  Second partition for Ubuntu formatted as free space.  Third was for all of my shared files and formatted as HFS+ WITHOUT journaling.
- Installed OS X Tiger first and set it up (copied back my settings, files, etc.)
- Installed Ubuntu using the ALTERNATE installer (text-based).  At the partitioning step I allowed the installer to automagically partition the free space then went back and created a /home partition.
- Once Ubuntu was set up I edited my /etc/fstab to have the shared partition mount automatically upon bootup.

In the end my partitions were set up like this (100 GB HDD):

- 33 GB OS X
- 7 GB Ubuntu (5 GB for / and 2 for /home)
- 60 GB HFS+

---

### Post by bogoliubov on 2006-06-16
[QUOTE=alphasubzero949]
- With the Tiger install DVD, I completely erased my HDD and zeroed all data.
- Created 3 partitions.  First one was for OS X and formatted as HFS+ journaled.  Second partition for Ubuntu formatted as free space.  Third was for all of my shared files and formatted as HFS+ WITHOUT journaling.
[/QUOTE]

Thank's for the advice. One perhaps stupid question: what's the advantage of using journaled filesystem?

Also, I only have a 60 Gb disk at the moment. Is 5 Gb for Ubuntu a reasonable size? What about swap partitions for OS X and Ubuntu?

I'm thinking about replacing the 60 Gb disc with a 100, not just for size but for speed. The 4200 rpm drive that I'm using now is dead slow...

---

### Post by AlphaMack on 2006-06-17
A journal logs all transactions so in the event of a system crash, the next reboot completes whatever was cut off.

With Ubuntu, however, journaled HFS+ is bad because that partition cannot be written to - only read.

5 GB is reasonable for Ubuntu, especially if it's just for /.  You don't need to worry about swap space for OS X as that is handled within the OS X partition itself.  On Ubuntu, if you allow the partitioner to automatically divide the free space you will have a dedicated swap partition.

---

### Post by bogoliubov on 2006-06-17
Thank's for your help. I guess you've tried Ubuntu on a Mac; what are your impressions on the advantages/disadvantages with Ubuntu compared to OS X?

---

### Post by llanitedave on 2006-06-17
The main advantages to OS X, in laptops at least, are ease of networking and the smoothness/speed of the sleep/hibernate function.  Until Dapper, the latter didn't work at all on my iBook.  Now it works, but it's still a little clunky compared to to the native OS X reaction to closing the lid.  Wireless internet reception is a no-brainer on the Mac... almost TOO easy.  I understand that you can get it working on Dapper, but I haven't yet done that.  Later today, I hope.

I'm using an August 2005-model iBook G4.

With regards to software and file system, that's a matter of personal preference, of course.  I prefer OpenOffice.org to either the discontinued Appleworks or the new version, that's even less functional.  Garage Band is a fantastic application, but I haven't used it as much as I'd hoped. Safari has no advantages over Firefox or Konquerer, iTunes has become little more than a fancy trojan horse, Mail is nice but no better than any of the Linux choices such as Thunderbird, and utilities and window navigation is pretty much a wash -- different styles but similar results.  Programmers editors are generally better for Linux, I think than is the Xcode editor.

I like the fact that KDE and Gnome are both more configurable.  I've been a Mac fan for almost 20 years, but I'm seriously thinking that if I can get wireless networking working easily on Dapper with my iBook, I'll just wipe the OS X partition completely and go exclusively with Dapper.

---

### Post by bogoliubov on 2006-06-17
Thank'a lot. What are your impressions on CPU/memory needs? I have Ubuntu on my desktop PC and it doesn't seems to use so much memory as OS X, but since I'm talking about two different computers it's not a very good comparison...

---

### Post by AlphaMack on 2006-06-18
[QUOTE=llanitedave]The main advantages to OS X, in laptops at least, are ease of networking and the smoothness/speed of the sleep/hibernate function.  Until Dapper, the latter didn't work at all on my iBook.  Now it works, but it's still a little clunky compared to to the native OS X reaction to closing the lid.  Wireless internet reception is a no-brainer on the Mac... almost TOO easy.  I understand that you can get it working on Dapper, but I haven't yet done that.  Later today, I hope.

I'm using an August 2005-model iBook G4.

With regards to software and file system, that's a matter of personal preference, of course.  I prefer OpenOffice.org to either the discontinued Appleworks or the new version, that's even less functional.  Garage Band is a fantastic application, but I haven't used it as much as I'd hoped. Safari has no advantages over Firefox or Konquerer, iTunes has become little more than a fancy trojan horse, Mail is nice but no better than any of the Linux choices such as Thunderbird, and utilities and window navigation is pretty much a wash -- different styles but similar results.  Programmers editors are generally better for Linux, I think than is the Xcode editor.

I like the fact that KDE and Gnome are both more configurable.  I've been a Mac fan for almost 20 years, but I'm seriously thinking that if I can get wireless networking working easily on Dapper with my iBook, I'll just wipe the OS X partition completely and go exclusively with Dapper.[/QUOTE]

Quoted for emphasis as these are pretty much my feelings about Ubuntu on Mac hardware.

I've installed Ubuntu on 4 machines - 2 Macs and 2 PCs - each of them with different quirks from the hardware to functionality.  I pretty much have the PC side under control but the Macs have been more of a challenge for the reasons quoted above.

One thing I would suggest is to try playing around with FOSS apps in OS X (Firefox, Thunderbird, the GIMP, etc.).  If you learn them easily enough (and even like them), you'll have an easier transition to Ubuntu.

---

### Post by bogoliubov on 2006-06-18
Now I've installed Dapper; dual-boot with Tiger. Can you point me to some howtos on soundcard, 3d acceleration and wireless network? I'd really appreciate it!

---

