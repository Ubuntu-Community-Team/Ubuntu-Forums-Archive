---
title: "Mac mini screen blanks 5 minutes after starting TV or mplayer playback"
date: 2008-12-15
forum: Apple Hardware Users
---

### Post by justdave72 on 2008-12-15
I have an Intel Mac Mini with the DVI out connected via HDMI to an HDTV.  I'm running Intrepid + Mythbuntu, and the security updates are up-to-date as of this afternoon.  I have the screensaver in Gnome set to never activate, and the screen sleep and machine sleep times set to Never in the power management control panel.  When watching liveTV or playing back recordings in MythTV, or playing a movie with mplayer, the screen will blank to a solid color after about 5 minutes, and then stay that way.  If I switch to a different VT I get a text console just fine, but if I switch back to the X terminal it stays blank.  Restarting gdm doesn't fix it, so it's almost got to be something driver level with that particular video mode or something.  Rebooting the machine, and suspending it then waking it back up, both fix the problem, but only until the next time it happens.  Anyone have any ideas?

The mini has the Intel Integrated Graphics Controller, which Xorg identifies as follows:

(II) intel(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0

At the point when the video quits, the following it output to the Xorg.0.log repeatedly:

(EE) intel(0): underrun on pipe A!

I've been Googling around for a day or two on that error message and related terms, and haven't found anything useful yet.  Is anyone else having this problem, or know what I should look for?

Thanks!

---

### Post by justdave72 on 2008-12-16
I was running kernel 2.6.27-10 which is apparently the current kernel in intrepid-proposed.  I had someone mention to me on IRC that it sounds like a kernel bug that was recently fixed in 2.6.28rc8.  I pulled the current Ubuntu kernel source from Ubuntu's kernel git repo and built it, and it gave me 2.6.27-11, and so far, this does seem to have fixed the problem.  I'll post again if it turns out it didn't, but I've gone about 45 minutes with video going to the whole time, and haven't had it blank out yet, and that's the longest it's lasted so far. :)

---

### Post by justdave72 on 2008-12-16
Gah!  Figures.  not 5 minutes after I post that it blanks out again.  Ah well, back to the drawing board.  Time to pull the upstream 2.6.28-rc8 kernel this time since that's where this was supposedly fixed.

---

### Post by justdave72 on 2008-12-17
The 2.6.28-rc8 kernel didn't help any either.  So that's the end of that theory.  Anyone have any ideas what else might be wrong?

---

### Post by ralph1973 on 2008-12-21
Hello,
I use my mac mini as Ubuntu desktop (workstation) with a mailserver running in the background (in vmware server). I've got the same problem, that the screen blanks after a couple of minutes. It frustrates me, and it looks as if the newest release  (I run 2.6.27-9-generic) crashes sooner than previous releases. Only X 'crashes', I am still able to switch to a console, but I cannot restart X, I have to reboot, what means that I have to kill running processes first, gracefully shutdown my mailserver and then reboot. This is really annoying and I didn't find a solution yet (googled a lot for a solution). For me it means now that I start my windows pc and do my work on this one, because typing a document is too stressfull because the screen can blank out at every random moment. If anyone has a solution, please let us know!

Ralph
Arnhem, Netherlands

---

### Post by justdave72 on 2008-12-21
I've found that I can successfully recover it about 90% of the time by running "sudo pm-suspend" from an ssh shell, and then walking up to the machine and hitting the power button to wake it back up after it finishes going to sleep.  Pain in the *** when you're trying to watch a movie and it keeps dropping the video every 5 to 15 minutes.

---

### Post by justdave72 on 2009-01-10
So I found a bug on freedesktop.org that had a similar problem with this driver, and they had a couple settings changes listed in the bug to try.

[https://bugs.freedesktop.org/show_bug.cgi?id=18651](https://bugs.freedesktop.org/show_bug.cgi?id=18651)

The bug is actually about the screen flickering, and not blanking out, but I was getting that flicker as well.

I added the Option "FramebufferCompression" "False" to my xorg.conf and disabled compiz in Gnome (by turning off the effects), and it's been going three hours straight since then playing movies the entire time without blanking out.

---

### Post by justdave72 on 2009-01-12
Just to followup on my previous post, I've put in a good 10 hours of viewing time on that thing since doing the stuff I mentioned in the previous post, and haven't had it freeze up once, so at this point I'm going to say it's fixed (or at least successfully worked around).

---

