---
title: "broke my system - reinstalled now xorg trouble"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by captlogic on 2007-07-28
Ok, so I broke my system, again. To make a long story short I tried to install OSS and broke my sound.  So I tried to fix it.  This is when things starting going from bad to much much worse.  By the time I was done I couldn't get the broken OSS install to work, no sound-nothing.  Since I have a separate /home partition and I've installed a megazillion programs, not all of which I use, I thought I would just reinstall.  So I did, reformatted / and left /home unformatted,

When I rebooted after the reinstall everything seemed fine until I went to install the nvidia drivers, I tried to install the (wrong version, new-nvidia-glx?) driver via synaptic.  I tried to fix that and I thought I did and then got the correct version of the nvidia-glx driver.  I then reconfigured xorg.conf for my widescreen and rebooted again.

Now I get a very ugly error message at startup and I'm dumped back to tty1.  I'm still very wet behind the ears so to speak and don't really understand the error.  Something to the effect that the nvidia driver files are version x and the (some other kind of nvidia driver file?) are version y.  The x and y refer to the versions mentioned above.

I'm running from the live cd and just want a fresh install including a COMPLETE reset of all system settings.  So I think to myself, boot from the live CD, delete all of the hidden files in my home directory, none of my user data there right?  Then my /home folder does not have any configuration files, just some papers and some pictures.  Alas I cannot delelete any hidden folders from the gui of the live cd, wrong permissions.

How do I do a complete reinstall, leaving just my user folders, about a dozen, in my home folder?

Thanks for reading my novella of a post.

---

### Post by Jeek Elemental on 2007-07-28
for nvidia drivers I recommend using Envy, get it here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

it has some dependencies, however if you follow the step-by-step on the page, it works great.

I would make a backup of /home and let the installer wipe the drive, you should be able to delete any files you want as root tho?

---

### Post by captlogic on 2007-07-28
I just keep trudging along.

So, I reinstalled again.  Everything's working just fine.  Widescreen OK, Sound (5.1 via ALSA) fine.

Great, too bad I couldn't have left well enough alone.  Instead I tried to install OpenSound oss v4.

It installed just fine this time, no problems using the install instructions included.  Reboot and now I get buzzing sound.  So I uninstalled OSS v4 and went back to ALSA, but the buzzing will not go away.

I'm using an creative audigy (1st gen) with creative 5.1 speakers.  When I first installed ubuntu I need to uncheck the 'output in digital' option, but now I can't find that option.  I thought it was on the volume control panel, but now I can't find that option.  Am I completely losing my mind?

Any suggestions?

---

### Post by Jeek Elemental on 2007-07-29
there seems to be an issue where digital output is enabled by default, have a look at this:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/94189](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/94189)

if you dont get the control in the volume panel, maybe theres an option in /home/user/.asoundrc.asoundconf?

also for oss you can use the aoss wrapper, lets you run oss programs with alsa. :guitar:

---

