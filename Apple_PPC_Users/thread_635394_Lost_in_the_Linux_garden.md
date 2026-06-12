---
title: "Lost in the Linux garden"
date: 2007-12-08
forum: Apple PPC Users
---

### Post by pwright2 on 2007-12-08
I'm a windows guy and out of my depth.  I have a green iMac PPC G3, Model M4984, OS 9.2.2, 160MB RAM, 9 GB HD, 333 MHz.  I'm sure it was a fine machine for its time but I can't find software to do the things I need (web browser with flash and a simple slideshow screensaver).  And a decent HTML editor like Kompozer.  They may exist but I'm not finding them.

So, I want to go to Linux, specfically some flavor of Ubuntu.  I've downloaded both the desktop and alternate install versions of PowerPC Xubuntu 7.10.  I'd rather run the desktop version first, to see how it does without blowing away 9.2.2. 

I had to ask in a Mac forum but I got it to boot the CD by holding down the C key while starting up.  Booting from the powerpc liveCD of Xubuntu 7.10, the boot seems to be going well for a while.  It stops and waits for an input and I hit enter to accept the default.  The screen changes from black to white to black a few times and then shows the Xubuntu logo for a bit.  Then it stops with this message:

[B][   75.371561]  atyfb: h_disp too large ffffff(ff)

Busybox v 1.13 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)

Enter 'help' for a list of built-in commands.

(initramfs)[/B]

Help indeed gives me a block of command words but no hint of what I should ask it to do.  Googling the atyfb line seems to say something about the framebuffer. 

Any idea what a proper next step might be?

-----Paul-----

---

### Post by Auria on 2007-12-08
See the PPC FAQ (it's a sticky) Gutsy has a few bad bugs in it, the FAQ will tell you their common workarounds. Alternatively you can also try 7.04.

Just as a quick note though, flash support on Linux PPC is not too good because adobe does not release flash for this platform. There is open-source alternatives Gnash and you can view videos with Miro though so it may depend on your needs.

---

### Post by PaganHippie on 2007-12-08
7.04 and 6.06 are still available and both have run fine on my iMac which also has 160MB of RAM.  You will probably want the Alternate CD -- I was never able to get the Live discs to work in that much RAM.  Go ahead and try regular Ubuntu or even Kubuntu; they'll be a bit slow, but much more feature-rich than Xubuntu.

---

### Post by pwright2 on 2007-12-09
I downloaded the Kubuntu 7.04 desktop and it appears to boot perfectly.  Takes a long time but comes to a perfect desktop.  Unfortunately it does not appear to recognize either mouse or keyboard.  Perhaps it just isn't recognizing USB.

Any tips and tricks?

-----Paul-----

---

### Post by PaganHippie on 2007-12-10
Try unplugging then re-connecting them?  Use a different USB port?  If they're working under OS 9 there's no reason Kubuntu shouldn't pick them up.

---

### Post by pwright2 on 2007-12-11
Yes, I had done the unplug routine without effect.  I had also rebooted and tried again with similar results.  I have, however, just completed a boot and the system seems to be working fine, although slow as molasses.  

Part of the problem is that it takes about 5 minutes to boot from the livecd, so I tend to wander away and come back later.  I noticed on one reboot that it reached a point where the desktop was showing, though not fully populated, and the mouse was working at that point but when I came back later, nothing worked.

So ..., this time I sat and watched it the entire time.  And when the desktop came up, I tried clicking some things.  They took a long time, since the machine was still booting from the liveCD, but they did respond.  And the whole thing came to a stop with a working desktop, though still rather slow.  

I appear to be able to run Konqueror and other standard programs.  

While it was booting and after the desktop opened, I got this message in a dialog box.

Error-KDesktop
The process for the file protocol died unexpectedly.

Later, while using Konqueror to search for Media I got this one:
     Error for locate media
     The process for the locate protocol died unexpectedly.

I haven't noticed that anything is broken

Hmmm.  Disk and Filesystem has finally opened.  It shows the Maxtor hard drive as having 8 partions.  7 of the 8 are between 5KB and 256KB.  #7 is 9.5GB.  Is this normal for an iMac?

Anyhow, this is neat.  Now I'll need to figure out how to install and dual boot, if that is possible.

-----Paul-----

---

### Post by Auria on 2007-12-11
Hmm I'm pretty sure you don't have enough RAM, especially for Kubuntu. Try Xubuntu, or perhaps alternate CD (no live desktop though). 160 MB of RAM is little for a LiveCD, and probably little for KDE in general too.

---

### Post by pwright2 on 2007-12-11
Undoubtedly too little, but it does run.  Now the differences between Ubuntu, Kubuntu, Xubuntu, etc are the desktops, correct?  So it should be possible to change between them.  How does one shut down KDE and substitute XFCE, etc?

Did I mention that it reads memory sticks just fine?

-----Paul-----

---

### Post by tgalati4 on 2007-12-11
Max out the RAM and find a used copy of Tiger 10.4.  You will be happier.  Ubuntu works, but not as smooth as Tiger on that old machine.

Correction:  Tiger 10.4 if you have firewire, Otherwise 10.3 then perform the on-line upgrades to 10.3.9.

---

### Post by pwright2 on 2007-12-11
This is intended to be the prototype of a group of kiosks using these very inexpensive machines.  If I can get a $30 machine to do what I want, great, but nobody is going to pay for a dozen copies of OS X and more RAM.  I don't need much performance.  A slideshow screensaver and a decent web browser will do the trick.

-----Paul-----

---

### Post by Auria on 2007-12-12
Easiest way is to download a Xubuntu CD and not a Kubuntu CD :)

If you have Kubuntu already installed, you can switch to Xubuntu with something like
sudo apt-get install xubuntu-desktop
see [http://tuxicity.wordpress.com/2007/01/30/howto-switch-from-ubuntu-to-kubuntu-or-xubuntu-or-edubuntu-or-vice-versa-610-edgy/](http://tuxicity.wordpress.com/2007/01/30/howto-switch-from-ubuntu-to-kubuntu-or-xubuntu-or-edubuntu-or-vice-versa-610-edgy/)

---

### Post by pwright2 on 2007-12-17
OK, so now I am running Xubuntu 7.04 installed on the hard drive from an 'alternate' CD.  I had to blow away the Mac OS formatting because the Xubuntu installer couldn't resize the partitions (though there was plenty of space).  Anyhow, boots fine and programs run.  It has the slideshow screensaver and Firefox 2.003.  Reads from a thumb drive just fine.

Unfortunately I cannot get it to talk to the network.  But I'm going to start a fresh thread on that one.  

But Xubuntu 7.04 is doable on a 333 G3 with 160MB RAM.

-----Paul-----

---

### Post by Gen2ly on 2007-12-18
If you run a bare bones system Xfce, Gnome, and KDE are all possible on that iMac.  However, Ubuntu produces more ... feature complete CD's.  Xfce is a better decision, but it's difference isn't tremendous.  I read a nice article on it today:

[http://ktown.kde.org/~seli/memory/desktop_benchmark.html](http://ktown.kde.org/~seli/memory/desktop_benchmark.html)

I currently am using an iBook 300 that only uses 140 MB with a Gnome Desktop and Web Browser running.  Gentoo is a more advanced install, but it's easier to rid the cruft:

[http://gentoo-wiki.com/HOWTO_Install_Gentoo_-_From_Stage1_on_an_iBook_G3](http://gentoo-wiki.com/HOWTO_Install_Gentoo_-_From_Stage1_on_an_iBook_G3)

---

### Post by oswaldkelso on 2007-12-19
you are right about ubuntu producing  feature compleate environment, thats because its geared to work out of the box on as much hardware as possible. that is what makes it such a great distro. it does'nt how ever make it run as well as a tuned install, that is possible as users learn about linux.

the thing that is needed is to give new users a way in that is a pleasing experiance. that is a big ask on old hardware with low ram and a standard u/k/xuntu install IMHO. 

for other achitectures you have choice, puppy linux, zenwalk etc.  but with ppc you are quite limited. debian, ubuntu, fedora, open suse,   slackintosh and gentoo plus some smaller distros that are geared to seasoned linux users of those only  gentoo debian and slackintosh are really geared to easily building a light linux install and for a new user thats quite a chalenge. i would add fluxbuntu when its ready , i would think running  breezy  would give  a new user a  plesent linux experiance on low end machines, and at least get them into the way of things. then they could learn how to cutomise their system and make it lighter and faster.

in short you can have your cake and eat it. but you have to learn to cook first.    

nice link to the ibook how to.

 [my cake]("http://www.my2bits.org/public/images/snaps/blackbox-rox2.png")

---

