---
title: "Can't boot my iMac G3 slot-loader"
date: 2008-11-21
forum: Apple Hardware Users
---

### Post by Dalazar.17 on 2008-11-21
Hi,

I found an iMac G3 with a slot-loading DVD drive in the street yesterday (long story), hooked it up, and it booted straight into OS 9.2, no problems.  After trying to install Slackintosh and Gentoo, each with different problems, I downloaded the Xubuntu 8.10 PPC alternate image, which I used to (seemingly) successfully install Xubuntu.  

Upon restart, yaboot prompts me for startup options, then xubuntu prompts me (so far, so good), and with the default commands, I see the "Loading..." message indicating that the system is attempting to start.

Then it shuts down.

Any ideas?  It has 256MB system memory, the standard 8MB ATI Rage 128 Pro, and the G3 400MHz, I believe.

---

### Post by stream303 on 2008-11-22
With OS9 functioning from the hard drive, you may want to do a firmware upgrade first!  It isn't absolutely necessary, and the previous owner may have already done it, but it is fortunate, at least temporarily, to have that up and working.

**support.apple.com/kb/HT1395**

After the update, you'll have to decide if you want to keep OS9, or just wipe it out completely during guided partitioning.

While I have nothing against Xubuntu, I'd recommend sticking to Ubuntu for a first-time install.  You can always add the XFCE desktop later, or reinstall from the Xubuntu image once you get your feet wet and prove that an install is possible on your machine.

Use of the "alternate" image is always the best way to go to nearly guarantee you'll get the bits on the disk at least without running into gui issues at the start, like totally shutting down. :)

Be sure to see these faqs to help you get started:
[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

First tip:  try booting at the second-stage yaboot boot: prompt with

```
Linux video=ofonly nosplash
```

And see if that leads you further down the road...

---

