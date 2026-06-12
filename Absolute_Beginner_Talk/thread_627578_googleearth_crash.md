---
title: "googleearth crash"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-11-30
Having looked at every thread I can find, I can discover no solution to attempting to start GoogleEarth and each time crashing Gnome/Xorg.

GE worked fine on my Edgy box, but the update to GE 4.2 killed it.

The new install of GE from Synaptic on my Gutsy box is a train smash.

Yes I have installed glibc but still a mess.

Like everybody, I expect problems installing something NEW, but it's most vexing to lose something which used to work fine (on the Edgy box)

Let's hope a solution is coming soon.

Thanks to all who've posted on this topic.

Cheers to all.

Mike.

---

### Post by quandary on 2007-11-30
first 4.2 is beta. It's not uncommon for beta software to be buggy...
second, 4.2 works well on my computer, so I suppose that either your file is corrupted, or that you did install it improperly, or that you have a graphics driver whose OpenGL implementation is buggy.

I would first check the md5 checksum on your download. uninstall it. download it again, and try again, because that's most likely the cause of the bug you are describing. 

Maybe you should also run the install as root.

---

### Post by dwiedenfeld on 2007-11-30
I didn't realize GoogleEarth was avaialble for Ubuntu! Cool! But...:(

When I just tried to load it through synaptic (googleearth 4.0.2735.0-0medibuntu4) I got a failure, that says "W:Failed to fetch..." and "404 not found". 

I checked the repositories I have enabled and [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/)  feisty free non-free is there and checked.

So why can't I get it? Is the server just down?

Using Ubuntu Feisty.

---

### Post by MichaelSM on 2007-12-01
Hi Quandary.

I appreciate your response.

It's pretty hard to install stuff on linux WITHOUT being root, especially from the repos.Unless entering one's admin password when Synaptic starts up is different from installing as root.

It's a fact that GE used to be easy-as on Ubuntu Edgy, at least in my experience. 

I'm not a computer programmer, so some suggestions you made in your reply aren't of much use to a common user.

If you look around, there's plenty of posts about this matter.

Since your own set-up is functioning so well, It would be a lot of help to a lot of people if you would assist us with details of your system and its parameters re. GE release and other stuff.

That's what the Forum's for. We're here to help each other.

Cheers,

Mike.

---

### Post by MichaelSM on 2007-12-03
Replying to my own thread ....headache.

I hope this assists someone, even though it's messy as an explanation.

OK. On my Edgy box I took out the 1998 model ATI AGP card (which used to run GE without a hassle until the latest GE update) and whacked in a 64meg nvidia AGP card which crashed xorg -no surprises there - and then I reconfigured xorg to VESA drivers which didn't work, So I enabled the nvidia drivers instead and after some reboots finally got my Desktop back.

Next(remember this is Edgy) I installed ENVY from Synaptic and fired it up. It recommended an automatic install of the latest nvidia drivers so I went for it.

What occurred in the ENVY console box was a series of downloads, installations, uninstallations, collecting and disseminations etc. which went on for several minutes to my amazement. Once ENVY concluded its machinations, and after a re-boot, Google Earth ran like a dream. Thank the gods for ENVY (on Edgy)

Now, back to my Gutsy box which seriously crashed Gnome with the nvidia agp card swapped to the Edgy box. 

I plugged in the old ATI card and got a mess which Gutsy defaulted to a poor screen resolution eventually. Terminal 'sudo dpkg-reconfigure -phigh xserver-xorg' Nothing much happened as I didn't get into the xorg blah setup, but suspecting something had happened I re-booted the Gutsy box.

Not only the screen resolution became far better, but Google Earth opened and RAN.

ENVY is not in the Gutsy repos.

Given the above scenario, is it needed for Gutsy?

If not, thanks and many thanks to the Gutsy compilers.

I make a lot of posts which appear complaining about changes in various parameters with different Ubuntu distros.

Many thanks to nowshining who replied to an xorg crash thread I started. Fortunately I kept notes, especially regarding Ctrl-Alt-F1 command which gets one into a place where 
one can access the system without Gnome.

Thanks to all.


Mike.

---

### Post by arvevans on 2008-06-10
I am another who used to use Google Earth on earlier versions of Ubuntu, but now with 8.10 Hardy it brings up the GoogleEarth splash screen and immediately reboots the X-server.

Having installed, tried, and uninstalled GoogleEarth several times since upgrading to Hardy, I'm about out of options and patience.  Any reasonable suggestions would be much appreciated.


[LIST]
[*]Video = Via Tech. K8M890, with 1200 X 1024 LCD
[*]CPU = AMD Athalon 64X2 3800+
[*]RAM = 1 GB (63% free)
[/LIST]

glxgears runs flawlessly.

Thanks,
Arv
_._

---

