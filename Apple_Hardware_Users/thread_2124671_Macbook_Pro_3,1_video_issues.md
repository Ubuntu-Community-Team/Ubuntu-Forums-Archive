---
title: "Macbook Pro 3,1 video issues"
date: 2013-03-11
forum: Apple Hardware Users
---

### Post by keeledover on 2013-03-11
No video that's the issue.  I've rewritten this post so many times now as I try to get from one problem to another.  Now it's been the graphics one but I've been diligently trying to no avail.  Maybe it's not possible ?  It seems to be the only Mac that has absolutely no info on the mac pages on the Ubuntu website (well maybe some mac mini but close enough to only model)
I'm not sure where to start from 
quick synapse(please avoid this section and skip to the "Problem at hand" section if possible; badly written and not sure of much use; will try to fix in the future):
Friend's Mac.  He couldn't get past a black screen when booting the CD (external drive; he says internal one only accepts original copies ?)
He partitioned it no clue with what probably disk utilities (the graphics version unless he followed a guide can't be bootcamp as he doesn't have a Windows disc)
He installed rEFIt
-------My part in this--------
12.10x64 (12.04.2x64+mac/12.04.2x64alternative/mini.iso x64 weren't even recognized when holding alt at boot) USB following the instructions on Ubuntu's website.
Got to grub prompt try/install didn't work.  Tried "nomodeset". "Try Ubuntu" let me switch to a terminal. Which I used to erase the partition created and make an ext4 partition.  "Install" worked with nomodeset and everything seemed to work even Wi-Fi.  Ubiquity (the installer ?) Worked fine asked if to install alongside Mac or what.  I followed the general guide advanced ext4/format/root partition/bootloader to same partition.  Waited for it to install it did so successfully.
Rebooted don't know if there was anything wrong with bootloader I sort of got ahead of myself but I "fixed" it according to someone's post on here. (Need to find that link later not sure if it matters as when I rebooted it went to grub and it didn't boot)
After that selected the EFIx64...grub option.  Grub comes up try to boot Ubuntu nothing happens.  "nomodeset" allows me to switch to terminal.  Read some post on the net about using envy..something or other first update then install.  Updated but couldn't find the package not sure what the name of it should be "apt-cache search envy" turns up nothing. More reading tried jockey but didn't know what file I needed tried installing nvidia_current via apt-get still not working.  Found out what I need for jockey-text uninstalled then checked "jockey-text -l" got my list tried nvidia_current didn't work (can't remember errors anymore I have all the logfiles if needed). Read some more online about needing "linux-headers-$(uname -r)"  and "dpkg-reconfigure nvidia-current" "nvidia-xconfig" nothing still.  Kept checking with that and jockey-text -e kmod:nvidia-current still nothing.  

Problem at hand:
Trying to run Ubuntu (after selecting in grub) brings a black screen with a blinking cursor.
Eventually, "jockey-text -l" said that nvidia_current was Proprietary, Enabled [finally!], not in use[damn it!]
And that is what I'm hoping if I can figure out will solve it.  But when I type that into google I get PC results only and the one or two threads with actual info and solutions to it are either things I've already tried or depreciated workarounds like installing nvidia-current-modaliases which Ubuntu seems to indicate is already in nvidia_current.

If anyone would be able to help me I would greatly appreciate it!  I'm sure I'll be needing some logs.  Whatever you need I got.  And will upload what is needed.  Say if the whole thing or just the latest parts.
Oh right I can get to a terminal if I replace "quiet splash" with "text". Advanced options/Ubuntu Recovery seems to work completely fine if I need to do something in there.
Nvidia GeForce 8600 GT
I'm sorry I've been trying for days on end and I'm sure I missed something.  Whatever it was be sure to let me know and I'll be sure to bring up the info as soon as I can.  Thanks for any help that can be provided I really appreciate it.

---

### Post by pirulo on 2013-03-18
I'm not sure to understand the problem. But here is my (partial) solution to the graphic card problem that I had on my Macbook pro 3,1 with Ubuntu 12.10.

I mainly followed [that guide]("http://www.rodsbooks.com/ubuntu-efi/"). Instead of using Ubuntu 12.04, I used the [12.10 Desktop Mac version]("http://releases.ubuntu.com/quantal/"). But I still cannot boot directly from the rEFInd menu: the X window cannot start correctly (it does not find the card, even with the "modeset" param passed to the kernel). I have to go through the Super Grub 2 CD, using the procedure indicated in the guide, and then everything runs fine. 

What I did after the installation and the update, it was to download and install the [NVidia driver]("http://www.nvidia.co.uk/object/linux-display-amd64-310.40-driver-uk.html"). Don't forget to install the linux headers before installing the NVidia driver:

[FONT=Fixedsys]sudo apt-get install linux-headers-`uname -r`[/FONT]

The difference I've noticed between the 2 ways to boot is that when starting on the Super Grub 2 CD, the card is not set in the same mode as when it starts directly from the rEFInd menu: the graphic modes are evidently different. I do not have a solution for that: it seems that it has to do something with how grub is configured, ie. before it gets in the menu.

I hope that helps.

---

