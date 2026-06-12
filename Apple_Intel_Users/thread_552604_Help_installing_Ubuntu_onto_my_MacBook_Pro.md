---
title: "Help installing Ubuntu onto my MacBook Pro"
date: 2007-09-16
forum: Apple Intel Users
---

### Post by dcwmark on 2007-09-16
Please help.  I tried to install Ubuntu onto my MacBook Pro.  I purchase the MacBook in Dec. of 2006.  I partitioned my HD using Boot Camp.  I inserted Ubuntu 7.04 i386 iso and pressed 'c' while the MacBook Pro was booting up.  I pressed enter on Start of install Ubuntu.  The Ubuntu logo popped up.  It was up for about 35-40 sec., then the monitor went black.  In about another 20 sec., the whole machine seemed to have just turned down.  And nothing else after that.  When I pressed the power button, the machine powered down.  I tried the process  four times more.  The same resulted.

I even tried to press the alt/option button when the machine was powering up.  I chose the "Window" partition to boot into.  The same thing happened.

Could anyone give me some idea, please?

Cordially,
dcwmark

---

### Post by ronocdh on 2007-09-16
> **dcwmark said:**
> Please help.  I tried to install Ubuntu onto my MacBook Pro.  I purchase the MacBook in Dec. of 2006.  I partitioned my HD using Boot Camp.  I inserted Ubuntu 7.04 i386 iso and pressed 'c' while the MacBook Pro was booting up.  I pressed enter on Start of install Ubuntu.  The Ubuntu logo popped up.  It was up for about 35-40 sec., then the monitor went black.  In about another 20 sec., the whole machine seemed to have just turned down.  And nothing else after that.  When I pressed the power button, the machine powered down.  I tried the process  four times more.  The same resulted.

I even tried to press the alt/option button when the machine was powering up.  I chose the "Window" partition to boot into.  The same thing happened.

Could anyone give me some idea, please?

Cordially,
dcwmark
If you were not even able to boot into the Live CD, it sounds like your burn might be bad. On the main screen of the Ubuntu CD, where the option to "Start or Install Ubuntu" is, there's also an option for checking the integrity of the disc. Do this and see whether any errors are found.

In the future I recommend burning CDs, especially ISOs, with the open source application **Burn**, which you can grab at [OpenSourceMac]("http://www.opensourcemac.org/").

---

### Post by dcwmark on 2007-09-17
ronocdh, thank you for your reply.  I did run a check from the Ubuntu main screen.  The check came back with message saying everything was fine.  I also downloaded Burn as you suggested and "burnt" another disk.  This time, it was worse :-(  I was not even prompted with the Ubuntu main screen.  Just a dark screen.   Cordially, dcwmark.

---

### Post by dcwmark on 2007-09-18
Is there anyone who may have any idea why my ubuntu install simply dies after the initial startup screen?  It just goes black and everything just shutdown.  Any help will be greatly appreciated.

---

### Post by cyberdork33 on 2007-09-18
Is this a Santa Rosa machine?
[http://ubuntuforums.org/showthread.php?t=474144](http://ubuntuforums.org/showthread.php?t=474144)

---

### Post by dcwmark on 2007-09-18
It is not.  I purchase the MacBook Pro in Dec. 2006.

---

### Post by cyberdork33 on 2007-09-18
> **dcwmark said:**
> It is not.  I purchase the MacBook Pro in Dec. 2006.
It sounds as though Xorg is not starting properly. 

Use ALT+CTRL+F1 to get to a terminal.
```
sudo apt-get install linux-restricted-modules-generic
```

Then edit your xorg.conf to use the fglrx driver, and x should then be able to start.

---

### Post by hurleyint1386 on 2007-10-09
i'm having this exact same problem. I had a terminal, then when i restarted, I can't seem to get back to it. What's going on? I really want Ubuntu on my MacBook Pro!

---

### Post by Some_Bored_Dude on 2007-10-09
What Gen MBP is it? I have a gen 1 and mine did the same, but i followed the wiki here on howto install it and it worked fine.

I Followed all the steps under the heading "Fixing xorg drivers" on the wiki page: [https://wiki.ubuntu.com/MacBookPro/Feisty](https://wiki.ubuntu.com/MacBookPro/Feisty) and perfect.

---

### Post by hurleyint1386 on 2007-10-09
> **Some_Bored_Dude said:**
> What Gen MBP is it? I have a gen 1 and mine did the same, but i followed the wiki here on howto install it and it worked fine.

I Followed all the steps under the heading "Fixing xorg drivers" on the wiki page: [https://wiki.ubuntu.com/MacBookPro/Feisty](https://wiki.ubuntu.com/MacBookPro/Feisty) and perfect.
hmmm, mine is the first gen. I'll take a look at that. thanks a lot

---

### Post by hurleyint1386 on 2007-10-09
> **hurleyint1386 said:**
> hmmm, mine is the first gen. I'll take a look at that. thanks a lot

Ok, so I've got it installed, now I can't get X up. I tried all the suggestions on that page you sent me to. Has anyone with a 17" MBP had any issues with getting X up and running with Ubuntu? This brings me back to when I had issues with Gentoo all the time.

---

### Post by cyberdork33 on 2007-10-09
> **hurleyint1386 said:**
> Ok, so I've got it installed, now I can't get X up. I tried all the suggestions on that page you sent me to. Has anyone with a 17" MBP had any issues with getting X up and running with Ubuntu? This brings me back to when I had issues with Gentoo all the time.
Make sure you did this correctly. the Wiki had a typo:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart
```

---

### Post by hurleyint1386 on 2007-10-09
I tried, but it's not connecting to the internet. It might be my college internet not letting me connect because it needs to check for viruses, but they don't have anything to check on linux (there are only about 3 people on campus that use linux)

---

### Post by cyberdork33 on 2007-10-09
> **hurleyint1386 said:**
> I tried, but it's not connecting to the internet. It might be my college internet not letting me connect because it needs to check for viruses, but they don't have anything to check on linux (there are only about 3 people on campus that use linux)
well you really need to get the fglrx driver for everything to work properly.

You can try using the vesa driver. That should get something up. edit your /etc/X11/xorg.conf file and replace whatever driver is currently specified for your video device to "vesa"

---

### Post by hurleyint1386 on 2007-10-09
> **cyberdork33 said:**
> well you really need to get the fglrx driver for everything to work properly.

You can try using the vesa driver. That should get something up. edit your /etc/X11/xorg.conf file and replace whatever driver is currently specified for your video device to "vesa"

nope, no luck with the vesa driver. is there a way to get a package, and copy it over and install it that way? or do i have to use sudo apt-get? thanks

---

### Post by cyberdork33 on 2007-10-10
> **hurleyint1386 said:**
> nope, no luck with the vesa driver. is there a way to get a package, and copy it over and install it that way? or do i have to use sudo apt-get? thanks

After you edit the xorg.conf you need to switch back to the X session (ALT+F7) and then hit CTRL+ALT+BKSP to kill the currently running x server, then it should try to restart. 

You can get the deb package by other means and then install it on the machine. You have to get the right package for your kernel version though.

---

### Post by hurleyint1386 on 2007-10-11
> **cyberdork33 said:**
> After you edit the xorg.conf you need to switch back to the X session (ALT+F7) and then hit CTRL+ALT+BKSP to kill the currently running x server, then it should try to restart. 

You can get the deb package by other means and then install it on the machine. You have to get the right package for your kernel version though.

Success! now there's one more thing. The mouse stays in the center, if i move it around, it always repositions back to the center, and if I don't touch the mouse pad, the mouse moves around the center slightly. Any ideas?

---

### Post by hurleyint1386 on 2007-10-11
> **hurleyint1386 said:**
> Success! now there's one more thing. The mouse stays in the center, if i move it around, it always repositions back to the center, and if I don't touch the mouse pad, the mouse moves around the center slightly. Any ideas?

Nevermind, just needed a restart

---

