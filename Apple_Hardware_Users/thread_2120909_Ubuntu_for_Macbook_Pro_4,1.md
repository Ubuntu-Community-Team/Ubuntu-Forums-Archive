---
title: "Ubuntu for Macbook Pro 4,1"
date: 2013-02-27
forum: Apple Hardware Users
---

### Post by Commandrkeen on 2013-02-27
I have a Macbook 4,1 and I read on the installation guide that Ubuntu 10.10 was next to this version of MBP. So, should I go with 10.10 or would 12.04 LTS be just fine since it is a newer developed OS that would most likely have drivers from early 2008? Thanks.

---

### Post by mörgæs on 2013-02-28
Moving your thread to the Apple forum.

Go for 12.04 or 12.10, also for older hardware.

---

### Post by Commandrkeen on 2013-02-28
> **mörgæs said:**
> Moving your thread to the Apple forum.

Go for 12.04 or 12.10, also for older hardware.

Alright thanks, didn't think there would be issue, just double checking. :)

---

### Post by wgpenney on 2013-03-01
> **Commandrkeen said:**
> Alright thanks, didn't think there would be issue, just double checking. :)

You should have no problems with 12.4, which is what I'm running right now. I have a Macbook5,1 which has similar specs as yours. The only difference I can see is the graphics card, mine being a GeForce 9400M. I've had problems with the install of 12.10 not configuring the proper graphics and wifi drivers and have yet to find a solution for it yet.

---

### Post by serpico007 on 2013-03-01
Good luck with your install.

I had to install from the 12.04 livecd minimal cd option because I only had a 650mb CDRW lying around. USB flash drive never worked past the boot screen when loading the kernel. Worked fine with my 4,1 model except sound is still not working. NVidia drivers were under additional drivers in system settings. I was told to select the 310 option since it was the current version from Nvidia's website. In Ubuntu it still says beta but ignore that in the list and just install it. 

Wifi was the broadcom driver under additional drivers in system settings. Works great. I just wish I could figure out sound now. I did plug in some headphones and could hear volume very very low. So it's not muted anywhere.

---

### Post by serpico007 on 2013-03-03
For anyone struggling with no sound on a Macbook Pro, here is a link that solved my sound issue!

[http://miteshj-linux-tips.blogspot.pt/2009/05/making-soundcard-work-in-macbook-pro.html](http://miteshj-linux-tips.blogspot.pt/2009/05/making-soundcard-work-in-macbook-pro.html)

---

### Post by Commandrkeen on 2013-03-10
Alright, I have finally gotten time to sit down and install. Thanks for all the feedback, guys.

---

### Post by serpico007 on 2013-04-08
Just to keep the 4,1 thread support going for future users here.

I installed 12.10 this past week and everything got detected and worked great. Nvidia video is the only thing that I had issues even after trying them (in Additional drivers) all I went back to the Xorg free driver.  For color calibration I imported the icc profile files from my OS X partition and both monitors look way better. I have a dual monitor setup, a LED external monitor along with the LCD laptop screen.

---

### Post by v1nsai on 2013-06-05
Thanks for posting your experiences guys.  I'm having a hell of a time installing Ubuntu 12.04 on my Macbook Pro 4,1 and I'm pretty sure I've narrowed it down to the video (nvidia) not loading properly.  It just freezes while booting, and no combination of 'nomodeset', downloading nvidia drivers and swearing while hitting it have gotten it running properly.  [I started a thread here]("http://ubuntuforums.org/showthread.php?t=2151565&p=12678057") but I like the idea of having an MBP 4,1 thread as a catch-all so I wanted to post here too.

I'm going to try booting from the [13.04 +mac iso from here]("http://releases.ubuntu.com/13.04/") so we'll see.  I'll post if anything works for me -_-

---

### Post by sock2 on 2013-08-14
> **v1nsai said:**
> Thanks for posting your experiences guys.  I'm having a hell of a time installing Ubuntu 12.04 on my Macbook Pro 4,1 and I'm pretty sure I've narrowed it down to the video (nvidia) not loading properly.  It just freezes while booting, and no combination of 'nomodeset', downloading nvidia drivers and swearing while hitting it have gotten it running properly.  [I started a thread here]("http://ubuntuforums.org/showthread.php?t=2151565&p=12678057") but I like the idea of having an MBP 4,1 thread as a catch-all so I wanted to post here too.

I'm going to try booting from the [13.04 +mac iso from here]("http://releases.ubuntu.com/13.04/") so we'll see.  I'll post if anything works for me -_-

Hi v1nsai, did you solved? I've a Macbook Pro 4,1 and I'm banging my head against the wall for installing linux on my Mac. The problem is the f*cking nVidia 8600 GT!

---

### Post by v1nsai2 on 2013-08-14
Same v1nsai here, I logged in with the new Ubuntu One and it won't stop putting a 2 on the end of my name.

Anyway, I gave up.  The lack of BIOS on Macs makes them pretty lousy Ubuntu machines anyway, and I've seen a way to make Ubuntu work without the battery-draining fake BIOS that it runs with on Macs, but with the issues I'm having just getting it to launch normally, I gave up.  Luckily, I've got another laptop that I can use as a linux box and let my mac continue being a mac.

Hope you have better luck than I did though, do post results if you get it to work so others with the MBP 4,1 can find it.

---

### Post by sock2 on 2013-08-15
Okay thanks. It seems that everyone on the web with MBP 4,1 didn't have no luck with Linux.
Thanks anyway for the reply!

:-)

---

### Post by Aaron_Goldfogel on 2013-09-01
Same here. The installer had the GUI, but no installation has. I tried both Raring and Precise (also mint) and got the same problem.
When booting into the installation disk, only "install ubuntu" works (with nomodeset). The live cd option does not work at all. The installer worked fine from there.
The real nightmare was the installation itself. Firstly it needed nomodeset to keep from going to a black screen (but actually into terminal from which blind commands work).
With nomodeset, the installation boots straight into command line. Nothing I can do seems to help. proprietary drivers, nouveau, nothing!
startx gives the error "no screens found" and its log says something like screens found but none were configurable. #**Xorg -config xorg.conf.new -retro **worked, but I don't have any how that helps. It just makes it more infuriatingly obvious that my system should be able to work! (As if the installer working with GUI wasn't enough).

I'd really like to try out linux after being a long-time mac user and I got my linux savvy friend to help me with this and he's stumped too. So this isn't some idiot mistake. Help!

---

### Post by maxbar on 2014-04-02
So just wondering, is this thread still active? Anyone has a solution yet to get Xserver running? If so, even if not optimal, please post your xorg.conf and the steps you took (such as driver install, editing grub.conf, ...) as a reply here - thanks!

---

### Post by Aaron_Goldfogel on 2014-04-03
Well I got rid of my Ubuntu partition and stuck with OSX a while ago. I wouldn't be adverse to trying again...

---

