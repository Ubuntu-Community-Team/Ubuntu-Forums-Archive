---
title: "Vista dual boot problems"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by age99 on 2007-09-06
Hi, I am trying to become a new Ubuntu user, but running into some problems setting up a dual boot with Vista.

I'm using version 7.04 on a live install CD.  

I have a Dell XPS M1330 machine, and it has one hard drive.  Any time I try get the install started from the boot CD, it crashes giving me this error:

/bin/sh can't access tty

it leaves me at a prompt and I have no idea how to get it back going again.  I've tried to follow some of the online tutorials for this, but with no luck.

Thanks

---

### Post by alienexplorers on 2007-09-06
Try hitting F6 for boot options and typing in:
> acpi=off
noapci

---

### Post by Sef on 2007-09-06
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Did you check the disk for errors?

---

### Post by age99 on 2007-09-06
Disk works fine althogh I cannot run the disk check because the same error occurs.

---

### Post by Sef on 2007-09-06
[Solution 1]("http://ubuntuforums.org/showthread.php?t=415009") (post 20):

> Quick solution to try guys:

When booting with livecd (Feisty 7.04) you could just try the option that says "Boot with Driver CD", but just keep the regular livecd in the drive and press enter both times when prompted to do so. This worked for me, so you guys may as well try it.

[Solution 2:]("http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error")

> Some Solutions to the ‘job control mode off’ error

So, here I present my summary of the ‘non-technical’ things you can do to correct the “/bin/sh can’t access tty; job control mode off” error and get your distro working. I’d suggest you follow these various alternatives step by step.

   1. Pop a blank floppy disc in your drive at bootup.
   2. and/or enter your BIOS (often achieved by pressing escape at system startup) and change the boot order of your system such that your hard-drive boots first, then CD-ROM and then Floppy (if you have them).
   3. Ditch the LIVE CD/DVD - and make sure you have the right distro for your system.. are you running an AMD x64 system like me? Try this version of Ubuntu Feisty Fawn. If you are running an INTEL based system, try this version
   4. Little known fact - there are ‘alternative’ iso’s available that (I believe) has different drivers that often correct the problem, and handle installs on older systems better. You can get the Feisty Fawn Alternative Version for AMD64 systems here, or the Feisty Fawn Alternative ISO for Intel systems here.


---

### Post by age99 on 2007-09-06
Neither of those options worked....

I'm completely at a loss here.  It seems that 7.04 doesn't jive with a lot of different hardware configs.  I'm hoping somebody has direct experience with the dell XPS M1330......

---

### Post by alienexplorers on 2007-09-06
Try looking at this page:
> [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330)

---

### Post by age99 on 2007-09-06
Well, at least I know that somebody did it, but that does not give any instructions on how it was done.....

---

### Post by age99 on 2007-09-07
Ok, looks like I got it sorted... somewhat.  Here's what I did:
[COLOR="Red"]
Boot up the livecd and when it gets to the first menu, select the Safe Graphics Mode and add the command:  break=top (Press F6 to add additional commands)

This will eventually crash and give a prompt where you add the following commands:
modprobe piix
exit

This should then work it's way all the way through the installation, although I did encounter quite a few issues, the first being that the install wizard went beyon the screen size and I couldn't figure out how to shrink the window.  The settings were also all messed up and it did not recognize much of the hardware, but most of that can be fixed up from info on other threads here.

All that being said, it was quite a pain in the butt, and more work than it was worth.  [/COLOR]

---

