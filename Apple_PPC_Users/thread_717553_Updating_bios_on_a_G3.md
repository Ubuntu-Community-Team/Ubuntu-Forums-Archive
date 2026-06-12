---
title: "Updating bios on a G3"
date: 2008-03-07
forum: Apple PPC Users
---

### Post by djbsteart1 on 2008-03-07
I looked at the apple update site and I couldn't really get anything from it, the file comes as a .bin, but as the computer doesn't have an os on it, I don't know how to install the update. I have tried install 6.06, but there is no option to edit the bios boot parameters, and holding down c doesn't help.

---

### Post by linear on 2008-03-07
Your first problem is that PPC Macs don't have a bios.

If the 6.06 CD is not recognized as bootable, there are a number of possibilities:

The Mac's CD drive is bad.
The CD was burned at too fast a speed, or is corrupted.
The .iso was corrupted during download.
The .iso wasn't burned to the CD as an image.
The keyboard is not an Apple keyboard, or is connected to a hub.

---

### Post by djbsteart1 on 2008-03-07
The keyboard is apple, and wasn't through a hub, I will re download the image and burn at 2x to make sure, well they have have something and for lack of a better word I called it a bios, firmware better? I don't think that the drive is bad as it had been running  OSX9 very recently, and on my second G3 which still boots OSX9 the cd wasn't recognized. 
Thanks for the help, I will report back when I have results.

---

### Post by stream303 on 2008-03-07
From what I understand, the firmware update can only be applied from a working older mac-os install from a hard disk.  You can get the docs and the upgrade file here

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

You could reload mac-os on the one that doesn't have it, and try again.  If they are similar, and you can't reload it for some reason on the old one, I've heard about the trick of doing the update, and then swapping the daughtercards around.

got that from

[http://www.lowendmac.com/imacs/index.shtml](http://www.lowendmac.com/imacs/index.shtml)

Hope this helps...

---

### Post by djbsteart1 on 2008-03-08
> **stream303 said:**
> From what I understand, the firmware update can only be applied from a working older mac-os install from a hard disk.  You can get the docs and the upgrade file here

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

You could reload mac-os on the one that doesn't have it, and try again.  If they are similar, and you can't reload it for some reason on the old one, I've heard about the trick of doing the update, and then swapping the daughtercards around.

got that from

[http://www.lowendmac.com/imacs/index.shtml](http://www.lowendmac.com/imacs/index.shtml)

Hope this helps...

I had thought that that was the case. I guess that I only have the daughter board option as I don't have a copy of any apple OS's, forgive me for sounding ignorant, but how do you switch the daughter boards, they aren't exactly accessible?

---

### Post by stream303 on 2008-03-08
Well, lets sort out some details.

Which model of G3 mac do you have?  You have two identical units?  How much ram do they have?  this might help identify it:

[http://www.everymac.com/](http://www.everymac.com/)

One of them still runs mac-os on it from the hard drive?  We can at least update that machine with a bios upgrade to install Ubuntu with.  The other one might be a bit trickier, although, but if the machines are identical, you might be able to swap the hard drive and do a firmware upgrade that way.   I'm not sure about your daughtercard until we find out what you have.

Also, what technique / utility are you using to burn your iso images with?  Are you just copying the file over, or doing a special burn?

---

### Post by stream303 on 2008-03-08
Now I'm officially freaked out by the firmware upgrade!

Has *anyone* installed Ubuntu on a G3 iMac, *without* doing a firmware upgrade?  Have you been left with a non-working unit after attempting this??

I've been reading about how if you try to install OSX without doing a firmware update with the original mac-os on the hard drive,  the OSX installer will warn you that you need to upgrade the firmware, but then leave you in a non-working state!  And then if you try to zap the pram, you are really hosed!

[http://www.gileskennedy.com/panthereatsimac](http://www.gileskennedy.com/panthereatsimac)

Will Ubuntu do the same?  I'm just wondering if those who have installed Ubuntu have just been lucky since maybe they have upgraded their firmware previously?

I'm a bit paranoid about this whole situation now...

---

### Post by stream303 on 2008-03-08
Now I really can't wait to get my hands on a G3 iMac.

I'm starting to wonder if this firmware update situation is somewhat of a non-issue for those of us who install Linux with an "alternate" image, and then proceed to just edit our /etc/X11/xorg.conf manually to make sure that the horizontal and vertical frequencies are in the proper range for an early iMac.

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

From what I've been reading, these installs of OSX 10.2 and higher (or attempting to use certain OSX utility disks when you haven't run the firmware update) reset the video frequencies, which are wrong. and tend to just shut down the monitor, or if left in that state, fry the video board.

So in our case, assuming that the board isn't fried, merely editing our xorg.conf file with the right freqs brings it back to life.  This might explain why the initial probing during install doesn't get the freqs right, and forces us to manually edit the xorg.conf file.  Hmmmmm.....

All conjecture on my part....

---

### Post by djbsteart1 on 2008-03-10
> **stream303 said:**
> Now I really can't wait to get my hands on a G3 iMac.

I'm starting to wonder if this firmware update situation is somewhat of a non-issue for those of us who install Linux with an "alternate" image, and then proceed to just edit our /etc/X11/xorg.conf manually to make sure that the horizontal and vertical frequencies are in the proper range for an early iMac.

[https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8](https://wiki.ubuntu.com/PowerPCKnownIssues#head-cae29299476585f042f0185bea1d51b9372722c8)

From what I've been reading, these installs of OSX 10.2 and higher (or attempting to use certain OSX utility disks when you haven't run the firmware update) reset the video frequencies, which are wrong. and tend to just shut down the monitor, or if left in that state, fry the video board.

So in our case, assuming that the board isn't fried, merely editing our xorg.conf file with the right freqs brings it back to life.  This might explain why the initial probing during install doesn't get the freqs right, and forces us to manually edit the xorg.conf file.  Hmmmmm.....

All conjecture on my part....


From what I have gathered the firmware update might not be essential, it is just something I want to do out of houskeeping. I think that they are different versions as they have different colours and sspecs but I could be wrong, I will try a new iso tonight and see it that helps.

---

### Post by linear on 2008-03-10
> **stream303 said:**
> Has *anyone* installed Ubuntu on a G3 iMac, *without* doing a firmware upgrade?

Yes. Although it may not have needed one. This was a slot-loading iMac, and so came with OS X in addition to OS 9.

---

### Post by stream303 on 2008-03-10
> Yes. Although it may not have needed one. This was a slot-loading iMac, and so came with OS X in addition to OS 9.

This is good to know. I suspect that while the firmware updates are good overall, they might not be mandatory as we can fix the vertical and horizontal freqs ourselves.  It would be interesting to see if the updates are necessary when doing *major* ram upgrades or hard drive upgrades..

It does appear that there are different versions of update depending on model.  Luckily this link takes you right to the ones that are needed so you don't have to hunt around:

[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

---

### Post by 3rdalbum on 2008-03-11
> **stream303 said:**
> 
From what I've been reading, these installs of OSX 10.2 and higher (or attempting to use certain OSX utility disks when you haven't run the firmware update) reset the video frequencies, which are wrong. and tend to just shut down the monitor, or if left in that state, fry the video board.

So in our case, assuming that the board isn't fried, merely editing our xorg.conf file with the right freqs brings it back to life.  This might explain why the initial probing during install doesn't get the freqs right, and forces us to manually edit the xorg.conf file.  Hmmmmm.....

All conjecture on my part....

Nice theory, but Mac OS X has never been booted on my iMac, and that had the Xorg.conf problem. At least, it had the problem on the Breezy live CD, but everything was completely set up on the Alternate CD install.

Feisty didn't require any tweaking!

---

### Post by djbsteart1 on 2008-03-11
> **3rdalbum said:**
> Nice theory, but Mac OS X has never been booted on my iMac, and that had the Xorg.conf problem. At least, it had the problem on the Breezy live CD, but everything was completely set up on the Alternate CD install.

Feisty didn't require any tweaking!

Thats good to know, I will report on feisty when i get home and hopefully that will; be all positive, thanks for the help, and I look forward to blowing my macs up.......

---

