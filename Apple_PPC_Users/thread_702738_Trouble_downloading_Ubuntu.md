---
title: "Trouble downloading Ubuntu"
date: 2008-02-20
forum: Apple PPC Users
---

### Post by gscott40 on 2008-02-20
I posted this earlier today on the support site...is that Launchpad?
There don't seem to be to many G4 users there.

I am now looking for information. Yesterday I posted a problem downloading Ubuntu for the Mac G4. Files download and then before expansion of the .iso file a warning indicating the file is damaged....no mountable files... pops up. This occurs no matter which mirror I use, which Macintosh computer I use ( I have several, towers, minis, and an Intel duo MacBook), or which browser, Safari or Firefox. I have tried both http and ftp protocols and I checked the file with MD5SUM (I think that's correct) and the file checks good....but will not mount after burning to a CD. I am using Mac OS X 10.4.11. I also downloaded the latest version of Stuffit Expander and received the same result.

**AM I THE ONLY ONE HAVING THIS PROBLEM???:?:**

Is there someone out there with a Mac that will try downloading ubuntu-6.06.1-desktop-powerpc.iso and see what happens. Can you unpack it and not get a warning about damaged files? I would like to know if someone else will have the same problem I am having. MY SANITY IS IN QUESTION.

George
[email]gscott40@comcast.net[/email]

---

### Post by paxswill on 2008-02-20
IIRC, I got this same error when I last tried mounting my disc images, but they still boot and install fine.

---

### Post by stream303 on 2008-02-21
The good news:  you're not going crazy!

ISO images need to be burned in a special way, not extracted and copied to a cd.

Just use Apple's disk-utility to burn the iso.

( If you are using Windows, I like the simple windows isorecorder
[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm))

With disk-utility open, drag your downloaded iso image into the left pane of disk utility.  Highlight it.  Then click the burn icon.

Depending on the integrity of your drive, or if you plan to install onto slower machines, you may want to reduce the speed of the burn to half or even slower.

I've heard that on older OSX boxes, disk-utility is called disk-copy, and that sometimes it will not verify a burn, yet the disk is ok.

Try that and let us know how it goes...

---

### Post by gscott40 on 2008-02-21
Thanks for the information....I burned it correctly. Unpacked the iso file and used disk utility to burn an image of the contents of resulting folder but......it doesn't mount when I restart the Mac.
I am going to try again and see what happens.

George

---

### Post by gscott40 on 2008-02-21
Wait a second I reread the reply and maybe I'm not doing it right....I have been upacking the contents and, not buring them to a CD, but burning an image of them. I read your reply to say that I should burn an image of the downloaded iso...which I am trying right now.

George

---

### Post by paxswill on 2008-02-21
If you're still having trouble, I have some directions.
[LIST=1]
[*]Insert a blank disk
[*]When the dialog pops up asking what you want to do, select "Open Disc Utility"
[*]Drag the Ubuntu image you downloaded into the lower portion of the left portion of the the main window of Disc Utility (The white area)
[*]Then, click on the Ubuntu image (single click, to select it)
[*]Then click "Burn" in the toolbar
[*]Select your options (A slower burn speed is recommended)
[*]Twiddle your thumbs
[*]Tada!
[/LIST]

---

