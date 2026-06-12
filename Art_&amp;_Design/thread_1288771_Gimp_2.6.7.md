---
title: "Gimp 2.6.7"
date: 2009-10-11
forum: Art &amp; Design
---

### Post by BMWDriver on 2009-10-11
Hi everyone.

It looks as though the latest Gimp version 2.6.7 is not in the repos for Ubuntu 9.04. I have some issues with Gimp 2.6.6 and would very much like to update it via the repos; seems much easier that way. 

I expect it will be on Ubuntu 9.10, however I never fully upgrade on top of my current install. I always dual-boot to remain safe, and then import my files until things are the way I want them to be.

---

### Post by Exodist on 2009-10-12
Nothing has chenged in 2.6.7 from 2.6.6. Just a few bug fixes. You will not see 2.6.7 to be in 9.04s repos. Doesnt look like 2.6.8 will make it to 9.10 either. Which is sad because it is slated to have many new features like full screen mode more on tune with Photoshop on the PC.

Its fairly easy to compile if you want to install the latest version tho.

---

### Post by mcduck on 2009-10-12
The basic rule is that packages in Ubuntu releases are only upgraded for security reasons and to fix serious bugs, so you are never going to see updates like that in Ubuntu's official repositories.

Anyway, you can get .deb packages for Gimp 2.6.7 from GetDeb.net: [http://www.getdeb.net/app/GIMP]("http://www.getdeb.net/app/GIMP")

---

### Post by BMWDriver on 2009-10-12
It's the bug fixes that interest me.

This was EXTREMELY useful in solving my problem: [http://lazyubuntu.com/how-to-install-gimp-267-on-ubuntu-904-jaunty-jackalope.html]("http://lazyubuntu.com/how-to-install-gimp-267-on-ubuntu-904-jaunty-jackalope.html") 
I uninstalled Gimp first.

FWIW, I've tried the beta of Ubuntu Studio 9.10 with the expected problems that I usually get with my ATI : no more Compiz 3D effects. Some problems too with the Wacom and my mouse being lefty configured.

Installation was a breeze with the official Jaunty, so I'm gonna stick to it for now. I'll try the official release of Karmic, maybe a few months from now. Then again, OpenSuse is tempting since they seem to have a graphical control thingy for Wacom. Dunno about Karmic.

Thanks for the input.

---

### Post by Niva on 2009-10-13
> **BMWDriver said:**
> 

Installation was a breeze with the official Jaunty, so I'm gonna stick to it for now. I'll try the official release of Karmic, maybe a few months from now. Then again, OpenSuse is tempting since they seem to have a graphical control thingy for Wacom. Dunno about Karmic.

Thanks for the input.

Thanks for the info on the issues you've encountered with 9.10, I'm guessing those would be polished out for the final release but it definitely makes me not want to upgrade when I hear stuff like this.

By the way the Opensuse utility is not good at all.  At least it wasn't back in the 10.0 days, I've not tried Suse since then so maybe they fixed the problems with it.  Let us know how it works for you.

I'm also curious what particular bugs did you experience in GIMP which caused you to need to upgrade?

---

### Post by kayosiii on 2009-10-13
> **Exodist said:**
> Nothing has chenged in 2.6.7 from 2.6.6. Just a few bug fixes. You will not see 2.6.7 to be in 9.04s repos. Doesnt look like 2.6.8 will make it to 9.10 either. Which is sad because it is slated to have many new features like full screen mode more on tune with Photoshop on the PC.

Its fairly easy to compile if you want to install the latest version tho.

Gimp has had fullscreen mode for some time just press F11. There is a hack that you can add to your config file. that will keep the toolbars on top of your image in fullscreen mode. otherwise you have to press tab to get them.

---

### Post by AJB2K3 on 2009-10-13
2.6.7 will never be in the repos because its a test release to test the changes.
Next repo version should be 2.6.8

Odd numbers= test version ( from gimps site)

---

### Post by kayosiii on 2009-10-13
Not so the 2.7.x is the test tree
2.6.7 is a minor bug fix release
2.8.x will be the next stable tree.

---

### Post by mcduck on 2009-10-13
> **AJB2K3 said:**
> 2.6.7 will never be in the repos because its a test release to test the changes.
Next repo version should be 2.6.8

Odd numbers= test version ( from gimps site)

There is no such thing as "next repo version", unless you mean that it might be in *next Ubntu release's* repositories...

Like I already said in this thread, the package versions in Ubuntu repositories are not updated, apart from security reasons and to fix serious bugs. Never just to provide new features or up-to-date program versions.

Ubuntu 9.10 has Gimp 2.6.7, and that's the only version it's ever going to have in it's repositories.

---

### Post by BMWDriver on 2009-10-14
A Gimp recurring bug was that I was unable to edit images unless I rebooted. I could select the window, tools and navigate through the image, zoom in and out, but the pen, brush and any other editing tool for that matter, would cease to function. Clicking in the image would not have any effect: no selection, no color change, no brush stroke, nothing. Closing the image, quitting and restarting Gimp proved useless. It was not a consistantly happening bug, but seriously bothersome.

So far so good with 2.6.7.

---

### Post by BMWDriver on 2009-11-19
Well, that's it. I had to kick Ubuntu Karmic from my system. I can't use one of the very important selection tools with Gimp because it hangs the system. I've tried Sabayon 5.0 (Gentoo) both under KDE and Gnome with the same issue. I suspect X or the Kernel. But, I've not had that issue with a live CD on another computer, with single core and about the same configuration otherwise.

Gimp also crashes under Vista on my laptop, but with only Gimp closing, with the same tool. I can at least restart Gimp and not have to reboot. Seems strange to me.

So, Bugzilla is my friend. 

Otherwise I'm back on the faithful Jackalope and sticking to it for now. I had never uninstalled it, preferring dual booting to make sure any other system I tried was doing good.

Perhaps I'll try Lucid Lynx when it comes out. Then again PC-BSD is also tempting.

---

### Post by AJB2K3 on 2009-11-19
> **BMWDriver said:**
> 
Gimp also crashes under Vista on my laptop, but with only Gimp closing, with the same tool. I can at least restart Gimp and not have to reboot. Seems strange to me.

Really? Haven't had 2.6.7 crash once yet but then its a 3gig ram 2gig duel core laptop.

---

### Post by BMWDriver on 2009-11-25
Yeah, I tried it on my other computer under a live CD, which has a 3.2 GHz Intel P4 single core and 2GB DDR, and that did not create an issue. The laptop is also a single core; it's a hyper portable with a 1.4 GHz Intel chip and 3GB DDR2, not a netbook but a step above.

Can't use that computer though until I upgrade next year. It's my HTPC and gaming rig, where my AMD is my graphics station. It's old (6 years), but very reliable otherwise and quite usable.

The ideal would be for me to downgrade to Gimp 2.6.6. under Karmic, but I can't do that without compiling, and I have tried and failed. It's a quite difficult endeavour!

---

