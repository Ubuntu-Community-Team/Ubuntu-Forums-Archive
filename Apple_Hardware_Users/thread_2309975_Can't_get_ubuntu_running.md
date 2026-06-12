---
title: "Can't get ubuntu running"
date: 2016-01-15
forum: Apple Hardware Users
---

### Post by amos4 on 2016-01-15
I've tried the latest 14.x Desktop and Server, and 15.x Desktop.  

The hardware is a Mac Pro 2008 3,1.  Quirk:  The machine has two video cards, an AMD 7950 and an Nvidia GTX980.  There are three monitors hooked-up to the AMD, and none on the Nvidia.  The purpose of the Nvidia is for GPU-based computing for science. 

I'm using the latest rEFInd.  In terms of discs, tray 2 has an SDD where Mac OS is the first partition, and I want ubuntu's root on partition 4.  An HDD in tray 4 has four partitions for /usr, /var, /home, and swap.  

All the livecd's boot just fine.  Install appears to go properly.  No bootloader is installed, consistent with the rEFInd instructions.  

On the first boot after install, the run appears find until it attempts to start X.  I then get a dialog (all three monitors are mirrored) that it could not configure graphics and will go into low graphics mode, and I have some options.  I'm able to get into the terminal at that point, at least for that boot.  

On subsequent boots, I go straight from the BIOS screen to a situation where monitors 2 and 3 are getting no signal, while monitor one is a black screen with a small number of very thin verticle stripes.  Nothing happens from there. 

Most options added to the kernel command line from rEFInd have no effect.  I've tried text, emergency, gfxpayload=text, nomodeset, and as I recall a few others.  There is no noticeable effect.  One that *does* have an effect is fbcon=map:1.  With that set, I at least get some on-screen logging during boot.  The boot appears to run fine and I get a CLI login prompt for a half a second.  Then the monitors flash, and all three monitors go black except for a NON-blinking cursor in the upper left. 

After booting into Mac OS and looking at the logs, I do see a crash file from the launch of X.  Of interest: in the xorg log files, it shows that the system is trying to use the Nvidia card, which has no monitors, instead of the AMD card.  

To try to fix that problem, I tried booting off the livecd, chrooting in, uninstalling the nouveau driver, and rebuilding initrd.  At that point, it would boot and give me the "could not configure graphics" screen on every boot.  But, when I would try to leave that screen to go to either low graphics or the terminal, I would instead get a screen that was grey with that xwindows-is-waiting-black-X-cursor in the middle, frozen.  

I then tried chrooting in again, this time I tried to replace the default driver on the AMD with fglrx.  The result was back to the black screen with thin purple stripes right after the BIOS screen. 

Oh - one thing I tried, is that rEFInd has an option to tell the video cards they're booting in Mac OS even if they're booting into linux.  This supposedly helps some systems with two video cards.  It had no effect here.  

Note that the issue may be limited to video not displaying.  The logs, which I can inspect from Mac OS, don't show crashes, other than a crash starting X.  syslog etc appear to show a normal boot -- when I shut the machine down to get out of the freeze, the logs record that I've pressed the power button, and the logs show services shutting down.  

Interestingly, I was able to get into a CLI *once*:  When the system found errors on the root disk, it booted properly into the emergency environment.  However, subsequent boots were back to the same.  And, as above, specifying emergency on the kernel command line has no effect.  

I've tried discussing this with folks in the IRC chat (who were very helpful with a number of troubleshooting steps, including a bunch of what I've described above).  But they and I have exhausted our range of ideas.  

Help? :)

(Before anyone say anything -- the entire reason I'm trying to get ubuntu running is so that I can use one piece of software that depends on CUDA and only compiles on linux.  So altering the video card configuration is not really an option; I need to try to find a way to get it to work with the existing hardware.)

---

### Post by este.el.paz on 2016-01-16
@amos4:

The quickest, easiest, and possibly best answer would be to try to run linux in a virtual environment . . . of your choice; that way OSX is handling the hardware/video side . . . .  I think that would suffice, considering you only want to run one application . . . .

Going into the issue a tad bit, from reading posts from the AmigaOne guys trying to get Ubuntu MATE 15.10 && or 16.04 running, and there seem to be some G5 guys in there . . . but point being there is some "issue" with AMD video cards in the linux world . . . .  So you could read through the posts on "Testers wanted for Xu/Lu/MATE 16.04" . . .  it's near the top of the list right now . . . and find the links these guys are posting to other forums--for those posts relating to your question, etc.

For sure I recall that "luigiburdo" seems to have had problems with amd graphics on his G5 . . . .  So, other option, try to set up the Nvidia card to work as default . . . install the "recommended" nvidia drivers . . .  should be in "additional drivers" . . . and, ***probably*** you would be "good to go."

e...

---

### Post by amos4 on 2016-01-18
@este.el.paz - Virtual environment won't work, the one application I need to use needs to access the GPU for CUDA.  

Also, the monitors are hooked-up to the AMD, so having the nvidia recognized properly (which it is) isn't going to help exactly. 

The AmigaOne, all that stuff, isn't that all about PowerPC hardware anyway?

---

### Post by este.el.paz on 2016-01-18
> **amos4 said:**
> @este.el.paz - Virtual environment won't work, the one application I need to use needs to access the GPU for CUDA.  

Also, the monitors are hooked-up to the nvidia, so having the nvidia recognized properly (which it is) isn't going to help exactly. 

The AmigaOne, all that stuff, isn't that all about PowerPC hardware?

> There are three monitors hooked-up to the AMD, and none on the Nvidia.   The purpose of the Nvidia is for GPU-based computing for science.

@amos:  Yes, it is PPC, but, what you would be looking for is if they list what their boot params are for the AMD card . . . that would be likely to be similar for you . . . minus the "powerpc" . . . etc.  Other than what I've mentioned I don't have experience with multiple monitor set-ups . . . even though my 02 iMac had problems getting video running because it had two DVI ports???? . . . that was a while back . . . .  Other option is for the purpose of getting a linux system running, just use one monitor . . . ???  Start easy, then, add monitors later . . . .

e...

---

### Post by amos4 on 2016-01-18
So the current status is, I am able to boot consistently into the CLI.  *Once* I was able to get all three monitors working, but I don't recall exactly what I did other than that I had to plug them in one at a time.  Every time since, if I boot without an xorg.conf, I just get a freeze.  If I boot with an xorg.conf custom-made for the three monitors, it recognizes the first two monitors.  But, when it gets to the third monitor (DVI-0), instead of seeing the third monitor, it recognizes the second monitor (DisplayPort-1) twice.

---

### Post by amos4 on 2016-01-19
Sorry, but I think its pretty straightforward why advice from a few years ago about a completely different hardware architecture, isn't helpful at all. 

In fact, if you look at the page you referred me to, the advice on those pages is to adjust the parameters of the PPC-specific bootloader. 

Does anyone else have suggestions?

---

### Post by Benjamin_Brink on 2016-02-09
Have you considered using just the CLI via an ubuntu-server installation accessed via ssh?
If one screen is usable during installation, apt-get install openssh-server after install.
On reboot, use another computer to login to ubuntu system via ssh/CLI and convert ubuntu-desktop to ubuntu-server. No need to use any screens on your computer.

---

