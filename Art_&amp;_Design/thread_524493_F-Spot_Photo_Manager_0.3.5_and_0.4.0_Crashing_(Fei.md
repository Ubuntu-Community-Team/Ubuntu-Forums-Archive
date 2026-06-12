---
title: "F-Spot Photo Manager 0.3.5 and 0.4.0 Crashing (Feisty)"
date: 2007-08-13
forum: Art &amp; Design
---

### Post by Lil on 2007-08-13
Hello,

You might have excuse a little ignorance as i am relatively new to Ubuntu, although I am an experienced geek :) (Windows, Mac OS X/BSD and Linux in general)

I have taken a general liking to F-Spot Photo Manager although I am about to give it up and just use Picasa instead. My problem is that two features that I like to use seem to crash it :(

1. On 0.3.5 when I go to print, I enter the Print window (File>Print) and change the page size to custom and enter the dimensions of a standard photo say, 6x4" and intermittently the program freezes up :( If I don't meddle with the page size it works fine. My printer driver is for my Canon Pixma iP1500; but it also happens if I select the Output to PDF driver.

2. On 0.4.0 which I compiled and installed in my home directory to test, the print problem above appears to be cured; but running a slideshow appears to crash the program and I am dumped back to the terminal :(

I am running Ubuntu 7.04 on a ThinkPad T40, using the ati driver in xorg.conf (FWIW) with AGP set to 4x (these are the only real changes I have made to the default configuration of the inner system).

Does anyone else experience these issues? I noticed posts referring to crashes when the hard disk was full but I have only just started to use a brand new 160GB drive! The ThinkPad also has 1GB RAM.

Anyone else suffering the problem noted on 0.3.5? I'm not overly surprised by 0.4.0's behaviour as it is a new iteration and I understand that at the moment it won't be included in Gutsy and 0.3.5 will stay in place, due prehaps to the temprement of 0.4.0.

Thanks!

Vicky

---

### Post by eyemeansit on 2007-08-15
"For what it's worth"... I know nothing of F-Spot or Thinkpads, but I've read of and experienced ATI video cards having issues with Feisty. I had some screen drawing problems with Blender awhile back, and others who had the same issue determined it to be because of their ATI card. Since then it seems to have been fixed. Wish I could help more...:(

---

### Post by stani on 2007-08-15
I would post this on the f-spot mailing list and you will be helped sooner than later.
Stani

---

### Post by FuturePilot on 2007-09-02
[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/115162]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/115162")
There's a bug here. It might be related.

---

