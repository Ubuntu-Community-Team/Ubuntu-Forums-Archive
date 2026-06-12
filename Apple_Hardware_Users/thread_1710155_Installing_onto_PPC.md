---
title: "Installing onto PPC"
date: 2011-03-19
forum: Apple Hardware Users
---

### Post by gl.tch on 2011-03-19
I hope this is in the right place. Something tells me you're all probably heartily sick of this kind of thing, but...

I'm looking to install Ubuntu onto my old iBook G4. It runs PPC with 512MB RAM. Usual stuff. The only quirk that it contains [to my knowledge] is that the ethernet port does *not* work.

To start with, I visited the 10.10 release page for PPC, located [here]("http://cdimage.ubuntu.com/ports/releases/maverick/release/") and downloaded the following: ubuntu-10.10-desktop-powerpc.iso, which tells me it is the "Desktop CD for Mac (PowerPC) and IBM-PPC (POWER5) computers (standard download)".

All fine and dandy. I burnt it to CD-R in Terminal using an overburn method I found on these forums; I suspect that this might be the source of my problems, but I don't have a DVD-R lying about.

What I'm now looking to do is to install 10.10 on top of my previous OSX install, wiping all traces of it and turning my machine into a straight Linux box. Upon restarting the machine and holding down C, a screen appears wherein I am prompted to hit return; I duly do so. It's probably worth noting at this point that if I type 'install', I get an error, though hitting return works fine.

The CD drive then proceeds to grind solidly for a couple of minutes, before I reach a screen that says 10.10 with four periods underneath that flick white and red. I believe there is an error message briefly that mentions needing wireless drivers; I assume that, were my ethernet port live, it would automatically obtain these. Perhaps.

Finally, the desktop environment seems to load. At no point has there been any real install dialogue. It seems that I have managed to load up the desktop environment from the CD rather than actually carry out the full install I wanted to; rebooting the computer results in it happily loading OSX like nothing happened.

I previously investigated a Hard Disk install, but either my computer or my brain were being uncooperative and I couldn't work out which. If this could be got to work, then this would probably be ideal, but it's been my impression that this requires a working ethernet port.

So - the big question - What Do? I've read the FAQ, and it didn't seem to help very much. If there is, somewhere, a topic that I missed in my search through poor choice of terms or simple ignorance, then please point me to it and I shall cease to bother you!

Cheers for your time and patience.

---

### Post by snafu006 on 2011-03-19
If its booting to a desktop that means every thing is going fine on the decktop you should see a icon saying install even tho you are running the live cd part you can install from here you next problem might be the wireless drivers and even the screen. Reboot the computer hold options as soon as the computer restart after a sec you should see the ubuntu cd icon click to and if you take you back to desktop install from here.

The installer will ask you if you want to use full hard drive or part just use full and fallow the rest of the install.

---

### Post by gl.tch on 2011-03-20
> **snafu006 said:**
> If its booting to a desktop that means every thing is going fine on the decktop you should see a icon saying install even tho you are running the live cd part you can install from here you next problem might be the wireless drivers and even the screen. Reboot the computer hold options as soon as the computer restart after a sec you should see the ubuntu cd icon click to and if you take you back to desktop install from here.

The installer will ask you if you want to use full hard drive or part just use full and fallow the rest of the install.

You are a hero and a gentleman, sir!

It's not installed; no real problems there as far as I can tell. Only two issues remain that, frankly, I am utterly stumped on.

1] Wireless
2] Trackpad

To address a common issue to them both: I was unable, during install, to tell it to download the necessary firmware/software/etc that it needed to get things to work seamlessly, due to the aforementioned ethernet port which, though apparently recognised under both Linux and OSX [appearing at En0, as I recall, or something similar] it remains stubbornly lifeless. In fact, evening opening the network settings dialogue pane resulted in a hard freeze; a force-shutdown and restart was required! This results, obviously, in not having what I need.

I have, at my disposal, a couple of Windows machines running Vista and Seven respectively, various flash drives, a couple of external HDDs, and enough CD-Rs to back up Wikipedia. Is there some way of downloading the software/firmware I need to one of my other machines, dumping it onto an external drive, and transferring it that way? If so, advice on where to find such packages and install methods would be much appreciated.

I am led to believe that both the trackpad and the wireless are known issues, so to speak, and that the wireless one can be completely solved and the trackpad one virtually solved.

Again, my thanks for your patience and help.

---

### Post by snafu006 on 2011-03-20
you need to install ubuntu befor every this will start to work

---

### Post by gl.tch on 2011-03-21
> **snafu006 said:**
> you need to install ubuntu befor every this will start to work

Oh, I'm very sorry - my wayward typing replaced 'now' with 'not'!

It's installed without issue, apart from the wireless/trackpad issues I mentioned above which are, of course, due to my completely bricked ethernet port!

Sorry for the confusion.

---

### Post by snafu006 on 2011-03-21
[http://ubuntuforums.org/showthread.php?t=1705143](http://ubuntuforums.org/showthread.php?t=1705143) Go to this post it might help you with your wireless.

---

### Post by pauljwells on 2011-03-21
Installing software from CDs and USB sticks is a pain :-) You may not know but Ubuntu has built-in support for the 3G dongle modems (Huawei) that you can get from Vodafone, 3, O2 etc. All you need to do is borrow one of these long enough to let your install find proprietary drivers for the wireless card and then you can use wifi for everything else.

---

### Post by rsavage on 2011-03-21
You only have to download drivers if you have an airport etreme card.  If you follow the link snafu006 gave and then follow the links in the first and third posts then there are directions to download drivers without an ethernet cable.  My concern is though that network manager is crashing so how are you going to set wirless up anyway?  I haven't heard about problems with ethernet before, and I thought I had read all problems with  G4 ibooks.  I certainly didn't have a problem my ethernet port.

There are a few things you need to tweak to get Ubuntu working perfectly with a G4 ibook.  The most important is to get the fans to work.

---

### Post by gl.tch on 2011-03-23
More trouble in paradise, I'm afraid...

I've found a guide to installing without internet access; it can be found [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access").

Essentially, I'm attempting to install b43_fwcutter from USB; the USB contains a complete mirror of the install CD [simply because the CD drive has apparently decided not to read anything] but unfortunately, it attempts to connect to the internet *anyway*.

Neither using the graphical install nor using the Terminal seems to fix this.

Is this a lost cause? ;)

**[Edit] In an entirely inexplicable turn of events, the above is now no longer true. Wireless connectivity is obtained; thanks, all of you, for your help. You've been invaluable!**

---

