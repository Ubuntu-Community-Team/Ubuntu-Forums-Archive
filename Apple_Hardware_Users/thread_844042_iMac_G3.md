---
title: "iMac G3"
date: 2008-06-29
forum: Apple Hardware Users
---

### Post by emackey3k on 2008-06-29
Hello,

I have an iMac G3 that was just given to me running mac os 9.  I don't have much use for it unless I can use it for a print server.  I currently have it placed right next to a HP deskjet 340.  I tried to download the right driver for mac os 9 with no luck.  I also tried to install xubuntu.  

The problem I am having with installing xubuntu is that it doesn't seem to allow me to boot from a cd.

Any suggestions?

---

### Post by stream303 on 2008-06-29
See this thread for another user that is just starting out:
[http://ubuntuforums.org/showthread.php?t=844024](http://ubuntuforums.org/showthread.php?t=844024)

Be aware that old G3 imacs may have weak pram batteries, and that can interfere with gnome starting up:
[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

---

### Post by emackey3k on 2008-06-29
Thank you for the reply.  I have the correct powerpc iso burnt.  The problem is when I try to boot from cd by holding down the c key at start up it does not boot from disk.  I have tried booting holding down the option key and the cd rom is not an option to choose either.  I guess the main problem is booting from cd.

---

### Post by emackey3k on 2008-06-29
I tried again this morning and I can now boot from the xubuntu 8.04 alternative install disk for ppc.  

However I now have a new problem.  The install fails when it gets to install the base system.  Many of the packages are corrupt and won't install.  This wouldn't be to big of a problem I can just try different installers.

Here is the problem, I can't eject the CD to put in a new one.  The mac os has been partitioned so I can't boot into that to eject the cd.  I don't see any button to eject the cd or even a little hole to stick a paperclip into to eject it.  There is an option on the main menu of the installer to eject the cd but that fails as well.

---

### Post by oswaldkelso on 2008-06-29
Not sure if this is the g3 imac but the manual edject is in the slot
[http://docs.info.apple.com/article.html?artnum=58566](http://docs.info.apple.com/article.html?artnum=58566)

[http://discussions.apple.com/thread.jspa?threadID=1509322&tstart=0](http://discussions.apple.com/thread.jspa?threadID=1509322&tstart=0)

---

### Post by stream303 on 2008-06-29
Have you tried restarting the computer and holding down the mouse button to eject the cd?

Many recommend 2x or 4x speed on CD-R media for G3 iMacs.  Also be sure you are burning it as an iso image, and not just copied over.

---

### Post by emackey3k on 2008-06-29
Thank you for the replies.  I was able to eject the disk by holding down the mouse buttons.  I have been trying to boot again to cd with a number of different disks with no luck.  

This is what happened last night.  I am not sure why it let me boot from disk that one time.  

I am burning as an iso and not just copying it to a disk.  I have been burning them at 1x speed.  

I am burning the normal Ubuntu ppc alternative install disc now and will try that.

---

### Post by emackey3k on 2008-06-30
I still have not had any luck.  I can now boot from disc all the time.  I starting burning them from my windows machine and not from my Ubuntu machine and now I can boot from any of the multiple distros I have now tried.  

I have tried Ubuntu 8.04, 7.10, and 6.06 both the alternative install ppc and the server install ppc.  All of the ubuntu distros fail at the base system install.  Many of the packages can't install because they are corrupt.  

I also tried Fedora 5, yellow dog 4, Opensuse 11 all for PPC.  The Ubuntu installs got the farthest.  I have also for the heck of it tried to install osx 10.4 from the install disc that came with my wife's macbook.  Predictably that did not work either.  I am going to ask the person I got the imac from if they still have the installation discs for mac os 9.1 that was on it.

---

### Post by stream303 on 2008-07-01
> **emackey3k said:**
> All of the ubuntu distros fail at the base system install.  Many of the packages can't install because they are corrupt.

Good to hear that you are booting, but have to ask:  have you made some free-space on that drive to accept the installs?  I guess are you telling guided partitioning to "use the entire drive" each time you try an install, or are you telling it to use "free space", which you may not have much left? :)

---

### Post by emackey3k on 2008-07-01
I am telling the guided partition to use the whole disk.  There could be a good chance the hard drive has some errors that is preventing the packages to write to disk.

---

### Post by stream303 on 2008-07-01
Maybe you could force an early fsck with the alternate or live installer - I'd have to look that up again.

You could also check the cd for errors.  With my alternate installer, at the second stage of the yaboot boot: prompt, hit -tab- to get a list of options.

For 32-bit ppc 
```
check
```

or for 64-bit PPC G5's:
```
check-powerpc64
```

---

### Post by emackey3k on 2008-07-01
What is weird is the checksum5 matches after I download the iso, it matches after I burn it to disc, but it fails when I check the disc when I put it in the iMac.

---

### Post by stream303 on 2008-07-01
It seems to be pointing to the cd-rom.  Is the lens dirty?  Maybe blow it out with some air?  The cdrom could just be on it's last legs.

Some things I'd try:

Where are you downloading the images from btw?

You could try a different brand of media.  Or, perhaps fall back to an older release that might have different timing in the drivers - I'd give Feisty 7.04 "alternate" a try - just to see if you have a corner-case with timing issues.

---

### Post by emackey3k on 2008-07-10
Thank you for you help.  I have given up on it, I believe it is a bad cd drive and is not worth replacing.  Thank again for the responses.

---

### Post by DRM_free on 2008-07-10
> **emackey3k said:**
> Thank you for you help.  I have given up on it, I believe it is a bad cd drive and is not worth replacing.  Thank again for the responses.

The fact that OpenFirmware was able to load the Linux kernel from the CD and execute it seems to indicate that the CD-Rom drive is working fine. Much more likely is that the ide/pmac.c driver that controls both the CD-Rom and hard disk has been broken by recent modifications to the code.

I suggest capturing the output of the 'dmesg' command and filling out a bug report on the [Linux kernel bugzilla]("http://bugzilla.kernel.org").

---

