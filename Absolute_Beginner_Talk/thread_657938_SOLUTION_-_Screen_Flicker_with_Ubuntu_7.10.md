---
title: "SOLUTION - Screen Flicker with Ubuntu 7.10"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by luckylucky on 2008-01-04
Hi to everyone who is experiencing annoying screen flicker on laptops using Ubuntu 7.10.  I have been seriously annoyed with this issue, as I'm sure some of you have been as well.  After much hunting around the forums & google for a solution, which I didn't find, I've come up with something that seems to have worked for me.  I hope that this will work for some of you too, but please note that I don't guarantee anything (so don't complain if following this it mucks up your computer).

Ok, so what is the idea I came up with that solved it?  Here is the overview of what I did.  This all took me about 15 minutes to accomplish.

Using older versions of Ubuntu I never had the screen flicker problem, so I downloaded an older version of Ubuntu 7.04, booted the live CD into my computer, copied the xorg.conf file from the live CD system (again, running 7.04), then rebooted back into my regular computer (removing the live CD) I backed up the original xorg.conf to xorg.conf.ORIGINAL then overwrote xorg.conf with the one I copied from the live CD.  Then I rebooted.  Poof, the screen flicker was solved, but since I have a widescreen laptop computer I had to do 915resolution to fix the screen resolution.  Rebooted computer and now it seems to be working beautifully without the flicker.  Problem solved!

I hope this helps some people.  For those of you technically savvy I'm sure the above are all the instructions you need to accomplish it yourself, but for the newbies I'm sorry I don't have time right now to do a more detailed explanation of the steps.  Perhaps someone else can elaborate here, or if enough people beg then maybe in a day or so I can find the time to write more.

---

### Post by luckylucky on 2008-01-04
You can download Ubuntu 7.04 here:
[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

---

### Post by kiproof on 2008-01-22
Yay!  that worked great for me.  I'd been changing settings and drivers for hours.  My laptop is happy again!!

Thanks
1

---

### Post by Rocket2DMn on 2008-01-22
I would suggest also backing up that new xorg.conf file in case it gets overwritten (during upgrades or if you end up reconfiguring X)
Something like:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.FLICKERFIX
```

---

### Post by rokky on 2008-04-01
Thinking about the diffs between 7.10 (in the Mint 4.0 variant) and earlier versions, 7.04 and 6.10, I realized it boiled down to the driver setting in xorg.conf:  changing it from "intel" to "i810" worked wonders for my Fujitsu Lifebook P5020 (and I still have the 1280x768 resolution without installing the 915 driver - woot!).  No need to download 7.04 and all that extra effort.

BTW, I found this same flicker issue with with PCLinuxOS 2007, and did not pursue the fix, but "came back" to Ubuntu that I was more familiar with.

Now, the big QUESTION is: why is this happening with the newer "intel" driver???   My searches turned up a Debian developer bug discussion that seemed to indicate the new intel driver was being looked at as the culprit with lots of Xorg.0.log/bug trace dumps from the poor soul with the issue , but seemed to wind up sloughing it off to some other cause - dunno....    

Seems like the developers get so caught up in tweaking all the latest hardware exotica, they lose sight of maintaining a stable platform for us ordinary users.  I find Windows 2000/XP  to be much more viable for long-term support of more software and hardware.  The much reviled "dll Hell" seems to me to be much less of a problem than all the Linux kernel/glibc varieties and the software they break. 

I have stayed with older distro versions (Ubuntu and Puppy) for precisely this reason.  And only a "new" (to me ;-) laptop with a messy partition table layout from several years of mutli-boot setups finally hosed by a Windows XP installation attempt (yes, it causes me trouble, too) led me to try the latest Mint/Ubuntu, and finally nail down this hugely obnoxious flicker issue - <sigh>

Rokky

---

