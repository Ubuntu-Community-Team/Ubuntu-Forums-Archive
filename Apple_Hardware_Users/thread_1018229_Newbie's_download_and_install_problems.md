---
title: "Newbie's download and install problems"
date: 2008-12-21
forum: Apple Hardware Users
---

### Post by People Person on 2008-12-21
I am attempting to use Ubuntu for the first time and I am having trouble from the get-go. I have an imac G3 from 2000, so I am using the links for the ppc downloads. I've tried downloading feisty, hardy, and gutsy on a different computer (imac G5 using Safari) but each time I get a message once the download is completed saying the file is damaged or may damage my system. Is there something I'm doing wrong?

Thanks in advance for any help that you can give. I've seen the threads on installing on old imacs, so I'm trying to do this as best I can without having my hand held throughout the whole process.

---

### Post by albinootje on 2008-12-21
> **People Person said:**
> I am attempting to use Ubuntu for the first time and I am having trouble from the get-go. I have an imac G3 from 2000, so I am using the links for the ppc downloads. I've tried downloading feisty, hardy, and gutsy on a different computer (imac G5 using Safari) but each time I get a message once the download is completed saying the file is damaged or may damage my system. Is there something I'm doing wrong?

Thanks in advance for any help that you can give. I've seen the threads on installing on old imacs, so I'm trying to do this as best I can without having my hand held throughout the whole process.

See here as a good introduction :
[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714)

And this looks like a good iso image to download and burn :
[http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-desktop-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/hardy/release/ubuntu-8.04.1-desktop-powerpc.iso)

Make sure you burn the iso image as an iso image and not as data.
[http://www.psychocats.net/ubuntu/maciso](http://www.psychocats.net/ubuntu/maciso)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
GL!

---

### Post by People Person on 2008-12-21
So far every iso that I've tried from the ppc download page has produced a "Damaged or may damage your system" message. I've also checked the MD5 hash for each one and none match up with the current hash list.

---

### Post by stream303 on 2008-12-22
Right, so it is happening as soon as the download finishes...

Hmm..  Is there an option in Safari to just save the file, and not "save and run immediately after download" ?  I'm wondering if it is immediately trying to "run the iso" you have just downloaded.  I'm not a safari expert, but I seem to remember having to turn that option off for most of what I do.  Just save it for me, don't run it. :)

What puzzles me is the md5sum mismatch.

How about downloading Firefox, and using that browser to download your files with and see if that makes a difference.

I know it doesn't sound scientific. :)  I'd probably try this first - I wish I had something specific I could point to.

---

### Post by SlidingHorn on 2008-12-22
> **stream303 said:**
> Right, so it is happening as soon as the download finishes...

Hmm..  Is there an option in Safari to just save the file, and not "save and run immediately after download" ?  I'm wondering if it is immediately trying to "run the iso" you have just downloaded.  I'm not a safari expert, but I seem to remember having to turn that option off for most of what I do.  Just save it for me, don't run it. :)

What puzzles me is the md5sum mismatch.

How about downloading Firefox, and using that browser to download your files with and see if that makes a difference.

I know it doesn't sound scientific. :)  I'd probably try this first - I wish I had something specific I could point to.

Most browsers have a "Save target as..." option if you right click on a link

---

### Post by mkvnmtr on 2008-12-22
I realized reading this post that I had never used Safari to down load a Linux distro. I always used Firefox or Camino. I have downloaded maybe 50 and never had a problem. Maybe another browser or a download manager will solve your problem.

---

### Post by People Person on 2008-12-23
Thanks to everyone who replied to my post. I had success dowloading with Ubuntu 8.04.1 desktop with Firefox and I was able to boot it on my G3, but when I pulled up the xorg.conf file I did not see "HorizSync" or "VertRefresh" in the Monitor section. Instead, I saw:

Identifier "Configured Monitor"

Also, there wasn't a Modules section at all.

Do the instructions cited for a blank screen on an iMac G3 only work with specific Ubuntu releases?

I've already tried booting Gutsy and all I could get after typing different combinations of 
"live-nosplash" and "video=ofonly" was something called BusyBox.

---

### Post by stream303 on 2008-12-24
So, did it come up, or did you have to use a virtual terminal to get to xorg.conf?

Also which machine are you running?

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

With the newer X, the emphasis is to leave more and more out of xorg.conf, and in fact with Intrepid the file is zero!  That hurts us ppc guys who need to edit that file 99% of the time.

But if yours came up ok, let us know which model..

---

### Post by People Person on 2008-12-25
I finally had success the other night with ubuntu-6.06.1-desktop-powerpc.iso. All I had to do was hit enter at the boot prompt and the splash screen came up. The screen then went blank and I was able to follow the instructions for the xorg.conf file from there. I know my iMac is one of the G3/400's. 

I'm so happy just to get it on the computer that I'll probably wait a while to try and update. Thanks to all for your assistance.

---

### Post by levelup3 on 2008-12-30
I am glad to read it here.

---

