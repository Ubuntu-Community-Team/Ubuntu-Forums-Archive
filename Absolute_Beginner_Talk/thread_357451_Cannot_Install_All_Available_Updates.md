---
title: "Cannot Install All Available Updates"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by darklyndsea on 2007-02-09
In the update manager, I receive a message which says:
Cannot install all available updates
Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.
The following updates will be skipped:
linux-image-386
linux-image-686
linux-restricted-modules-386
linux-restricted-modules-686

When I do "sudo spt-get dist-upgrade", this is what I get:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade...Done
The following packages have been kept back:
  linux-image-386 linux-image-686 linux-restricted-modules-386
  linux-restricted-modules-686
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

In Synaptic, pressing the "mark all upgrades" button doesn't seem to do anything.  Is there anything I can do, or do I not need those upgrades, or what?

---

### Post by natman on 2007-02-09
Im not sure but some of this info may help ( you may already know this if so soory for a wasted reply)
1 Have you all the needed repositoreies enabled in synaptic? ( maybe universe and backports )

2 its says in your error message about kernel 686 and 386, 386 is for single core and 686 for dual core processors, are you trying to fetch an update for a different build of machine?

Good Luck:

---

### Post by anothernewuser on 2007-02-09
I'm having pretty much the same problem - though I'm not getting the 686 messages just the 386 ones.

I think that the problem is another install of ubuntu if that makes sense.

Here's my story - I installed 6.06 and then manually messed up the video driver in a fit of overconfidence so I reinstalled because I wasnt too comfortable with messing around on the command line.  I figured it would install over the messed up install but it seems to have installed beside it as I now have 2 different ubuntu choices when i boot.  The new one which works fine and is updated and the old one which defaults to the command line.

Everything had been going fine until the most recent updates when i got the same messages you did.  My best guess is the older of the installations is somehow preventing the newer from updating.  Does any of this sound like it might be similar to your problem?

---

### Post by xpod on 2007-02-09
Theres a big blue message at the top of the forum about problems with the latest kernal update and theres also a big thread somewhere regarding it:)

---

### Post by jimrz on 2007-02-09
there are problems with the update software. see this [http://ubuntuforums.org/showthread.php?t=356408]("http://ubuntuforums.org/showthread.php?t=356408")

---

### Post by anothernewuser on 2007-02-09
Yes. I see that my reationalizing of this was all wrong and I guess I'll wait for the fix.

I'll not hijack this thread and will deal with my other problems in another post another time then.

---

### Post by v4169sgr on 2007-02-09
I see from reading the referenced thread that there are solutions.

Would someone be kind enough please to put together a simple step by step guide on solving the problem?

---

