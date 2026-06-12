---
title: "Minimal Install CD for 64PPC AWOL?"
date: 2009-05-05
forum: Apple Hardware Users
---

### Post by casbahdk on 2009-05-05
I would like to install a minimal Jaunty 64PPC system, but I have been unable to find anything newer than Hardy at this link:

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

Is there somewhere else that the Jaunty 64PPC resides or have there simply not been any 64PPC minimal install CD images created since Hardy?

Is it possible to do an apt-get update, upgrade, dist-upgrade twice to end up with a minimal Jaunty system?

Cheers

---

### Post by stream303 on 2009-05-05
Still there:  (they just didn't put the updated link on the page, but it's there)

[http://ports.ubuntu.com/dists/jaunty/main/installer-powerpc/current/images/powerpc64/netboot/mini.iso](http://ports.ubuntu.com/dists/jaunty/main/installer-powerpc/current/images/powerpc64/netboot/mini.iso)

Just wait until you see the options of what you'd like to install - nearly ANY flavor.  I just did an install with it earlier tonight.  Nice.

Don't forget that since it is a very small kernel, on G5's your fans might scream like a vacuum-cleaner until after your first reboot.  Luckily it is only cold air that is blowing.  Kind of unnerving, but don't sweat it as after the reboot all should be well.

---

### Post by mkvnmtr on 2009-05-05
On the minimal install I have seen it recommended that you do an update and an upgrade before you start to install programs. So yes it is possible to upgrade from a 8.04 minimal install. But 9.04 is there. I downloaded it the other day just not had time to install. I would like to hear how it goes for you.

---

### Post by casbahdk on 2009-05-05
Thanks all around. Steam, what would you suggest that I install to get KDE, but hopefully avoid the display problems I have been experiencing with the Kubuntu PPC install?

Cheers

---

### Post by stream303 on 2009-05-05
Since the 64-bit version won't install on anything less than a G5, you must have one and that combination of hardware (if you are still using the same external monitor) might prove to have no troubles at all.  You could try the Kubuntu install option and see how it goes.

If the results are the same, we can pin it down to something about your monitor that needs to be taken care of in /etc/X11/xorg.conf.

Or, you could start with the goal of making sure that xorg.conf is going to work by ruling out other variables, like the GDM login screen.  In other words, do a cli-only or server install, and apt-get the xorg environment in which you start it at the cli with *startx* and run a simple window manager rather than a full desktop at least temporarily.  IceWM, fluxbox, openbox etc might make a good choice for a WM, at least temporarily until you find the magic needed in xorg.conf.

Once you get a working xorg.conf down, just save it, install your KDE environment, and then substitute your working xorg.conf back in.

Another fast way to determine if it is just your monitor that is giving you grief is to borrow one from a friend and see how that goes.

I'm not sure that just switching to Kubuntu will solve the problem, but you'll have to be your own pioneer.  To save bandwidth and time, perhaps try Xubuntu which is a little bit lighter.

As you try out the various options, you may want to burn a cd with all the packages you have downloaded so far in case you want to reinstall and try again.  For example, if you try the Kubuntu option right off the bat, after install, even though you may still not have your graphics working, burn the downloaded packages from:

**/var/cache/apt/archives**

Perhaps label it "Kubuntu 9.04 package backup".  If your graphics are still totally wack, you can burn these at the cli with *wodim* the replacement for cdrecord.

Just some thoughts ... this is always the issue with ppc, and now with xorg taking on smarter attributes while our hardware stays relatively unintelligent, makes each release an adventure in xorg.conf configuring unfortunately. :)

---

