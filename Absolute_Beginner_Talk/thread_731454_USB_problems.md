---
title: "USB problems"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by iainv on 2008-03-21
Dammit.

Was having problems getting VirtualBox XP to recognise USB ports.

I've followed all the advice I can find, installed all the updates and followed the instructions here: [http://www.arsgeek.com/?p=2776](http://www.arsgeek.com/?p=2776) which is the most concise summary of all the other suggestions.

And now not only does VirtualBox STILL not detect USB, but my memory stick is no longer detected in Ubuntu.

The wifi and the mouse (both USB) are still working, so something's getting through, lsusb just hangs now though, so i've no idea what's going on.

Help!!!!

Iain

---

### Post by iansane on 2008-03-21
Here's a solution I used for vmware. It puts an entry in fstab that mounts all usb. It's probably the same issue.

[http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=3862823](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=3862823)

---

### Post by iainv on 2008-03-21
Thanks - you've fixed the problem with my memory stick and lsusb is working again.

Sadly VirtualBox still doesn't see a USB port anywhere. :(

Anything else I can try?

---

### Post by iainv on 2008-03-21
OK - partially solved but not there yet.

The first part of the solution was to realise i'm an idiot! - I was using the OSE version of VB which doesn't include USB support. Having downloaded and installed the PUEL version VB can now see the USB device, and windows detects a USB hub...



...but not the scanner.

:(


Any help appreciated!

---

