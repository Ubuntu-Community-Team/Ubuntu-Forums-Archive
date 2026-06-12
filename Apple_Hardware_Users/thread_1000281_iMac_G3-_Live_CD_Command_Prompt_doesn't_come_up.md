---
title: "iMac G3- Live CD Command Prompt doesn't come up"
date: 2008-12-02
forum: Apple Hardware Users
---

### Post by eJoystick on 2008-12-02
Hi,
Excuse me if this is the wrong board. I have an iMac G3, and, of course, I want to boot Ubuntu on it. However, after it boots up, and I type Control+Alt+F1 to bring up the command prompt, nothing happens, except a thing that's like [[^, preventing me from opening the xorg.conf file. Help?
-eJoy

---

### Post by eJoystick on 2008-12-02
Sorry about not explaining my iMac.
Its 350 MHz, 192 MB RAM, OS X 10.2 and OS 9. CD-Drive.

---

### Post by stream303 on 2008-12-02
> **eJoystick said:**
> Hi,
Excuse me if this is the wrong board.

You've come to the right place!

Even though you haven't indicated which release of Ubuntu you are trying, with 192mb ram, things are going to be tough.  That's why I always recommend the "alternate" text-based installer.  With that, at least you'll be able to get the system on the disk, and then worry about configs later.

Have you made some free space for the install?  If not, you'll have to shrink that partition(s) to hold it, or just blow the whole thing away when Ubuntu's guided partitioning will offer to do.  Say goodbye to OSX and OS9 if you decide "use the whole disk" - just so you know. :)

In the end, is it worth it?  You'll end up with roughly the equivalent of a 700mhz x86 box with only 192mb of ram.  This may not be enough horsepower for what you want to do, even if you run Xubuntu.  I'm assuming you want to continue.

I hate to sound like a broken record, but these days for first-time installers, with low memory specs, I think the most productive time could be found installing Debian Etch 4.0r5 stable.  It is still supported, and has the old-style X server configuration that makes using the faqs and wikis here a breeze - since both distros share many of the same solutions to iMac problems.

If you like you can get Etch 4.0r5 stable right here for the powerpc version:

[http://www.debian.org/distrib/](http://www.debian.org/distrib/)

All you need is CD-1.  You may even want to run the XFCE Cd-1 for even more benefit with only 192mb ram.

Once you get up and running with an earlier version like these, you may feel like tackling a more recent release of Ubuntu later on.

---

