---
title: "Install of Fawn on iMac G3/500 successful but..."
date: 2007-08-01
forum: Apple PPC Users
---

### Post by Lurcher on 2007-08-01
By the way, I should think ZoiaGuyver for her (I assume 'ZoyaGuyver' is a female) assistance because what I have done so far I would have been unable to do.

The install took awhile (on and off, about a day), but I got it done.  What I am writing about now is that once I got Fawn installed (I believe that that is the latest version for PPC) it is remarkably slow, and I am not exaggerating.  A snail would be quick in comparison.  

Once I move my mouse, I may get movement of the cursor five or so minutes later.  Once I log in, ten or 15 minutes later elements of the desktop begins to appear.

What I am wondering is that is there something I can do via Terminal to jazz things up because ubuntu is little more than a curiosity at this point.  I mean, I like that there are alternatives to Windows and Mac OS X, but functionality is crucial.

Which is not to assume that I think that ubuntu works like this normally; which is why I am posting.

My second request is to find out how I can partition (probably via Terminal, but I would like to know about any options out there) my G3 with both ubuntu and OS X because the installation of Fawn wiped my pre-existing Jaguar install (for some reason I cannot see the ubuntu partition when I startup from OS X and use disk utility – which I have installed on a portable hard drive), which probably has a bit to do with the redraw rate (I assume that that is the right choice of words) being so remarkably slow that I could have very easily missed the option for a particular partition to install ubuntu to. 

I want ubuntu and (a version of) OS X on my G3 because I don't want to rely on my portable hard drive to work with OS X.

And as always, thank you in advance.

---

### Post by linear on 2007-08-01
Check that you have disabled dri in xorg.conf. If you need instructions, see the Troubleshooting section of the [PowerPC FAQ]("https://wiki.ubuntu.com/PowerPCFAQ").

---

### Post by Lurcher on 2007-08-01
I am so loving Feisty Fawn.  I went over my commands in Terminal (sudo nano /etc/X11/xorg.conf) and noticed that prior I didn't save my commands, some of which weren't changed.  I went back, checked and changed my Horizsync and VertRefresh settings when necessary, and made sure that I used  ctrl + O and then,  sudo killall -HUP gdm.

Feisty Fawn now :guitar:.  It moves briskly, and works great.  I have even written down my password in case I forget;)

Now if anyone has any clues how I can partition my Feisty installation I will be most grateful.

Cheers,

Lurcher

---

### Post by Lord Shank on 2007-08-10
Well if I read right, you wiped the Jag install, and you are running os x from a firewire drive, with FF running off the main drive.  The best way to do a partition is to backup your install or start fresh.  You could try running gparted on your live cd and resize the partition, but I can't remember if it will do HFS+.  You could leave the 2nd part as free space and erase it if disc utility will recognize it.  Either way it is probably going to be a very slow process to make it a dual boot.  Order a pizza and spend some time.  10GB's is usually fine for an ubuntu install, and it won't really slow down os x too much, although, unless you've upgraded your std HD, it might really be too small for dual booting.  Do you have at least 20?  i know my 600MHz only had 20GB stock, I bought a cheap 40 GB 5400 hitachi, and that made a lot of a difference over the 3400RPM drive that was in it.  Now though you can get 7200 rpm on the cheap.  If you have to swap, go to iFixit and follow the instructions, takes about two hours to swap a drive.  I run tiger and fawn on a G3 600MHz no prob w/ 384mb and 40GB 5400RPM.  Let me know if I can help.

---

### Post by Bikerbob on 2007-08-10
Well I have a G3/400 running os X 10.3.9  os 9 for classic and I can boot direct into it. and I also have FF running as well. 

Where the issue with creating the linux install comes in on the ppc, is the bootstrap. Fat32 or NTSF use a MBR and you put Grub there.. and its always in the same place. On an HFS install you need the drivers partitions in a specific location and you need a space for the bootstrap partion for your linux.

Are you going to continue to run OS X on the firewire drive? If so.. just go ahead and install on that drive and not worry about the internal install of FF. If you want to use space on that drive you installed FF on to.. the only thing you can do is resize with gparted from the livecd as was suggested.... problem is.. once you have monkied with the drive with gparted it is no longer os X diskutility friendly.. as os X will not see all the partitions like gparted will.

The ideal way is to create a partition large enough for you OS X install.. leave the rest as free space... do the OS X install... then do your FF install and it will partition the free space and create the bootstrap etc..etc.. no fuss no muss.. your bootstrap will include the option to boot into X.

James

---

### Post by Tearstone on 2007-09-14
I want to thank you for this thread. I took my son's G3 and installed Ubuntu on it and was left with an extremely slow installation. I read the FAQ a few times but didn't feel it applied to me because I actually saw the desktop fine. Regardless, it works well and I'm installing Edubuntu on it now!

---

### Post by koresko on 2007-10-29
From searching for 'dri' in /var/log/Xorg.0.log, it looks like Gutsy's version of Xorg ignores the Module section of xorg.conf, at least to the extent that commenting out 'Load "dri"' doesn't prevent the DRI module from loading and bringing the machine to a crawl.

I got my system working right again by renaming the actual library, which is /usr/lib/xorg/modules/extensions//libdri.so.  There is probably a more proper way to prevent it from getting loaded, and the file will probably get replaced with a new, broken one the first time Xorg gets updated, but it's working for the moment.

The proper way to prevent a module from being loaded is (according to 'man xorg.conf'):

Section "Module"
.
.
.

       Disable  "modulename"
EndSection

Note: I have not tried this approach yet.

---

