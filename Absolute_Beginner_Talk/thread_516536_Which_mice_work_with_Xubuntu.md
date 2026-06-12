---
title: "Which mice work with Xubuntu?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by gerry1936 on 2007-08-03
Having started a thread about my mouse not working with Xubuntu, and then finding that there was another, I got thinking.

I have available:

PCline PCL-WS01 and
A4Tech SWOP-35

These both work with Windows, and with Damn Small Linux, and Puppy Linux. They don't work with Xubuntu 7.04 or Gentoo 2007.

I found out that the latest Kernel dropped support for some old hardware. DSL and Puppy both use an old Kernel, to save space. So my problem MAY be a Kernel problem, rather than Xubuntu. 

So... is anyone out there using either of the above mice with Xubuntu?
And...please look at the label under the mouse that you are using, and post the model details here, so that I can go and buy one to try.

(Only wired mice, please.)

Gerry

---

### Post by gerry1936 on 2007-08-03
Forgot- I'm using PS2 connection.

---

### Post by Fraoch on 2007-08-06
Bizarre, I'm having the same problem too.  Both a generic trackball mouse and a Microsoft optical Intellimouse.  Both PS/2.

I'm just trying to install and I can get to the desktop but I can't do anything from there because I can't move the pointer.  I thought it was a BIOS thing, but there was an old install of Win98SE on the hard drive that I'm trying to overwrite - both mice work fine there.

---

### Post by ugm6hr on 2007-08-07
Is this a problem with both AlternateCD & LiveCD installs?  Just wondering.  The AlternateCD seems to cause one other problem that doesn't exist with LiveCD.... bizarre.

Perhaps it's got something to do with how xorg.conf is configured?  Worth posting your xorg for perople to see.

Just seen this: [https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221](https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221)
Looks like it's a bug in Fesity - it's been fixed (apparently) - but you need to update.

If you can't get to the menu to update - use the Ctrl+Esc keyboard shortcut to get to Applications menu->System->Update-Manager
Use the Tab / Enter keys to "Check" then "Install" updates.
Hopefully that should fix it....

---

### Post by Fraoch on 2007-08-07
I haven't tried to install using the alternate CD.  I may have to do that because I can't install via the normal CD unless there's a keyboard shortcut to get to the "install" icon.

Doing some searching and looking at the bug you posted I see this is a known issue.  Some of my searches have shown how to reconfigure xorg.conf, I'll give that a shot.

Thanks.

---

### Post by ugm6hr on 2007-08-07
> **Fraoch said:**
> I haven't tried to install using the alternate CD.  I may have to do that because I can't install via the normal CD unless there's a keyboard shortcut to get to the "install" icon.

Doing some searching and looking at the bug you posted I see this is a known issue.  Some of my searches have shown how to reconfigure xorg.conf, I'll give that a shot.

Thanks.

I thin you *might * be able to install from LiveCD - try this:
[http://ubuntuforums.org/showpost.php?p=3146498&postcount=7](http://ubuntuforums.org/showpost.php?p=3146498&postcount=7)

---

### Post by Fraoch on 2007-08-07
Thanks, ugm6hr!  I'll let you know how it goes.

---

### Post by Fraoch on 2007-08-07
No luck so far.  I tried a USB mouse which worked right away, then I went through the install script which left the old Windows install, forgot to install GRUB and left my system unbootable.

I'll try the alternate CD.  I was hoping not to waste a CD (Mr. Cheap here).

Also, reconfiguring xorg as described here [http://ubuntuforums.org/showthread.php?t=514978](http://ubuntuforums.org/showthread.php?t=514978) didn't work with the LiveCD, xdm couldn't be restarted.

---

### Post by ugm6hr on 2007-08-07
> **Fraoch said:**
> then I went through the install script which left the old Windows install, forgot to install GRUB and left my system unbootable.


Are you sure you told Grub where to install (generally hd0, but may not be on your system)?  And is the CD OK?  

I certainly had no problems with the LiveCD - and not installing Grub would not leave the system unbootable - it would leave it auto-booting to Windows.  The auto-Grub configuration thing sometimes gets the wrong location for the OS entries - I updated my kernel to find that the Grub menu appeared, but none of the options worked except Windows, since it thought all the kernel images were in hd0,6 instead of hd0,5.

If all of this means nothing to you - just tell us what happens (exactly) when you reboot with no CD in the drive.

---

### Post by Fraoch on 2007-08-07
> **ugm6hr said:**
> Are you sure you told Grub where to install (generally hd0, but may not be on your system)?

It never asked me.


> And is the CD OK?

Yes, I checked it on two systems.  

> I certainly had no problems with the LiveCD - and not installing Grub would not leave the system unbootable - it would leave it auto-booting to Windows.  The auto-Grub configuration thing sometimes gets the wrong location for the OS entries - I updated my kernel to find that the Grub menu appeared, but none of the options worked except Windows, since it thought all the kernel images were in hd0,6 instead of hd0,5.

If all of this means nothing to you - just tell us what happens (exactly) when you reboot with no CD in the drive.

I'm redoing the install using the alternate CD but even then I had to resort to manual partitioning.  The guided install was doing weird things - installing the entire HDD as /media?

I've installed Ubuntu on 2 PCs, this is my first Xubuntu install.  I've forgotten how to partition but I guessed at the following:

- swap, 2 X 192 MB (the RAM in this old machine) = 384 MB

- /boot as ext3, about 500 MB

- / , 10 GB

- /home, the remaining space (about 10 GB, this is a 20 GB drive)

Hope this works.  I'll reboot, get updates then install the PS/2 mouse.  Whew!

---

### Post by Fraoch on 2007-08-07
Well, I'm up and running (more like up and crawling).

Anyway using a USB mouse, installing a working system, installing all updates then installing the PS/2 mouse did the trick.

As for performance, I think I flew too close to the sun on this one.  I had heard that Xubuntu was suitable for older hardware, but I think this one is too old.  AMD K-6/2 400 MHz, 192 MB RAM.  The CPU is pegged at 100% most of the time, and when it isn't, even moving the mouse causes it to spike up to 25%.  Maybe I'll try DSL on this.

---

### Post by ugm6hr on 2007-08-07
> **Fraoch said:**
> As for performance, I think I flew too close to the sun on this one.  I had heard that Xubuntu was suitable for older hardware, but I think this one is too old.  AMD K-6/2 400 MHz, 192 MB RAM.  The CPU is pegged at 100% most of the time, and when it isn't, even moving the mouse causes it to spike up to 25%.  Maybe I'll try DSL on this.

Before you wipe the HD - might be worth trying an alternative Window Manager first:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

You should be able to install e.g. *icewm* and *menu* from Xubuntu, and then just restart and choose IceWM in Sessions from GDM login.

Then keep your fingers crossed.....

---

### Post by Fraoch on 2007-08-07
You know, now that I'm playing with it, it's not so bad!  My main system is a Core 2 Duo E6600 with 2 GB of RAM, so obviously it's going to feel a little slow.

I think I'll stick with it!

Thanks for all the help ugm6hr!

---

