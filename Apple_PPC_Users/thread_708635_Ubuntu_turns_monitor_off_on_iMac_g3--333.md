---
title: "Ubuntu turns monitor off on iMac g3--333"
date: 2008-02-26
forum: Apple PPC Users
---

### Post by calexand on 2008-02-26
I know that there are numerous posts regarding the "black screen" problem with this particular version of iMac, but I haven't seen one pertaining to my woe...
Sorry if a re-post of sorts.
Booting from the Live PPC version of Ubuntu 6.10, the machine gets all the way to the installer GUI and turns the monitor off(?).  It has 320 megs ram and has had all Apple firmware updates applied.
The only way to bring it back to life is a reboot.  Any help is appreciated, this is my Daughters' machine and she is smitten with the way Ubuntu works on my B/W g3 (G4 upgrade, 512 megs ram, Radeon 7500, 19" LCD).
Thank you.
CA
:confused:

---

### Post by stream303 on 2008-02-26
Live-cd's are a drag. :)  I'd definitely recommend using an "alternate" installer.  Perhaps Feisty:  I'd burn at a very low speed.

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

We are probably looking at manually editing your /etc/xorg.conf file in any case to make sure that the Horizontal Sync is 58-62, and the Vertical Refresh is 75-117

In addition to that, your early iMac may have to be partitioned so that Ubuntu resides inside of 8gb.  If that is the case, there are options to use the rest of the disk with manual partitioning etc.  [www.everymac.com](www.everymac.com) shows that this comes with a 6gb standard drive, so if that is the case, and you don't mind a total dedication to Ubuntu, maybe use "the whole disk" when guided partitioning prompts you.  Just don't hold me responsible if you don't have the old mac restore disks. :)

Definitely give any of the alternate installers a shot, and let us know how it goes!

---

### Post by stream303 on 2008-02-26
Yikes!  did you really mean 320mb of ram, or just 32mb which was the default amount?

---

### Post by 3rdalbum on 2008-02-27
You should probably try the unofficial 7.04 build; it has fixed this bug.

It's been a long time since I have typed in all the stuff to fix this problem, so I don't remember exactly. But if you do a search for "imac blank screen" on this forum, you'll find the answer.

---

### Post by calexand on 2008-02-27
Yep, 320 megs of installed ram. Sorry it took awhile to answer, for some reason I am not getting notices about any postings to this thread, besides the initial post/answer.
That did not help as the monitor turns completely off and will not wake...
Where would one aquire the unofficial build of version 7.04?
TIA,
ca

---

### Post by stream303 on 2008-02-28
Ok, that should make a fine machine for Ubuntu or perhaps a lighter-weight alternative, Xubuntu.  The catch-22 being the monitor totally shuts off so you can't see what you type to fix it. :)  At least with the "alternate" images, you should be able to get it all installed without shutting down the monitor, and then we can take it from there if it still acts up.

"Official" refers to officially-supported, such as 6.06x dapper versions, whereas while the Feisty and Gutsy versions are available, they are just "unofficially" supported, and can be downloaded at a different site than the worldwide official release mirrors.  Saves a lot of space out there in mirror land.

You can grab Ubuntu Feisty here:

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

or perhaps Xubuntu Feisty which might be a bit snappier in performance on that machine here:

[http://cdimage.ubuntu.com/xubuntu/ports/releases/feisty/release/](http://cdimage.ubuntu.com/xubuntu/ports/releases/feisty/release/)

Be sure to get the "alternate" image so it won't shut your monitor down prematurely.  I'll look into that shutdown situation.

Looks like we may have to disable dri in xorg.conf as well as manually define the vertical and horizontal freqs.  This was nice:

[http://www.yellowjug.com/mac/xubuntu-linux-on-imac-g3/](http://www.yellowjug.com/mac/xubuntu-linux-on-imac-g3/)

---

### Post by 3rdalbum on 2008-02-29
When you press Control-Option-F1 to get to a text terminal, the screen comes back on. So you *will* be able to see what you're typing in.

---

### Post by calexand on 2008-03-07
Sorry it has taken me awhile to get back to you...
My Daughter has sold the iMac and succombed to the Dark Side, she bought a Winbox.
Thank you for the help, but never did get issue resolved.
CA

---

### Post by stream303 on 2008-03-08
> **calexand said:**
> That did not help as the monitor turns completely off and will not wake...

Ok, well the Mac has gone to a new owner.  Maybe they will show up here! :)

That whole issue of the screen turning off sounds like an install was attempted without updating the bios firmware first.  (I'm hoping to get my hands on a G3 soon and was doing some digging around.)

This link about problems with bios updating (and solutions) really opened my eyes:

[http://www.gileskennedy.com/panthereatsimac](http://www.gileskennedy.com/panthereatsimac)

wow.

---

### Post by 3rdalbum on 2008-03-09
Macintoshes do not have a BIOS. They use OpenFirmware.

---

