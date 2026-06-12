---
title: "update problem....again"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by SteelCore on 2007-02-24
Hi guys,
Remember the update the caused the X server not to start properly a few months ago.  It just happened to me again.  I'm using 6.06 and on rebooting I'm getting the same message "Failed to start th Xserver (your graphical interface).  It is likely that it is not set up correctly..."

---

### Post by taurus on 2007-02-24
Maybe you need to reinstall the driver for your graphic card again.

Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure xserver-xorg
```

---

### Post by Henry Rayker on 2007-02-24
I'd be willing to bet that you have installed drivers for your video card that originated from somewhere other than the repos, haven't you? This problem tends to affect people who, in their search for 3d accelerated graphics, install a driver for their card from someplace other than the repos; then, when the kernel updates, X can't use that driver (it was compiled for the kernel you had been using, not the new one) and X freaks out.

Try using a previous kernel, or give some more information about your situation (video card, video card driver etc.) so someone can try to remedy this situation.

---

### Post by SteelCore on 2007-02-24
> **Henry Rayker said:**
> I'd be willing to bet that you have installed drivers for your video card that originated from somewhere other than the repos, haven't you? This problem tends to affect people who, in their search for 3d accelerated graphics, install a driver for their card from someplace other than the repos; then, when the kernel updates, X can't use that driver (it was compiled for the kernel you had been using, not the new one) and X freaks out.

Try using a previous kernel, or give some more information about your situation (video card, video card driver etc.) so someone can try to remedy this situation.

I don't think so.  I did previously activate 3d acceleration using advice I got on this forum (you can check the post).  But I'm positive I didn't install any drivers.  As a matter of fact I don't even know how to :confused:

---

### Post by Henry Rayker on 2007-02-25
You did install the drivers. The package "nvidia-glx" is going to be the driver you installed via the synaptic package manager.

In order to reinstall the drivers (because you've changed the kernel) you should log into the command line (when you get the X error, press CTRL-ALT-F1 and log in). Now, once you're logged in, I believe a ```
sudo apt-get install nvidia-glx
``` will suffice. You can also check your xorg.conf file to make sure everything is okay with that (ie, the video device is using "nvidia" instead of nv...similar to the problem you previously had in that thread of yours).

now, for my rant...mods edit it if I'm overstepping my bounds...I really don't think users should be installing software if they don't know what the package even is...I see this problem, for the most part, affecting users who install Beryl without understanding what it is they're doing. Beryl, at this point, breaks a LARGE number of users' installations every time there is a kernel update or similar and, as such, I really think all Beryl posts should be accompanied with a statement concerning this. My laptop has been running Ubuntu for over a year now, and I have NEVER had an issue with an update breaking my X. My girlfriend's PC has been running it for 4 months or so, and she's never had a problem either...because neither of us run Beryl. I'm not saying the app is bad, just the information concerning it is nowhere near being up to par. /RANT

---

### Post by SteelCore on 2007-02-25
Thank you for taking the time to help me on this.
I did enter the "sudo apt-get install nvidia-glx"
after it asked for my password it gave the following output:

Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
0 upgraded, 0 newly istalled, 0 to remove and 1 not upgraded.

After that I used Ctrl+Alt+Del to restart and the problem persisted

---

### Post by Henry Rayker on 2007-02-25
At this point, I would try the ```
sudo dpkg-reconfigure xserver-xorg
``` as suggested by taurus. Enter the information as it requests it. Check to see if that gives any more desirable results...

---

### Post by SteelCore on 2007-02-25
I did go thru that command when taurus first mentioned it but unfortunately could not answer most of the questions.  It would be unreasonable for me to ask for help on each of the configuration steps though I'm willing to read any available tutorial or guide on that subject.
BTW in case all fails I could easily reinstall Ubuntu.  My current files are graphically accessable if I use the freespire live cd within the ./home directory.

---

### Post by randiroo76073 on 2007-02-25
If you have one, use an ubuntu live cd, that way it's easier for someone here to guide/help you.  Try this command, it helped me:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by tyler_roach on 2007-02-25
When you do:
sudo apt-get install nvidia-glx
The computer senses that you already have it installed (even though it's compiled for the previous kernel), so it doesn't do anything at all.

To reinstall the drivers, try:
sudo apt-get install --reinstall nividia-glx

Or you could always fall back on the vesa drivers.

---

### Post by SteelCore on 2007-02-25
I tried.  A window came up that asked me to choose the desired resolution and when I did the terminal appeared at the bottom with the message:
"xserver-xorg postinst-warning; overwriting possibly-customised configuration  file; backup in /etc/X11/xorg.conf.2007022000710"

---

### Post by SteelCore on 2007-02-25
> **randiroo76073 said:**
> If you have one, use an ubuntu live cd, that way it's easier for someone here to guide/help you.  Try this command, it helped me:

sudo dpkg-reconfigure -phigh xserver-xorg

I tried.  A window came up that asked me to choose the desired resolution and when I did the terminal appeared at the bottom with the message:
"xserver-xorg postinst-warning; overwriting possibly-customised configuration  file; backup in /etc/X11/xorg.conf.2007022000710"

---

### Post by SteelCore on 2007-02-25
> **tyler_roach said:**
> When you do:
sudo apt-get install nvidia-glx
The computer senses that you already have it installed (even though it's compiled for the previous kernel), so it doesn't do anything at all.

To reinstall the drivers, try:
sudo apt-get install --reinstall nividia-glx

Or you could always fall back on the vesa drivers.

Yes, that did work.  I have my desktop back now.  Thank you very much.

---

### Post by randiroo76073 on 2007-02-25
> **SteelCore said:**
> I tried.  A window came up that asked me to choose the desired resolution and when I did the terminal appeared at the bottom with the message:
"xserver-xorg postinst-warning; overwriting possibly-customised configuration  file; backup in /etc/X11/xorg.conf.2007022000710"

Thats as it should be, before reconfiguring your xorg.conf it makes a backup to fall back to if needed, you would use following command to revert to backup:
sudo cp/etc/X11/xorg.conf_backup_[given number]/etc/X11/xorg.conf

Once you get your xorg.conf where you want it, make a copy & name it 1xorg.conf.bak, then whenever you can't boot because of X failure you can flip to backup file and reboot with known good xorg.conf :)

---

