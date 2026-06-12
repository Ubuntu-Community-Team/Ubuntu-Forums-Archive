---
title: "Time for Linux to start falling apart, as usual"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by Mramius on 2007-12-19
Well, I was cruising along perfectly...not installing tons of packages...just browsing the web and reading news etc.

The update notification comes up to tell me there were available updates, I updated, rebooted and VIOLA!

First, X wouldn't start so I had to revert xorg.conf to some default backup.  And none of my ccsm rules are working anymore.  Even though they're right there, all written up and waiting.  I guess it's just deciding to ignore them.

This is what happens to Linux.  It just starts to decide that it's done running smoothly and begins to fall apart on itself.

---

### Post by new2*buntu on 2007-12-19
You could just not update then...

---

### Post by Whiffle on 2007-12-19
Thats why I don't do ubuntu updates anymore.  I update in slackware, but I check what I'm updating first, and never have that issue.  Ubuntu really needs to come up with a system of notifying the user that the updates they're about to download could possibly mess things up, its happened to me a few too many times.

---

### Post by Tristicus on 2007-12-19
Did you restart during updates? 

sudo get update

Just to make sure.

---

### Post by Mramius on 2007-12-19
I restarted after updates.

What does sudo apt-get update do?

---

### Post by Whiffle on 2007-12-19
It updates the list of available packages (same thing as hitting reload in synaptic)

---

### Post by Mramius on 2007-12-19
I'm not sure what updating the list of packages has to to with X being unable to restart and my video card being suddenly disabled.

---

### Post by Whiffle on 2007-12-19
It has nothing to do with that :)

---

### Post by Joeb454 on 2007-12-19
It wasn't a kernel update by any chance was it? Because they're the most likely to screw the system over.

And it doesn't take that long to reinstall if it's that big a problem...just customising it takes the time

---

### Post by Mramius on 2007-12-19
If I enable my NVidia driver in System>Admininstration it tells me to restart.

I restart and X won't start...blah blah blah about my video card module.

Restore a backup of my xorg.conf file and startx...and can't use any desktop effects.

---

### Post by Dr Small on 2007-12-19
I never accept updates, mainly for that reason. Maybe it's just me, but I don't need things to be updated when they work perfectly fine :|

Dr Small

---

### Post by Mramius on 2007-12-19
Is there a way to see which packages were just installed?

---

### Post by Clickbg on 2007-12-19
sudo apt-get update
sudo apt-get upgrade

That will re-upgrade your system if somehow updating was not finished last time. It is possible some update to be broken from the ubuntu releaser but chance that to happen is very low. I have updated early today and all is cool :)

---

### Post by eolson on 2007-12-19
Yup,  I did three different machines.  Two desktops and a laptop and all are good.

A bad update can happen with any O/S.  Have had Windows updates trash my machines more than once also.  Just one of those things.  Updating is not necessary if your happy with your system as is.  I just do it because ....

---

### Post by Saint Angeles on 2007-12-19
you need to READ the updates before installing them.

you installed a new kernel. this is the only thing that requires a restart in linux... (for most other stuff, a restart of X is only needed occasionally)

basically you just swapped out the heart of your computer for a new one. you had your old one just the way you wanted it but ubuntu gave you a heart transplant and you havent configured this new one.

---

### Post by Clickbg on 2007-12-19
p.s. To see installed packages 

sudo dpkg -l

To reinstall package:

sudo apt-get --reinstall install packagename

---

### Post by Mramius on 2007-12-19
Heh, I did read them.  But they're all so cryptic.

lib5h
(This package is needed by bindrv8lib)

bindrv8lib
(This package is needed by trubinlib)

trubinlib
(You don't need this package)

libc.ed
(A package)

drvrlib4
(We're not really even sure, but we bet you have a dependency for it)

binlibbinlib
(Update to Firefox)

---

### Post by Mramius on 2007-12-19
Oh, and lest I forget...

NVidia3dUpdate
(This will undo every single thing you've done to the computer since you installed the operating system.  It's real name is 'Destrucolib' but we realized no one would install it if it was called that)

---

### Post by spiderbatdad on 2007-12-19
> **Mramius said:**
> Oh, and lest I forget...

NVidia3dUpdate
(This will undo every single thing you've done to the computer since you installed the operating system.  It's real name is 'Destrucolib' but we realized no one would install it if it was called that)

:lolflag:

---

### Post by asmoore82 on 2007-12-19
Have you used Automatix2 or Envy?

---

### Post by A$h X on 2007-12-19
> **Mramius said:**
> Heh, I did read them.  But they're all so cryptic.

lib5h
(This package is needed by bindrv8lib)

bindrv8lib
(This package is needed by trubinlib)

trubinlib
(You don't need this package)

libc.ed
(A package)

drvrlib4
(We're not really even sure, but we bet you have a dependency for it)

binlibbinlib
(Update to Firefox)
I would download all of them on principle.

---

### Post by dpar on 2007-12-19
Try starting Ubuntu using the old kernel. If it works, just make that one the default.

---

### Post by crjackson on 2007-12-19
I got the updates this morning and here's what happend in my case.  The kernel updateed but the restricted modules weren't ready or something and didn't update.  My nVidia card restricted driver didn't work anymore because it wasn't matched to the kernel, so I had no desktop effects.  A little while later (a few hours) I checked for new updates and my restricted modules were ready.  I updated, re-enabled the restricted driver, rebooted and everything was perfect.

Perhaps for one reason or another, your not loading all your modules as needed.

This used to happen to me when using an ATI card more often than I like to admit.  To fix it I would open up a terminal and...

```
sudo depmod -a
```

If this isn't your problem, then it won't hurt anything.  I forgot to mention I would have to reconfig. my monitor after words too...

---

### Post by corstar on 2007-12-19
dude, 
I know this is the ubuntu forums, but swtich to Debian.
I have not had an X crash since i installed over six months ago.

I have crashed a couple of apps but that's 'cos I'm running Lenny (unstable).

I couldn't take my X server crashing after an update...that's not cool.

---

### Post by P235 on 2007-12-19
It does look like there are updates for the header files related to the Linux kernel.  It may not be much consolation now, but I usually refrain from installing updates related to the kernel for a few weeks as I usually read of some thread describing new, unforeseen difficulties.  Why not reboot and use your old kernel?

---

### Post by GSF1200S on 2007-12-19
Id like to reassure you that Linux doesnt just fall apart- Ive had this install going since 7.10's release, and its run wonderfully. I never had any problems with Feisty. Edgy gave me issues, but the HAL was older, I was new, etc..

The Nvidia card issue is quite small. People need to stop thinking of the command line without X as a crash; its not a crash, its just a prompt for a few seconds of maintenance.

Either a new Nvidia version was released, a new set of restricted modules was released, a new xorg.conf was released, or well, thats it ;)

Make sure do to as synaptic says once the driver is installed:

To enable the driver, run "sudo nvidia-glx-config enable".

This will update the new xorg.conf after the driver is installed...

---

### Post by GSF1200S on 2007-12-19
Another thing to keep in mind is that ubuntu is pretty much "cutting edge," so the fact that some of you have had "crashes" is to be expected. Debian may be a better choice if youre after rock solid stability...

---

### Post by Whiffle on 2007-12-20
> **GSF1200S said:**
> Another thing to keep in mind is that ubuntu is pretty much "cutting edge," so the fact that some of you have had "crashes" is to be expected. Debian may be a better choice if youre after rock solid stability...


I'm trying to figure out what is more of a priority for ubuntu, stability, up-to-date/cutting edge software, or user friendliness.  The one in the middle doesn't play nicely with the other two.

On the updates end, according to this page:
[http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition)

> 
The task bar contains an update area where we'll notify you when there are updates available for your system, from simple security fixes to a complete version upgrade. The update facility enables you to keep your system up-to-date with just a few clicks of your mouse.

From the sounds of that, *you shouldn't need* to read through every update, i mean its user friendly and easy!  Somehow thats not quite reality though.

---

### Post by jrickard on 2007-12-20
There was a kernel update today.  You probably have an NVIDIA or ATI graphics driver.  This is a slightly painful anomaly right now in the way that proprietary graphics drivers have to be mated to the kernel.

A gentleman has done a great job of automating this with a Python script titled ENVY.  You must download this [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu2_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu2_all.deb)

It will open into your home directory.  From then on you simply run the script.  Open a terminal window, and enter envy.

When you update a kernel and reboot in the future, it will normally take you to a command line interface.  You can run the envy script and it will update your NVIDIA driver automatically.  Then reboot and you should be up and running.

Jack Rickard

---

### Post by Dapman01 on 2007-12-20
I used to have the same X-server problem with the restricted drivers.  I recommend going to google and downloading envy, it works better and I never had to mess with the x servers

---

### Post by Caffeine_Junky on 2007-12-20
This sounds like a "Kernel Update" issue to me!

Just boot from the previous one that was configured!,  ..unless you needed a Kernel Update?

It is quite simple, Look at the list of proposed updates before you apply them!, ...and if you want to update your Kernel because some new support for your hardware is available in the new one, you will have to install the** Graphic's Drivers **on the new one, because your **xorg.conf** file requires it.

Thus, your OS is **not** "falling apart" ..it was an error between your Keyboard and chair that caused the problem :)

---

### Post by aktiwers on 2007-12-20
There where some kernel updates today, and the same thing happened to me. All I had to do was to reinstall the nvidia drivers, but I had to do it from one of the Virtual terminals, which is not much fun... at least not for new users!

---

