---
title: "iMac G3 kernel panic at 9.04 boot"
date: 2009-06-18
forum: Apple Hardware Users
---

### Post by lx45803 on 2009-06-18
Okay, I have this iMac G3 I use as a server for my house, and for several months, it's had 8.04 server on it. I noticed that 9.04 was out and I decided that it was probably time to upgrade. I followed the directions for network upgrading, but was told that there was no new version available. Not one to be put off by a silly little error message, I proceded to download the alternative CD to use its built in upgrade system. Everything went fine through the upgrade process, and it looked like everything worked. Then I restarted.
```
[timestamp] aty128fb 0000:00:10.0: Invalid ROM contents
Loading, please wait...
```
It then promptly shut down. I tried a few more times with similar results. When that didn't work, I thought I'd try the old kernel at the yaboot prompt.
```
boot: old
Please wait, loading kernel...
/cpi@f2000000/mac-io@17/ata-4@1f000/disk@0:3,/boot/vmlinux.old: No such file or directory
boot:
```
Uh oh. Well, I thought I'd try to boot the current one again, just because it was that or give it away as a doorstop.
```
boot: /cpi@f2000000/mac-io@17/ata-4@1f000/disk@0:3,/boot/vmlinux
Please wait, loading kernel...
  Elf32 kernel loaded.
```
Apparently booting like this shows extra verbose messages, because now I have a screen full of stuff, with three interesting messages at the bottom:
```
[time] VFS: Cannot open root device "<NULL>" or unknown-block(8,1)
[time] Please append a correct "root=" boot option; here are the available partitions:
[time] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)
[time] Rebooting in 180 seconds..
```
Now, from my time with OS X, I know that kernel panics are a Very Bad Thing. I can no longer boot into Ubuntu, and the bootstrap system (the screen before yaboot) doesn't seem to want to boot my 8.04 Server install CD to let me try and fix things. I have a few other discs I could use, but I can't eject the disc in there to try it (although I haven't tried holding the mouse down at startup; it doesn't have one).

I am pretty much at a loss, most of my experience is with linux, and not with the bits that get linux running. Any ideas?

---

### Post by MikeTheC on 2009-06-18
The only way you're going to be able to eject the CD on boot is with a mouse attached.

---

### Post by grundygreen on 2009-09-23
I've been having this issue too.
I've had ubuntu installed on this machine before.
So what is the issue?

---

### Post by sweetleaf on 2009-09-25
Is it a slot-loading iMac? If so, it should actually have a standard Mac paperclip-eject hole on the right side of the slot. It's hard to see, because it's *inside* the slot. I don't remember whether or not you need power to eject; you might want to google that before trying. :-)

I have no idea how to recover from a kernel panic. But if you do recover, and you make it back to the first [FONT="Courier New"]aty128fb[/FONT] error, don't let that part deter you. I had the same problem with a fresh Jaunty install, and managed to get past it with some graphics tweaks. I don't remember exactly what I did, but it was probably something to do with yaboot options--nosplash, nofx, quiet, and/or video=ofonly. 

As a side note, I'd love to hear from anyone who's managed to get X.org in Jaunty to use the r128 driver for this Rage card...

---

### Post by lx45803 on 2009-09-26
I have bad news for you grundy. My solution to this was as follows:
1) Disassemble iMac to remove hard drive.
2) Put in other computer, copy home folder
3) Format hard drive, set aside
4) Disassemble iMac CD drive to remove 9.04 install disk (this one was not fun)
5) Reassemble everything
6) Install 8.04
7) Remove hard drive - again
8) Mount in second computer again, put home folder back
9) Reassemble everything - again

Sorry to be the bearer of bad news, but this is the only thing I could think of to save my little backup computer. Fortunately, my iMac now lives in my basement (where it's out of the way, and well cooled), humming away almost silently with the quietest 120 GB hard drive I've ever heard.

If you're willing to go through about 4-6 hours of kinda difficult, possibly dangerous work (for your computer, probably not you), you should be able to save your computer. If you want to go through with my solution, then I'll try and provide a little more detailed instructions for disassembling your iMac to get at the hard drive (it can be a bit tricky if you don't know what you're doing).

Let me know what you decide.

---

