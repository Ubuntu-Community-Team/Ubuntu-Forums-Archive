---
title: "VMWare VIDEOCARD help"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by Woutervdkrol on 2007-05-10
Hey all!

w00t first time for me entering the "Ubuntu-community" :)

Anywayz, I'm running Ubuntu (Ultimate Edition) under VMWare, so actually running in Windows. I normally have a ATI Radeon X1300 videocard, but VMWare seems to be emulating a own videocard, not capable of really smooth dragging with windows, let alone using Beryl (which was the main reason I installed Ubuntu).

So, does anyone have any idea on how to either: 

* run my "native" videocard directly in VMWare
* make the VMWare's virtual videocard faster + capable of running effects

Thnx alot in advance, looking forward to some answers :)

Rock on, 

Wouter van der Krol

:guitar:

---

### Post by jkeyes0 on 2007-05-10
Woutervdkrol,

Welcome to the ubuntu community!

Sad to say, VMware does not natively support 3d acceleration (what I believe you're asking about). 
There are some experimental ways to get it to work, but personally, I haven't had any luck getting the VMware driver to do any 3d effects. The 3d acceleration is only supposed to work under VMware player and VMware workstation, so if you're using VMware server, it definitely won't work. That being said, if you're using the player and want to try out the 3d acceleration, this page might help:

[http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html](http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html)

If you'd truly like to test out how Ubuntu will run on your system (with full 3d acceleration) the best way to try is to actually install it, even if it's just a dual-boot situation.

EDIT: Nevermind the VMware link above... I just read through it again, and it says it only supports Windows 2000 or XP. It might work, but it's even more likely not to, if the guest OS (Ubuntu) isn't Windows..

---

### Post by Woutervdkrol on 2007-05-10
Hehe feels like home here, thnx for welcoming me.

And thnx for helping, or at least give me the info. And the dual-boot situation is a bit too risky for me. About 3 weeks ago I tried to dual-boot my Win Xp system, ending up with a Ubuntu which didn't recognize any of my wireless network adapters (meaning no internet for me :D) and a removed partition on which Win was installed, and all my personal stuff.. All gone :P

I don't dare to set up a dual booting system anymore ..

Thnx anyways!

---

### Post by docsmooth on 2007-05-10
The key to dual-booting windows and Ubuntu (how I work) is to, at the very start of your PC's life, make sure your windows partition doesn't eat up the entire disk. :)  There are some pieces of software (Norton Ghost for around $100 is one of the easiest to use) that will seamlessly resize a Windows partition down, giving you some free space for Ubuntu.  I have a 100GB drive that's split 30GB for Windows, 70GB for Ubuntu.

For your VMWare question, there are a few things that you may want to try:

1) defrag your windows drive.  If possible, copy the VMWare disks off to removeable media, then defrag the drive, then re-copy the VMWare disks back to your PC.  Then run the VMWare "defrag disk" function in the VM properties.

2) Run the Ubuntu system at full screen.

3) Disable real-time virus scanning for ".vmdk" file types, or for the entire VMWare directory.

4) double the amount of RAM you give to your VMWare systems. If VMware suggests 256MB RAM, give the VM 512.  This will take advantage of the Linux file cache to reduce disk IO.

Also, VMWare Workstation 6 just came out, and has better 3d support - take a look at that, if you're still running 5.5.  You can set the "3d.enabled=true" in the .vmx file by hand, and see how it passes through to the Ubuntu system.

You may not get beryl running as smoothly as you want, but that should help make the system quite usable.

Doc SmooTH - Ubuntu for 6 months, Windows for years.

---

