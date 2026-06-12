---
title: "Noobie with Boot Problems"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by tbone02 on 2007-08-22
OK.  I'm almost a complete noob, so go easy please...

I installed ubuntu 7.04 server on my old win2k pc.  AMD 1ghz, 400MB, 2 ide hdd, first is 40GB and second is 8GB.

Then I installed the ubuntu desktop so that my transition from windows to linux might go smoother.

My goals are to establish a web server, mail server, and ftp server over my dynamic ip address (cable).

Then I attempted to download some packages for configuring apache2 to begin with.  When I rebooted, the system never booted.

grub started stage 1.5 and stopped with an Error 17 message.

I could restart but the same thing happens every time.

I researched this problem on this board and google and found out about supergrubdisk, which I downloaded, burned, and booted to from a cd.  I've run all of the sgd scripts available, but to no avail.  During this process, the only thing that was successful was removing the old grub installation from the mbr.  Now when I boot from the hdd, i get an invalid system disk error.  I tried to reinstall grub and it doesn't install.

I've also tried to boot from a 7.04 live cd and a 6.06 live cd.  I have tried to install to HDD all over again and I get the following:

Buffer I/O error on device hda, logical block 0

over and over
and eventually:

ldm/validate/partition/table():  Disk read failed.
Buffer I/O error on device hda, logical block 0
Buffer I/O error on device hda, logical block 0
Buffer I/O error on device hda, logical block 0
Buffer I/O error on device hda, logical block 0
Buffer I/O error on device hda, logical block 3
Buffer I/O error on device hda, logical block 3

throw in some logical block 1s and 2s and it just keeps repeating for a few minutes with similar errors.

Eventually it breaks out of this and moves onto the installation screens, stalls for a long period on "Trying to enable the frame buffer...", then I select language and keyboard, only for the installation to completely hand up on the "detecting hardware, please wait...".  It just stays at 0% forever.

I've searched and can't find any other way to solve this problem, can anyone help?

Thanks in advance!  Remember, I'm a noob.

edit:  While I was typing this post, I was trying to reinstall to the harddisk from the livecd and it IS actually progressing.  Although I'd estimate it's about 10-20 times slower than it was the first installation.  It got stuck detecting CD-Roms for about 5 minutes, then it got stuck detecting HDD for about 5 minutes, as I type it is sitting on detecting other hardware.  Now it has a blue screen.  I am glad it is progressing, but am also leary because it is taking so much longer than it did the first time.

---

### Post by southernman on 2007-08-22
I hate to tell you this, but it sounds as if you have a dead/dying hard drive. Although you may be able to feel it spinning... or hear it spin up, doesn't mean it's a working drive.

My advice is to grab [SystemRescueCD]("http://www.sysresccd.org/Download"). It has a nifty tool on it that you can run called TestDisk. It isn't overly complicated to use, but you'll need to do a bit of reading.

I really think your going to be in the market for a new HDD.

Good luck!

edited - You can do this on the Ubuntu Live cd as well, but you'll need to install testdisk into your ram to do so.. simply by doing the following things:

Go to Applications > Accessories > Terminal

In the terminal window that comes up do:

> aptitude install testdisk

to begin running testdisk, simply do this at the command prompt once it's installed

> testdisk

now just follow the really intuitive guide once in the program

---

### Post by tbone02 on 2007-08-22
During the partition, I get the following:

Input/output error during read on /dev/hda

ERROR!!!


I can retry and get the same thing.  I can also ignore or cancel.

I'm concerned that my hdd is fried for some reason...

Any suggestions?

---

### Post by tbone02 on 2007-08-22
> **southernman said:**
> I hate to tell you this, but it sounds as if you have a dead/dying hard drive. Although you may be able to feel it spinning... or hear it spin up, doesn't mean it's a working drive.

My advice is to grab [SystemRescueCD]("http://www.sysresccd.org/Download"). It has a nifty tool on it that you can run called TestDisk. It isn't overly complicated to use, but you'll need to do a bit of reading.

I really think your going to be in the market for a new HDD.

Good luck!

edited - You can do this on the Ubuntu Live cd as well, but you'll need to install testdisk into your ram to do so.. simply by doing the following things:

Go to Applications > Accessories > Terminal

In the terminal window that comes up do:



to begin running testdisk, simply do this at the command prompt once it's installed



now just follow the really intuitive guide once in the program

Well, I'm beginning to think you are probably correct about the harddrive.  I will try to find the program you referred to, although I won't be able to boot linux to run it.

However, I just had an idea.  I can try to install ubuntu on my secondary harddrive (8MB).

Thanks again!

---

### Post by southernman on 2007-08-22
You can install it all from the livecd... it will use your ram to install it into. Doesn't involve a harddrive at all.

Yeah, you could install on the 8GB drive, and it would work for a temporary solution. Don't do any fancy partitioning just use a 800MB swap file and the rest as /

If you intend to install a lot of other applications.. keep an eye on disk space with df -h at the command prompt.

---

### Post by tbone02 on 2007-08-23
> **southernman said:**
> You can install it all from the livecd... it will use your ram to install it into. Doesn't involve a harddrive at all.

When I boot from the livecd, and it brings up the menu screen, what option do I choose to run linux without involving a hdd?  I don't think I've been able to do this.  The options (as I remeber them from work) are:

install to hard drive (involves hdd)
repair installation (involves hdd)
check cd for errors (doesn't involve hdd, but doesn't run linux)
boot from hard drive (involves hdd)

There may be another options, but I can't remember what it is...

So how do you boot the livecd and simply run ubuntu from the cd/ram?

Here is a link to the "graphical installation"
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

However, my cd menu screen doesn't include the same options.  It doesn't give the option to "start or install ubuntu" but rather "install ubuntu to hard drive" or something similar.

FYI, I have tried both the 6.06 and the 7.04 server cds.  Should I burn a livecd of the desktop 6.06 or 7.04 and run that?  I'm assuming that the server cds do not have livecd capabilities because they don't include the graphical desktop...?

---

### Post by southernman on 2007-08-23
> **tbone02 said:**
> When I boot from the livecd, and it brings up the menu screen, what option do I choose to run linux without involving a hdd?  I don't think I've been able to do this.  The options (as I remeber them from work) are:

install to hard drive (involves hdd)
repair installation (involves hdd)
check cd for errors (doesn't involve hdd, but doesn't run linux)
boot from hard drive (involves hdd)

There may be another options, but I can't remember what it is...

So how do you boot the livecd and simply run ubuntu from the cd/ram?

Here is a link to the "graphical installation"
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

However, my cd menu screen doesn't include the same options.  It doesn't give the option to "start or install ubuntu" but rather "install ubuntu to hard drive" or something similar.

FYI, I have tried both the 6.06 and the 7.04 server cds.  Should I burn a livecd of the desktop 6.06 or 7.04 and run that?  I'm assuming that the server cds do not have livecd capabilities because they don't include the graphical desktop...?

Well ummmm, since the LiveCD is what you said you used (in your first edit)... I assumed you had it. So for this to work you either need to grab the livecd or the system rescue cd I mentioned at the beginning.

---

### Post by tbone02 on 2007-08-23
> **southernman said:**
> Well ummmm, since the LiveCD is what you said you used (in your first edit)... I assumed you had it. So for this to work you either need to grab the livecd or the system rescue cd I mentioned at the beginning.

I assumed that all of the installation cds were "livecds".  I'm guessing that was an incorrect assumption.

Is this correct?

Desktop installation cd is a livecd.  Server installation cd is NOT a livecd.

thanks again for your help, southernman.

---

### Post by southernman on 2007-08-23
None of the server installation cds are "LiveCD's."

As for Desktop Installation CD's then yes, you have two different types. The default CD you can download from Ubuntu IS the LiveCD. Not all systems can run the livecd due to video card and/or ram issues. The LiveCD contains both a GUI based installer and the text based installer.

Alternatively, when downloading the Ubuntu installation cd, there is a box for you to tick (just below the "start download" button) which will download what is known as the "Alternate CD" which only has the text based installer.

Because of the issues some have with the LiveCD's already mentioned (eg.. graphic cards or lack of ram), if asked, I suggest using the Alternate CD. If there comes a time that you need a livecd for recovering from a flubbed up system, I suggest the SystemRescue CD.

For what you need to do, I stand by the suggestion of SystemRescueCD since it already has the testdisk program on the CD. No sense in making the task at hand (eg... checking your hard drive) any more complicated than absolutely required.

Just tyring to help you along is all so no worries.

---

