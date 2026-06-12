---
title: "Audio/Sound on Toshiba Satellite P105"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Pesty on 2007-11-03
I'm in the process of converting my Vista laptop into a dual operating system, So far the only thing stopping me from fully using ubuntu is a lack of audio.

I've spent most of this week creatively Googling, searching threads here, and pestering my friends who already have linux to the point where they (almost) don't want to talk to me about it. I haven't had any other problems with it so far.

I know it's not a BIOS setting, or Vista is still overriding something. I've tried to completely uninstall Alsa and re-install it, but so far to no avail. 

"aplay -l" gives me the following information.

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any suggestions for me? like I said, I've been looking through any threads I can find on the subject but so far none have worked for me. I haven't done any that requires compiling or creating any extra files, because I get to that point, and I can never turn the newly created code file into something ubuntu will read and follow the instructions. I'm good at following terminal commands, and I'm starting to understand the way commands work a little better, but I've still got a ways to go before I fully understand Linux.

Any help would be greatly appreciated.

---

### Post by tubasoldier on 2007-11-03
I'm having the same issue with Gutsy 7.10.

If you want sound to work you will have to recompile your kernel. It seems this is an issue with that particular  sound chip. Dont ask me why but somehow Ubuntu developers dont seem to get it right about every other kernel.

---

### Post by ubukool on 2007-11-03
Hi there,

There is a problem with sound for those who have intel hda soundcards on Gutsy 7.10.  I too have had a frustrating time googling and checking out different solutions.  Basically, this worked fine out of the box in Feisty, so I'm wondering why it doesn't work now?  This is the kind of crippling problem that will stop Ubuntu seriously challenging Windows, imo, but hats off to the developers who have given us a wonderful OS, in every other way superior to Windows.

This might help:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

I've tried methods A and B, but it's still not working correctly.  Some applications work, some don't.  Skype doesn't work and neither does sound on Virtualbox.  Some media players work, some don't.

There's no rhyme or reason to it.

Good luck! :)

---

### Post by Pesty on 2007-11-03
Thanks for the link, I've gone through and followed A, and B, but to no avail. I'm trying method C, but as soon as I try to sudo apt-get install alsa-source, the terminal turns into a Blue EULA agreement for sun-java6-bin It has an <Ok> at the bottom of the terminal window, The terminal doesn't respond to any keystrokes other than up or down arrow keys, or the pageup/pagedown keys.  

I'm wondering if I should just try a new install of 7.10 and start with method C. I've avoided saving anything locally on the hard drive to this point, so I wouldn't loose anything.

---

### Post by mikonen on 2007-11-03
I'm having the same issue with my boyfriends computer, it's a toshiba satlllte p105 with the same specs as Pesty, so we can probably figure this out with a bit of patience.  :popcorn:

 If it is any help the bug fix:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

is not specific to this chipset.  The bug is for a buggy PCI of 8086:284b, whereas on the Toshiba Intel audio card it is 8086:27d8, so I am almost positive that it isn't referring to our sound issue.

There was a fix that worked back with Feisty but I can't find it now.  It had to do with adding a single line to /etc/modprobe.d/alsa-base but every thread that I have found today on the Ubuntu forums that mention this do not work, so maybe it is the bug?

Thinking out loud...

---

### Post by mikonen on 2007-11-03
Just so the thread readers know, there is a bug report for this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

Looks like its all kernel/acpi for toshiba sound issues, not drivers.

---

