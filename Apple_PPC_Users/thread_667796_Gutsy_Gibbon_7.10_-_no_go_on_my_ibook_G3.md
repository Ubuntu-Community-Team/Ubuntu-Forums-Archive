---
title: "Gutsy Gibbon 7.10 - no go on my ibook G3"
date: 2008-01-14
forum: Apple PPC Users
---

### Post by kansas_plainsman on 2008-01-14
After more than 10 hours of booting, rebooting, internet research, downloading, cd burning, and more and more booting cycles...

...the iBook on which I was attempting to install ubuntu 7.10 is now running OS X Panther.

Took me about 5 hours to finally get to a completed install of ubuntu, but the desktop the install system provided was partially broken and I could not make one of the final 'patches' (adding "ide-core" to /etc/initramfs-tools/modules) because I could not get to a command prompt (or any application)

Upon rebooting I got a password dialog, but it refused to accept my user ID or password.  Subsequent reboots failed to get even that far, leaving me with a blank screen, or a blank screen with an underline in the upper left corner...

..and once that had happened, subsequent attempts to reboot, even from CD failed with various errors, commonly referencing invalid file systems and such.

Trying a different CD of kubuntu 7.10, I did manage to get it to boot from that CD twice - each time 'panic'ing in different places and leaving me with a warm brick.

I figured I had a dead iBook.  But just in case (and because I hadn't driven myself crazy enough yet) I tried to install OS 9... no joy.. but I still had a few hairs left on my head so I tried installing OS X Panther.

Install went without fault.  Subsequent reboots are perfect.

The ONLY thing I can think that made the difference is that while I was running it with Panther originally, I was careful to apply all patches, including all firmware patches available.  Maybe Apple has included something in the firmware that doesn't like Linux?

Anyway, kubuntu is running happily on my intel desktop, and the iBook is going up for consignment sale locally.  If/When it sells, I'll be getting a basic intel laptop to put kubuntu or xubuntu on.

Just thought you would like to know.  Now I have an appointment with a straight jacket, wet packs and a padded room.

---

### Post by tgalati4 on 2008-01-15
G3's are a tough call.  Great processor, less-than-standard motherboard/graphics architecture.  You will generally have a better experience maxing out the RAM (256 MB on some machines) and finding a used copy of Tiger.  Tiger is a good operating system and stable.  My uptime on my powerbook as I write this is 149 days.  I challenge anyone to meet that kind of uptime on a laptop.

Or, sell it and get a used G4 powerbook with Tiger.  As prices come down, they are decent machines.  Of course you can find a used Thinkpad for less and install Ubuntu on it, but you will have to spraypaint the Tpad silver because they only come in corporate black.

I've had Thinkpads in the past.  They are decent machines, but not as nice as a powerbook.  Depends on what you want to do on it and how much you want to spend.

---

### Post by Gen2ly on 2008-01-15
Hmm sounds like this wasn't the normal install.  yikes.

There are usually people that can help out of most these binds, so if you have another computer around fire off the posts here to the forums.  A possible even better resource is to use the freenode irc chat network and join the ubuntu channel.

I remember when I had an issue with the Ubuntu CD not so far back that I tried Debian Etch and it install nearly perfectly.

---

### Post by kansas_plainsman on 2008-01-15
I guess I didn't make myself clear - I'm was trying to install ubuntu on my iBook G3.  As I pointed out, I was able to get OSX Panther back on it without problems.. but I didn't want OSX on that box.

Not sure why I would want to spray paint an IBM Thinkpad silver.

Anyway, thanks for the comments.

---

### Post by GVCarroll on 2008-01-15
If you're willing to downgrade to Ubuntu 7.04 Feisty it works on my G3 iBook 500MHz 320MB RAM.

I've only had two issues with the install:

1) Monitor setting defaults to 800x600 instead of 1024x768 which is a bit of a pain during a LiveCD install since the installer window ok/next/back buttons are just off screen at the bottom. But I minimized both panels and that shows just enough to complete the install. Fixing the xorg.config after the install to fix the screen is pretty easy.

2) Having to uninstall the processor cycling (powernowd I think its called) which causes annoying "hitches" in the UI if its running.

That's it though. Installed it, ran through the upgrades and it's fine. Also installed kubuntu-desktop and xubuntu desktop as well, the latter running the fastest of the 3 (no surprise there).

Dual booting it with Tiger (which runs fairly, not great obviously).

---

