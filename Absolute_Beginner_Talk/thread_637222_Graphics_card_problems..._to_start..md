---
title: "Graphics card problems... to start."
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by AngryMallard on 2007-12-10
I have the worst computer ever created. A Dell Dimension 2350 with all of the stock stuff in it except extra RAM, its hard drive, and the CD/DVD drives. And no matter what issues I have with it in Ubuntu, it seems as though the regular fixes for everyone else don't fix anything for me. 

After using 7.10 for about a week, I had to reinstall because something was wrong with the kernel. It worked perfectly, except I couldn't install any programs. Great. So I reinstalled, and THAT install worked perfectly, except for some reason Flash wouldn't work in Firefox. So I started AGAIN, thinking it would be easier to do that than to reconfigure my kernel or fix Firefox/Flash. Wrong.

Now the problem is that something is wrong with the video driver and when the system boots, it locks up just before it gets to the install screen and I see lots of vertical stripes. I know what you're thinking! Boot to recovery mode and do a dpkg-reconfigure xserver-xorg. Normally I would chose the Intel driver, because this computer is a piece (I got it for free, I would NEVER voluntarily buy a Dell) and has integrated graphics. 

This time it doesn't matter what driver I pick. I've tried the Intel, i810, vesa, vga drivers as well as played around with all of the other settings in the xorg.conf file. Nothing is working. If anyone out there has a magic fix, besides tossing the Dell and buying a decent computer, I would love to hear it.

---

### Post by Orestes on 2007-12-10
Toss the Dell. ;)

Tried changing the driver to fbdev? Fancy posting your xorg.conf?

HTH

---

### Post by AngryMallard on 2007-12-10
I couldn't really post my xorg.conf because I can't actually do anything from that computer besides things from command line. So that would involve hand-typing it in my laptop. Let me try that driver and then I'll post my xorg.conf.

---

### Post by AngryMallard on 2007-12-10
OK. I tried that driver. I got a different set of stripes and then a little window saying that Ubuntu is running in "low graphics mode." I chose "continue in low graphics mode" but then nothing happened. I had gotten that screen before with a couple other drivers with the same end result... frustration.

Sometimes the computer locks up after boot on the login window with the psychedelic vertical stripes... other times I get the "low graphics mode" nonsense and then nothing.

What gets me is that this computer was working [nearly] flawlessly before this one particular install. At least the video driver was working.

---

### Post by Orestes on 2007-12-10
Your machines are on the same network, right? If your laptop has openssh-server installed on it, you can type

scp /etc/X11/xorg.conf myusername@mylaptopsipaddress:~/

on your dell, and it'll copy it into your laptop's home directory. 

But that's a bit L337 H4X0R. ;)

---

### Post by Orestes on 2007-12-10
Here's a thought:

Boot your Ubuntu Live/Install/Desktop CD.

If your graphics work, copy the xorg.conf from the live system over the one on your hard-drive.

I've done that in the past on my old Thinkpad T22.

HTH

---

