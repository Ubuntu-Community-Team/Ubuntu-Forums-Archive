---
title: "Would an earlier version boost performance?"
date: 2008-06-12
forum: Apple Hardware Users
---

### Post by gphaze on 2008-06-12
I am using Ubuntu Hardy Heron right now on a G4 Mac Mini and I am *extremely* happy with Ubuntu.

I couldn't say enough nice things about it, and I still am not yet that skilled with the linux environment. Been a Mac user for 20 happy years.

One of my reasons for trying Linux in the first place is that I have read that Macs can perform faster on a Linux install than they can on OS X, because Linux is "lighter" on the processor than is OS X.

Not sure of the right phrasing there, but I get the idea that Linux requires fewer resources, and is therefore faster than OS X on the same piece of hardware.

Not that Hardy Heron is lacking, but I can't say that it's faster. It's about *as* fast as OS X.

So, I wonder about the merits of trying an earlier version of Ubuntu to see if I can get the speed boost I've read about.

Any thoughts on this?

thanks!

gphz

---

### Post by avtolle on 2008-06-12
Well, you might try Xubuntu, or Fluxbuntu to see if the use of lighter-weight DEs might help a bit. If you are really into this, a minimal install and then a "ground up" installation of the precise applications, appropriate drivers, etc. you want might help "speed thing up". Remember that in the end, the limiting factor is going to be the speed of your CPU.

---

### Post by influx.ca on 2008-06-12
I recently tried  both 6.06.1 and 8.04 on my G4 ibook (which is essentially the same machine in this context) I kept 8.04 simply because I was able to get everything working that I needed (airport extreme, smb connectivity, trackpad support) with minimal difficulty. The install handled 95% of what I needed it to handle.

I found no discernible differences in performance between the 2 versions of Ubuntu. I did however notice a slight increase in performance from Tiger to Ubuntu. Weather this difference was perceived or actual, I don't know. Point being, it *felt* faster.

That being said, if you are new to Linux (like myself) you may get other benefits out of trying different versions on the Mini. I feel I wouldn't have had as much satisfaction and a sense of accomplishment if I had of just went with 8.04 first and had the smooth install I did. Finding out how to get things to work helps you learn and gets you involved in the community. So I guess what I am trying to say there, is try it out for yourself and see what happens. :)

---

### Post by aysiu on 2008-06-12
An earlier version will not give you better performance.

You can, however, try a window manager instead of a desktop environment (Ubuntu defaults to the desktop environment called Gnome). I'd recommend you try the window manager called IceWM:
[http://www.psychocats.net/ubuntu/icewm](http://www.psychocats.net/ubuntu/icewm)

---

### Post by stream303 on 2008-06-12
In pre-Hardy releases, you might be interested in using the "noatime" parameter in your /etc/fstab.  See the threads about this one.

More ram is definitely a big plus if you are constantly using swap.

You can install a lighter-weight desktop, but that won't magically fix heavyweight programs like Firefox, OpenOffic, Gimp, etc.  Search out lighter weight alternatives.  One of my newest favorites is the PcManFm file manager.  Many other light-weight applications may be of interest rather than the default ones in Ubuntu.  (I use ogg123 [part of vorbis-tools] at the commandline for streaming audio, rather than rely on gui apps for the most part as an example)

Is your video card set up to perform it's best with the necessary options?  Depending on the card, you can boost speed that way as well - see the faqs for ATI especially.

Do you absolutely need 24-bit color depth?  Not editing photos or just doing simple general purpose work?  You might be able to drop your color depth down to 16 in xorg.conf and see a nice improvement there.

Aside from adding ram if you are low, there are many things you can do to boost your apparent speed.  It can be a nice sub-hobby to see how far you can take your machine with it's built-in limitations.

---

