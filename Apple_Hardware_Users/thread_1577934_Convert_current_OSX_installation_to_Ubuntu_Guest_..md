---
title: "Convert current OSX installation to Ubuntu Guest ."
date: 2010-09-19
forum: Apple Hardware Users
---

### Post by Raditude on 2010-09-19
Hey all. I'm about to change colleges soon, and my new college (Full Sail University) requires us to have MacBooks. The university distributes the MacBooks to us with loads of class-related software pre-loaded. I'm unsure if they give us recovery discs for the Mac installation and the software.

I have used Macs before, but I'm not all that Savy with them. What I need is a walkthrough on how to do certain things:


[LIST]
[*]I want to backup the hard drive of the Mac, including the OS, and all the included programs.
[*]I want to wipe the hard drive, and install Ubuntu as a single OS.
[*]I want to take the backed up OSX and run that in VirtualBox, with full functionality: (internet, video making, graphic work, multimedia, etc)
[/LIST]
After that, I want to install Windows 7 as another guest OS, but I think I can handle that.

---

### Post by conundrumx on 2010-09-20
Virtualizing OSX is a mixed bag, and the performance and stability are almost always lacking.  You would have a much easier time running Ubuntu as a guest OS.  That being said, you can use almost any CLI utility from Ubuntu in OSX, and many GUI utilities have equivalent alternatives.  OSX also has it's own X server.

If there is Mac software you'll be relying on at your new school I would highly recommend against virtualizing OSX.

---

### Post by Raditude on 2010-09-20
The reason I want to virtualize is so I can switch between Mac, and Windows using the Compiz Desktop Cube. I haven't found an alternative for Compiz in other OS's. I don't wanna have to restart just to change OS's.

---

### Post by conundrumx on 2010-09-21
> **Raditude said:**
> The reason I want to virtualize is so I can switch between Mac, and Windows using the Compiz Desktop Cube. I haven't found an alternative for Compiz in other OS's. I don't wanna have to restart just to change OS's.

There's virtualization software for OSX the same as any other.  As far as the Compiz cube, that's a very shiny way of doing virtual desktops, a feature which is built into OSX under the name "Spaces."  If virtual desktops are the killer feature keeping you attached to Ubuntu I'd suggest give Spaces a shot.

---

