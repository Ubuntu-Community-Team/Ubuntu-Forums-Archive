---
title: "Failed install on Power Mac G4"
date: 2014-02-03
forum: Apple Hardware Users
---

### Post by bosler on 2014-02-03
I bought a used G4 at a second hand computer/Electronics shop. It came with everything minus the hard drive. I installed one of my own, and when I've been trying to install 12.04 PPC, I CAN't even get to the installation screen. It keeps telling me that it's in low graphics mode, and asking me if I want to troubleshoot the resolution, use the current graphics for one session, exit to login, or reconfigure the graphics. 

I have tried all four of these options and regardless of what I pick, I end up at a command prompt with absolutely no idea how to proceed. 

From the the splash Ubuntu screen, if I go to the page that lists the details, I get an OK on all the entries except "Starting restore sound card(s') mixer state(s)" which fails.

I have even started a couple of boots with the Radeon resolution, color depth, and refresh rate listed at the very onset, but yet I always end up at the same screen if I do this or not.


Any help would be greatly appreciated!

---

### Post by moore.bryan on 2014-02-04
I'm not sure if you have a G4 with a PowerPC arch; if so, have you checked out the Ubuntu on PowerPC [FAQs]("https://wiki.ubuntu.com/PowerPCFAQ") and/or [Known Issues]("https://wiki.ubuntu.com/PowerPCKnownIssues") pages?

---

### Post by este.el.paz on 2014-02-04
> **bosler said:**
>  

I have tried all four of these options and regardless of what I pick, I end up at a command prompt with absolutely no idea how to proceed. 

From the the splash Ubuntu screen, if I go to the page that lists the details, I get an OK on all the entries except "Starting restore sound card(s') mixer state(s)" which fails.

!

@bosler:

Well, not sure if I can offer anything technical, as I'm a GUI user for the most part, but I have done a fair number of linux installs of various flavors, on various PPC machines . . . .  But not entirely clear what's happening with your install.  Have you been able to boot a LiveDVD of 12.04?  Do you have some form of OSX installed on the computer, so you know you can boot OSX, or you haven't been able to boot anything?

Other questions, looks like you have gotten to a boot prompt, in other words second log in window in Yaboot or TTY window?  At that prompt, you might try to hit the tab key, which will/should give you a list of various boot commands that you should try to string together usually the "live nomodeset" is the minimum . . . but sometimes you can find other suggestions onliine about adding stuff in for "video" . . . the hint on the "low resolution" might point in that direction, and or the "driver" . . . but the driver options might be listed in the "tab" . . . seems like something with "nv" is what works for many G4 units . . . so reading up on how to retro-compile the nv driver ***might**** help you out?????

But, then you are saying that you can get to the Ubuntu splash screen, which is usually a sign that something is working, rather than just getting stuck at the black screen or the split screen or other problems that might need an xorg.conf file adjustment . . . .  For the most part if the md5sum numbers are correct on your .iso file???  It is usually fairly easy to boot the LiveDVD and even get through the install process . . . but, that doesn't necessarily mean you will be able to see anything when you go to boot it . . . you can find a number of threads talking about how to use the TTY command line to make adjustments . . . when there is no video . . . so, essentially blind . . . .  A sense of humor is required when working with PPC . . . .

Best deal is to have a dual-boot HD set up running whatever OSX is suited for your computer as the "base" system, and then have a partition to play around with linux . . . using Yaboot or whatever works for your computer to switch, or using the "option" key to select the system/disk you want to boot . . . .  Best of luck.

e.e.p.

---

