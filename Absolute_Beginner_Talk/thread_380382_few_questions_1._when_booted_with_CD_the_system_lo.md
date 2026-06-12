---
title: "few questions: 1. when booted with CD the system loaded but there wasn't installation"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by asdf2 on 2007-03-09
few questions:
1. when booted with CD the system loaded but there wasn't installation. how to install it? (i've already open suse but i want to delete it.

2. it's amd 64 bit with pci express graphic card. when the system loaded the loading graphics looked bad and had some king of jumps.

 i don't know if i will continue using these forums because for example the need to add tags by the poster.

---

### Post by i.am.canadian on 2007-03-09
Hi there.

1. Did you just boot the live cd, or did you boot to it and click the install icon on your desktop?  If you did install it, did you take the live cd out of the drive before your computer rebooted?  If not, you may have ended up just booting off the cd again.

2. I'm not entirely sure what to do about this.  If you let us know what type of card it is (nVidia or ATI for example) it might shed more light on your problem

Not to argue with you about your choice of forums, as it is just that, a personal choice, but I have found people to be quite helpful here if you are willing to stick with it and keep a positive attitude.

So that's my two cents...

---

### Post by 23meg on 2007-03-09
> 1. when booted with CD the system loaded but there wasn't installation. how to install it? (i've already open suse but i want to delete it.

You have to double click the "Install" icon on the desktop to start the installation.

> 2. it's amd 64 bit with pci express graphic card. when the system loaded the loading graphics looked bad and had some king of jumps.

What's the exact model of the video device? You can probably sort that problem out after installation; did you have it with other distros?

---

### Post by asdf2 on 2007-03-10
> **i.am.canadian said:**
> Hi there.

1. Did you just boot the live cd, or did you boot to it and click the install icon on your desktop?  If you did install it, did you take the live cd out of the drive before your computer rebooted?  If not, you may have ended up just booting off the cd again.

2. I'm not entirely sure what to do about this.  If you let us know what type of card it is (nVidia or ATI for example) it might shed more light on your problem

Not to argue with you about your choice of forums, as it is just that, a personal choice, but I have found people to be quite helpful here if you are willing to stick with it and keep a positive attitude.

So that's my two cents...

1 it wasnt installed. i don't understand. do i need to install it while loaded in windows? i've boot the cd and pressed enter.

2 graphic card is nvidia  WinFast PX6600.

---

### Post by asdf2 on 2007-03-10
> **23meg said:**
> You have to double click the "Install" icon on the desktop to start the installation.



What's the exact model of the video device? You can probably sort that problem out after installation; did you have it with other distros?

nvidia WinFast PX6600
it also happened in other distributions. in open suse i wasn't jumped  i recall right  but the loading graphics was freeze for moments.

---

### Post by igknighted on 2007-03-10
Once installed you need to install the nvidia graphics drivers.  This is done by searching in synaptic for the package "nvidia-glx" and installing it.  Then run the command "sudo nvidia-xconfig" in the terminal, reboot, and the jumpiness should be gone.

As for installing, once the live CD is fully booted, on the desktop should be an icon that say "install".  Click that to run the installer.  As an alternative, running the command "ubiquity" or "sudo ubiquity" from the terminal will also start the installer.

About the forums, I am sorry you don't like the default layout, but if you stick around I promise this is the absolute best linux community in the world.

---

### Post by asdf2 on 2007-03-10
thanks,

but it can't be installed without loading that live CD the isn't required to install?
maybe it will be faster to install just by booting into installation wizard.

---

### Post by i.am.canadian on 2007-03-12
Hi there.  To install from a live cd you will need to make sure that your BIOS is set to boot from your CD drive.  Depending on the make of your computer you will need to hold down a certain key at boot up, which I would be unable to tell you, but you could probably find from a google search or watching the boot screen for a message.

Once this is done, insert the disk and wait for it to ask you to hit enter or something to boot from the cd.  Then wait for it to load, it may take a while.

Once it is loaded, there will be only one icon on the desktop and doubling clicking this will begin the install process.

I hope that is a little clearer.

---

