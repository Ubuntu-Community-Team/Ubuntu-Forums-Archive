---
title: "Can't mount USB devices in Feisty"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-06-02
Whenever I plugged in my USB flash drive, or my external hdd Feisty was able to read/write to both. After trying to install ntfs-3g it seems like Feisty can't mount USB drives anymore. Can somebody help me so these devices can automount when I plug them in?

---

### Post by gh0st on 2007-06-02
I found that in feisty all I had to do was install ntfs-config and then I could tell it to automount dives for me fine. If you've installed ntfs-3g already then you might have the package installed already.

Try this

```
sudo apt-get install ntfs-config
```

Then have a look on the menu under "system tools" and there should be a configuration app, it doesn't have a lot of options but I found installing that package and just ticking the relevant box fixed my external NTFS drive problems.

Hope that helps a bit :)

EDIT: forgot to mention you might wanna remove any ntfs packages you've installed already before installing ntfs-config, I found that made a difference for me

---

### Post by alexyz on 2007-06-05
I was having the same problem.  To make it easier to find this thread, 

usb external hard drive mount broken after recent kernel update 2.6.20-16-386 dmesg /var/log/syslog errors like this

[11214.008000] usb 4-1: new high speed USB device using ehci_hcd and address 37
[11214.144000] usb 4-1: configuration #1 chosen from 1 choice
[11214.144000] scsi10 : SCSI emulation for USB Mass Storage devices
[11214.144000] usb-storage: device found at 37
[11214.144000] usb-storage: waiting for device to settle before scanning
[11214.524000] usb 4-1: USB disconnect, address 37
[11214.764000] usb 4-1: new high speed USB device using ehci_hcd and address 38
[11215.636000] hub 4-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[11215.748000] usb 4-1: new high speed USB device using ehci_hcd and address 39
[11216.268000] usb 4-1: device not accepting address 39, error -71

after installing these packages

libntfs-3g0 (1:1.328-1)
ntfs-3g (1:1.328-1)
ntfs-config (0.5.5-0ubuntu1)

the external drive auto-mounted just like it used to.  no reboot required.

I guess these weren't installed before.  not sure why they would suddenly become necessary.

it was a pain to figure this out.  this forums are too big anymore, too much noise.  we should really devote more effort to documentation, in some more structured form than a forum.  I'm as guilty as anyone.  pardon the off-topic rant.  :-|

---

### Post by alexyz on 2007-06-07
an update.  Same problem reappeared, fixed by reinstalling the ntfs packages (see previous post).  

Most likely the ntfs packages are not the problem.  The install fixes it, coincidentally.

I think the problem was this:  the auto-mount point was owned by root, and didn't go away when unmounted.  The mount point is a directory under /media  also visible under Places/Computer or in Nautilus under Go/Computer.  I wasn't able to delete it from nautilus, even when running as root.  

From the command line I deleted the mount point from /media, and that fixed it.  When I plugged in the drive it auto-mounted again.

-----------------------
part II:

When it auto-mounted, the mount point (directory) was owned by my user account, not root.  I copied some files, no problem.  Before I unplugged the drive, a few minutes later I got an "unsafe drive removal" or some such error, and (a little scary), my trusty command-line session showed a broadcast error:

  Message from syslogd@localhost at Thu Jun  7 21:13:26 2007 ...
  localhost kernel: [182976.088000] journal commit I/O error

Yikes.  Now the mount point is owned by root.  I assume if I go through the whole rigmarole again everything will work.

Important note if you've just installed:  auto-mounting was working flawlessly in the past.  As noted before I think it started after the recent kernel update.  This must be a bug.  I apologize I don't have time right now to try to track it down.

Tip to this post

[http://ubuntuforums.org/showthread.php?t=454465](http://ubuntuforums.org/showthread.php?t=454465)

:-|

---

