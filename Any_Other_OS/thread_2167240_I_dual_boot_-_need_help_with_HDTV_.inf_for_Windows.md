---
title: "I dual boot - need help with HDTV .inf for Windows XP side"
date: 2013-08-12
forum: Any Other OS
---

### Post by squakie on 2013-08-12
I'm running Ubuntu 13.04 and Windows XP in a dual-boot.  I no longer have a monitor and just use my small HDTV via one of the HDMI inputs.  All was fine when I was just Ubuntu, but I had to re-partition and then install Windows XP and then 13.04 over again, as I need native Windows XP in order to run my VHS to disk cheap hardware adapter (won't run with XP in virtual box even with all USB installed).  So, it still works fine for Ubuntu 13.04, but on the Windows XP side I think I need a .inf file of some sort to truely support my HDTV.  Currently in XP the desktop is fine but when I open applications, even non-maximized windowed applications) the resulting window display is too large for the screen and I can't move them or use the window/maximize button or via the system line.  So, it's making things a little awkward.  

Any ideas would be appreciated.  Keep in mind I've got 3 different USB VHS to disk adapters and none of them will work in Linux.  I can't afford buying any more of them just to see if they will work in Linux, and there are a limited (well, relatively speaking) number of tapes I need to load in, so using Windows is okay for that.  I can't use Handbrake to shrink the converted files from mp2 to m4v as the Handbrake window is one of those way too large ones.  So, I have to load them in Windows, then reboot to get to Ubuntu so I am able to run Handbrake on the files.

If I could just get through it all on Windows then I could do it faster and I'd be done with Windows again faster.  Wanted to get 1 of them working in Linux to avoid Windows but no such luck.  An EasyCAP but not the chipset to use in Linux; a Roxio VHS to DVD device - recognized in Linux but can't capture video or audio correctly even after trying several suggestions from the net; and finally a Pinnacle DVC-100 - I had seen a you-tube video showing it working in Linux, but I can't get the thing to work at all in Linux.  If someone has some straight-forward way to get one of those working natively in Linux I could get rid of Windows all together again.

Either way, any help is greatly appreciated!

---

### Post by westie457 on 2013-08-13
A couple of ideas for you to consider.

If the tv has a pc-monitor input use a monitor cable.

Update the drivers for your graphics card (Nvidia or ATI)

Set the display resolution of the computer to match the native resolution of the tv.

The first one is an option and should work regardless, the others are necessary whatever you try.

Also you must update XP to SP3 for the updated graphics drivers to work.


No guarantee that this will work.

---

### Post by squakie on 2013-08-13
Thanks westie457 - you given me some things to think about and try.  I am already at SP3 for XP, so I know at least for XP and the TV it's the old .inf file information that's missing (forgot about manually specifying them like you suggest).  I suspect that XP isn't querying the TV correctly or the TV isn't replying correctly (heck, even in Ubuntu it thinks it's a different brand and size - it's a cheap TV! ;) ).

I'd like to try just using a vga cable, as my TV does have that for input, but I'd need to pick one up first so being lazy I thought I'd try the other things first ;)

Thanks again! ;)

---

