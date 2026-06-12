---
title: "Ancient Computer: Setting up Ubuntu (again)..."
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by Onos on 2006-01-10
**The Computer:** It is pretty much a stock machine bought at a Radio Shack, definitely not a "hot rod" computer. I have not modded it at all.

**Compaq Presario** (unsure of exact make, bought it in 2001)
[LIST]
[*]Celeron (P4 compatible) 1200~MHz
[*]Nvidia "Vanta LT" 16MB Graphics card/chip
[*]USB Camera (some make of Toshiba)
[*]20GB IDE main hard drive
[*]Generic Compaq CD-R/W installed
[/LIST]

**OS:**Running **(X)ubuntu Breezy Badger 5.10** with XFCE windows manager

**The Problem:**
[LIST]
[*]High maintenance, unable to get everything working with out an enormous time commitment; 
[*]I probably shot down its performance by trying to tweak it to look like those really cool screenshots with the nice compositing effects (HOWTOs listed on these very forums). It is very slow at the moment... just moving a window makes it jump to 100% CPU usage.
[/LIST]

**The needs:** While I do not necessarily mind tinkering and re-formating and re-installing distros ... my wife wants a working computer soon.  And re-installing windows is the very last option I want: I only keep Win2k on my PC because I needed it specifically for VPN into my work computer when I telecommute.
[LIST]
[*]Japanese / US language input (used **UIM-anthy** so far, no problems)
[*]media player(s) to handle Quicktime, RealMedia, .asx, .wmv with both audio and video (currently using mplayer, but audio stream fails. gzine works, but is also hit-and-miss).
[*]USB camera operability
[*]printer share for HP Photosmart 7660 (works as a local printer)
[*]OpenOffice (assuming it works well enough) for porting documents to WIN platforms
[*]relative speed and ease of use: keeping bloatware to a minimum.
[/LIST]

It need not be "strained" to do things beyond its limits; my wife uses the PC mostly for viewing/updating her various blogs, doing email, online banking, and minor photo editing. And editing Excel/MS Word-slash-OpenOffice documents.

**Issues:** I am unsure of which Ubuntu variant to re-load... 
[LIST]
[*]**Ubuntu** with Gnome (the "stock" install, supposedly bloated and a bit slow running on my ancient machine)
[*]**Kubuntu** with KDE (even more bloated, but much more configurable... I will probably not consider this in light of my speed situation)
[*]**Xubuntu** with XFCE (seemed like a good idea at the time: it loaded fast and had a clean interface... until I messed it up with that compositing stuff.  Also, XFCE seems not to be as well supported yet by Ubuntu as is the KDE and Gnome DE's, requiring much tweaking out of the box.  Perhaps its day will come with Dapper Drake?
[/LIST]

My next step is most likely to eat my humble pie and accept that I will have to wait longer until I can afford that $900+ USD "hobby machine" to play with Linuxes on to my my hearts content... 

...and pop in the LiveCD, reboot, and put in the stock install with Gnome and run Automatix so Mrs. Onos can have a reasonably well-working computer, although I might need to do some tweaking to get the USB camera, printer, and uim or scim working again.

Sorry for the long-winded post... but I would appreciate it greatly if someone could check my thinking on this and possibly steer me in the right direction. :)

---

### Post by fuscia on 2006-01-10
are you planning to do the 'server' installation?

---

### Post by carlosqueso on 2006-01-10
You shouldn't have any problem...as my machine is a lot more ancient than yours.  I'd just install Ubuntu...it shouldn't have any problems.  If you want to use xubuntu, let me know and I can talk you through a setup.  The camera should work fine in gnome or XFCE with the gnome-volume-manager.  Printers are a little more problematic.  OpenOffice is good, but I like abiword and gnumeric because they're faster and gnumeric has statistics functions.  I'd just reinstall.  Like I said, if you're interested in using XFCE (I do) I'd be happy to help with that too.

---

### Post by Bartender on 2006-01-10
Didn't understand your comment about the compositing effects.  Do you mean you've got a busy desktop wallpaper?  Set the computer back to "None".  That's how my very capable home-built M$ machine is set up.  Why bother with the glitz if you suspect it's interfering with what you need to get done?  
This Compaq you're talking about; it's got W2K on it now, right?  Not Linux yet?
Something you didn't mention.  How much RAM?  W2K and XP aren't very happy with less than 512.  Betcha that old Compaq came with 256.  If you've got 256 for system memory and only 16 on the vid card that would go a long way toward explaining general sloth and especially graphics intensive slowdowns.  More RAM also means your HDD won't be so busy all the time, which is a good thing.  Does the HDD churn a lot every time you ask the computer to do anything, even small tasks?
From comments on this forum, Ubuntu will run just fine on older computers but you might as well consider its RAM requirements to be comparable to XP.  You can run it with 256 but apparently 512 gives a big boost.  Unless you install the stripped down server version.  Being a newb myself, I can't imagine not having the GUI.
EDIT: I definitely wouldn't wait to buy a more capable machine.  The time to begin your Linux learning curve is yesterday.

---

### Post by mips on 2006-01-10
There really is nothing wrong with the spec of that computer. You did not mention how much ram you have ???

If I was you and had a little bit of cash lying around I'd pop some more ram into that machine seeing ram is relative cheap and it helps a lot in system performance.

I would simply install Kubuntu. The KDE environment would be more familiar to a windows user compared to Gnome. KDE is nice and I find it more configurable, I only switched 2months ago after using Ubuntu since v4.10.

You can also fine tune the OS to speed it up, there are some guides around here somewhere.

What VPN software/server do you use on Win ? Might be possible to do in Ubuntu.

---

### Post by Delkster on 2006-01-10
I've set up a computer based on a Duron 1000 MHz running Ubuntu with the Gnome desktop. It's a wee bit slow at times but since it has 512 MiB of RAM and a decent -- albeit not very modern -- graphics card (GeForce 2 Ti with the proprietary NVidia driver), it's quite workable. OpenOffice 1.x, and its startup in particular, used to be quite slow with it but 2.0 should be a bit slicker. I haven't tried it, though.

I wouldn't suggest trying composite with old graphics hardware such as yours.

Edit: If you use the proprietary NVidia driver, with hardware older than GeForce 3 (I think) you need to use the legacy version of the driver (nvidia-glx-legacy, the legacy version of your linux-restricted-modules)

---

### Post by Onos on 2006-01-10
**My setup has 256MB RAM,** and I have Breezy Ubuntu running (crawling, to be accurate) under XFCE.

The computer in question originally shipped with Win XP Home Edition, which after ME, is the variant of Windows I probably detest most.  I then experimented with gentoo on the advice of an old gaming friend of mine, but with my tinkering with things (yes, it is probably a bad habit of mine) I managed to blow up 17.5 hours worth of gentoo emerges, compiling and mucking about in various *.conf files.  

Configuring the gentoo install to pick up my cordless mouse was an excercise of patience to say the least. :p 

**Not wanting to put poor Mrs. Onos without a computer for too much longer,** I went to this (Xubuntu) distro, which to our delight, installed quite nicely, only missing my printer and the USB camera on the install.

I'm not sure of the exact type, would have to google the specs for that particular make when I get home later, or possibly open up the case?  I will need to check "under the hood" anyway to see if I have room for more memory, or if the motherboard specs will allow for a higher capacity RAM board.

Since I am likely to be short of cash for the foreseeable future, I will likely upgrade the memory as a short-term fix to make things run easier, if I can.

I must confess that I didn't think ahead when attempting to run the compositing effects (according to guides posted by poofyhairguy and someone else here)... that was what really dragged down my performance.  Short of knowing how to undo that bit of compiling I did last night (per the HOWTO) ... I am guessing a clean install will be the better thing to do.

**Concerning drivers:** Initially, I had had the default drivers from the original install.   The nvidia-glx-legacy drivers seem to work fine, the latest nvidia-glx crashed XFCE upon restarting.  Right now, it is a bit of a mess - compiled the nVidia driver pack 7174 for i386.

**@mips:** my VPN software is a specialized CISCO version for use by the Dept. of Defense, so it is not too likely I will be able to find a linux variant of it. I use it to remotely control my PC at my office from home, Win 2k to Win XP.  Aside from that and a small assortment of games, I keep Win 2k on that PC (that machine is a different PC from the one we are discussing)

**@Bartender and Fuscia:** I did the "server" installation as recommended by an XFCE setup guide I found through these forums.

**@carlosqueso:** I might take you up on your offer to help with an XFCE install.  I am attracted to the idea of a lightweight "DE" as gnome is a tad heavy, and with KDE, I don't know if I am coming or going with all the things it has going on.

For a basic XFCE install, I am looking at having at the least:
[LIST]
[*]**Thunar File manager** - gives a nice gnome-like treatment of the file system. (currently works on my wife's profile, but it is a bit broken in my profile)
[*]**conky** - gives a good status treatment of the mounted drives, particularly available drive space
[/LIST]

No more of that compositing stuff, at leat until I can buy my higher performance "hobby machine". :p 

As for Abiword and gnumeric - can they export files in MS format?  My wife does some translation work and the companies that she works with use MS Office. (shocker! :rolleyes: )


Is it possible to set up an option to log in to either gnome or XFCE?  That might work, with gnome as a fallback if I louse things up in XFCE again.

---

### Post by carlosqueso on 2006-01-10
Coolness....and now for your questions. Yes you can install thunar, I probably even have a .deb of the latest svn version around that you'd be welcome to use, but as always with these custom debs YMMV.  If you'd like it, I'll post it when I get home.  For mounting removable stuff like cameras and such, I use gnome-volume-manager (you can install it through (syn)apt(ic)).  Just run it once, and make sure to save your session when you log out of XFCE. It seems to work better than the default automounter in XFCE.  As for Abiword and Gnumeric, they're designed to export to the MS formats, although I haven't done much work in either (used OpenOffice until I graduated from college), so I don't know what results you'll have.

---

### Post by nihilocrat on 2006-01-10
If you want even less bloat, install fluxbox or blackbox instead of XFCE :cool:

... but I still think XFCE is good. It's my favorite of the window managers for a good balance between efficiency, good looks, and friendliness.

---

### Post by mips on 2006-01-10
[QUOTE=Onos]
**@mips:** my VPN software is a specialized CISCO version for use by the Dept. of Defense, so it is not too likely I will be able to find a linux variant of it. I use it to remotely control my PC at my office from home, Win 2k to Win XP.  Aside from that and a small assortment of games, I keep Win 2k on that PC (that machine is a different PC from the one we are discussing)[/QUOTE]

Ok, I know the Cisco VPN client is available for Win, OSX, Solaris, Linux etc. But if Cisco made specific changes to the code for the DoD as they sometimes do for certain clients then there is less hope but you never know.

---

