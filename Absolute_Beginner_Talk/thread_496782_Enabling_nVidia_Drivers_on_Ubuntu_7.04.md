---
title: "Enabling nVidia Drivers on Ubuntu 7.04"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Kralnor on 2007-07-09
Howdy!

I just installed my first distribution ever but I can't for the life of me seem to get the nVidia drivers enabled.

When I go to *System > Administration > Restricted Drivers Manager* it says "Not in use" under Status. Checking the Enabled box doesn't seem to do anything.

I have also tried following the tutorial **[here](http://doc.gwos.org/index.php/Latest_nvidia_feisty)** but at step 5 it doesn't recognize the "nvidia-xconfig" command.

Cheers in advance for any help

---

### Post by MementoMori on 2007-07-09
Hey there,

I just recently installed some drivers myself. A moderator gave me a bit of a walkthrough, but I found another on the Linux discussion page at nvidia.com. When I find a link I'll edit, but for now, have a look here,

[http://ubuntuforums.org/showthread.php?t=495464](http://ubuntuforums.org/showthread.php?t=495464)

See if this helps.

Edit: Here's the thread at NVNews.

[http://www.nvnews.net/vbulletin/showthread.php?t=94072](http://www.nvnews.net/vbulletin/showthread.php?t=94072)

---

### Post by steve.horsley on 2007-07-09
The command:
**sudo aptitude install nvidia-glx-new**
should do the trick.
You may then need to edit /etc/X11/xorg.conf using this command:
**sudo nano /etc/X11/xorg.conf**
, find the line:
     Driver   "nv"
and change it to
    Driver   "nvidia"
Then log out and back in again.

---

### Post by Kralnor on 2007-07-09
Cheers

Following the latter link seemed to work until I reached the actual installation. I got this error message - "You do not appear to have libc header files installed in your system. Please install distribution's libc development package".

I tried using ```
sudo apt-get install build-essential
``` but that just returns an error about the package build-essential not being available.

> **steve.horsley said:**
> The command:
**sudo aptitude install nvidia-glx-new**
should do the trick.
You may then need to edit /etc/X11/xorg.conf using this command:
**sudo nano /etc/X11/xorg.conf**
, find the line:
     Driver   "nv"
and change it to
    Driver   "nvidia"
Then log out and back in again.

**sudo aptitude install nvidia-glx-new** did not report any changes being made

Editing the line in xorg.conf caused Gnome to be unable to start because no screen device was found. I had to revert the edit to go back to how it was before.

I seemed to be able to grab the latest build-essential package by using these commands
[b]sudo aptitude update
sudo aptitude install build-essential[/b]

Let's hope I can install the nVidia driver now ;)

**Update**: Installing the build-essential package seemed to do the trick! I was successfully able to install the latest driver as well as enable the driver. I ran into a small problem of the vertial refresh rate being set to 50Hz but was able to fix it by running the nvidia utility GUI - unfortunately I forgot the command, will make another update if it pops into my memory just for completeness sake.

While Ubuntu certainly is a bit trickier to update drivers on than WinXP it certainly feels a lot more solid. I love how packages are easily downloaded and updated ;)

---

