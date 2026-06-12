---
title: "Ubuntu on Mac OS X - Alone or Dual???"
date: 2009-07-26
forum: Apple Hardware Users
---

### Post by feveryear on 2009-07-26
I've been away from the Linux community for some time, when I dropped out of college and got a full time job. I since then saved up for a MacBook Pro, and came to find out, even though Mac OS X was notably better than Windows in my opinion, Ubuntu is the best OS for me still! 

So I tried to get it to dual boot. I even tried to follow the detailed directions for my specific MBP. It will install, but I have one major issue. rEFIt doesn't let me boot into Ubuntu. Now, I installed GRUB to hd0 by accident, not going to the step of (hd0,3), and then I started back over and made sure GRUB got installed to (hd0,3). Is that difference a huge problem? How can I fix that? So far it hasn't proven bad for me. The problem is I installed Ubuntu, and if I turn off the MBP and then start it up holding down the OPTION key, I'm able to boot into Ubuntu. If I let rEFIt show up, and I select the Linux option, it shows me a grayed Tux and then just goes black-screened and freezes. I've not gotten any further than that!

I love Ubuntu. I've heard that it's a good idea to keep OS X just in case of firmware updates. I honestly don't care, if my MBP works without those firmware updates then I wouldn't be too concerned about keeping OS X just for that. So my question is, if rEFIt has a solution, what is it? Or can I just altogether get rid of OS X and keep Ubuntu as a single boot, ignoring whatever firmware updates Apple may send my way?

Thanks in advance for the help.

---

### Post by feveryear on 2009-07-26
Well, I just took the plunge, backed up my files and wiped my MBP and completed a clean install of Ubuntu 9.04. I'm still configuring things as per the awesomely detailed How-To that is available. 

Just a few questions!

The sound now works, but it is VERY quiet, even when I have the volume maxed out.

Also, at the end of the [tutorial]("https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty") it talks about the EFI. Is that something I need? I'm not really sure of the importance of that part. I noticed that when I unplug my charger from the MBP, I do only have about 1:40 remaining on the battery, so I was afraid I may have to slug my way through the EFI part, although it seems dangerously confusing.

Any help on these two matters is greatly appreciated.

---

### Post by russo.mic on 2009-07-26
I have to say I recommend keeping an OS X installation on the MBP for if nothing else firmware updates.  Beyond that, it so many times has come in handy to have a OS X installation laying around.  For that jerk who brings you a HFS+ formatted flash drive EVEN though you told him to make it FAT32, or whatever.

---

### Post by rjcalifornia on 2009-07-28
I recommend both. I dual boot 'cause sometimes I use photoshop and other apps that are not on Linux.

---

### Post by Brightbelt on 2009-07-29
Hi Feveryear,
  
I could be wrong but my understanding is that you only need rEFIt if you're setting up a dual or triple booting situation.

Given that you've wiped out OSX and have only Ubuntu installed at this point, (That's my understanding of what you said), rEFIt is probably no longer necessary.

Good Luck.

---

### Post by raronson on 2009-07-29
Yes, Bright, that's correct.  rEFIt only works if you have an OS X install, or an HFS+ formatted partition on which to put it.  However, there's really no need because in the absence of an EFI boot partition, the system will default to "legacy mode" and behave like a traditional BIOS.  The only drawback is that there's a 30 second timeout, i.e., the gray screen while the macbook looks for OS X.  This can be bypassed by pressing alt, but even then it still makes for slow booting.  rEFIt dual booting takes just as long.  In essence, after a short gray screen pause, rEFIt 'presses alt' for you and lets you choose between OS X and whatever else is installed.

I'm testing Karmic right now on a macbook4,1 using Grub2 which has EFI booting capabilities, but so far, I haven't heard if anyone has this working with Apple's somewhat custom implementation of Intel's EFI standard.  Surely in the future, it'll work like a champ, so hold tight.

As for firmware updates, I just applied all the current ones before I reformatted and installed Ubuntu with no OS X.  I'm still kind of frosty about an old firmware update that killed my dvd superdrive (can't read DVD movies--everything else works).  The hardware works well enough in my estimation until the end of this laptop's life cycle.

Like you though, OS X was not for me.  It's a fine OS and light years ahead of Windows, but I just prefer Linux.  The UNIX mix under the hood didn't really fit my needs, and using Macports or fink to complete the environment just ends up being messy.  One example is a package, let's say, that needs a newer version of python than the OS X system default.  It will install that new version for the target package.  This leaves you with two pythons (granted, OS X is smart enough to sort it out by putting all the macports in /opt, which separates it from the default system).  There's UNIX under there for sure, but it's just-UNIX-enough to drive the hardware and GUI.  I'm ranting...

You're not alone.

---

### Post by Dullstar on 2009-07-29
Right now, I have to say if I wanted Ubuntu only, I'd probably get a laptop with Linux preinstalled as opposed to getting a MacBook.  I have an iPod and a few Mac compatible games, so I would prefer a dual boot.  It's not that I would keep OS X because of firmware updates, I'd keep OS X because I like it.  Ubuntu was originally my replacement for Micro$oft Windoze.  This was because I can't get this computer replaced yet.  I've used OS X before, and it is light years ahead of Windows!  Now comparing between that and Ubuntu?  I'll find out.

---

### Post by feveryear on 2009-07-29
Yeah, I wiped out OS X and went for straight Ubuntu. For some reason my Battery Power stinks, but I tend to keep my MBP at my desk nowadays, I'm not a mobile nerd anymore since I have a Public Works Labor job. That's good to know about rEFIt, thanks! Oh, and raronson, I found that trick on how to Bless the Ubuntu partition using the Mac OS X DVD, and so the gray screen only lasts about 3 seconds. I'm slowly but surely getting everything settled into.

I'm not too big on programming, but I do some Java programming every once in a while, when I find a need that I want a specific setup for an app of my own design. Otherwise, I've always preferred the ultimate customization of appearance, performance, and security. 

There are a few quirks of the system, like the touchpad hack that enables the actions like the MacBook Pro for right click and such, but enabling that hack disables the click and drag feature for resizing, or moving files on the desktop. So I use an external mouse.

For such PROS from a system, and a FREE system, and a system the way I want it, I don't mind doing some manual setting up.

---

### Post by raronson on 2009-07-30
I'm still working out the blessing.  My DVD drive won't read the install disk anymore, so I'm trying out the firewire trick using my wife's macbook (still a work in progress).

Good news for your touchpad though--I'm testing Karmic, and they've updated the gnome-mouse-properties applet to include two-fingered scrolling (vertical and horizontal) and disable touchpad while typing.  As for gestures on a MBP, I can't say for sure.  You might still need to make an fdi policy file for the appletouch module.  With the new applet though, I was able to delete my custom file.  A lot of small irritations were fixed as well with the pad.  So when Karmic is released in October, hopefully everything will work out of the box.

There was another thread recently about extending battery life on a MBP in the Apple forum.  I gave it a quick glance and it seemed to be a pretty comprehensive howto.  I just need the time to give that another look over.  It also touches on improving suspend-hibernate, so you may have want to give that a look if you haven't already.

Good luck.

---

### Post by feveryear on 2009-07-30
I'll have to check that out. I went through the HowTo for installing Ubuntu onto a MacBookPro5,1 and it had me create a .fdi file. The touchpad works alright, although I'm very interested in Karmic and I'll have to try that out, but when it comes to the touchpad, using that .fdi file, whenever two fingers are touching the pad, it automatically assumes a right click. I can't grab a window's title bar and drag the window over to the other side of the desktop to get to an icon on my desktop. That's my biggest problem. I'll have to look into Karmic though, and I'll search around tonight for that topic about the Battery, especially if it has some stuff for Suspend/Hibernate.

---

### Post by raronson on 2009-07-30
[http://ubuntuforums.org/showthread.php?t=1215928](http://ubuntuforums.org/showthread.php?t=1215928)

There's the battery life thread for the macbook pro.  Hope it helps you out.

---

### Post by MikeTheC on 2009-07-30
Sorry to hear about you dropping out of college. Hope you can get back in soon.

---

