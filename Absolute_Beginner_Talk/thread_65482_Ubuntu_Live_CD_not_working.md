---
title: "Ubuntu Live CD not working"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by Afrika on 2005-09-14
Hi.
This is probably the right place for me, since I'm brand new to Linux.
I downloaded the Ubuntu Live CD, to see how this thing will work, before I decide to convert to Linux.
When Live CD booted up, there was a long list on the Dos(or Dos lookalike) screen, which showed normal status for almost anything, until the end of the list.
This is some of the last listed:

ehci-hcd:loaded successfully
pci          [success]
running/etc/hotplug/usb.rc
[429467.161000] ohci_hcd 0000:00:0a.1:Unlink after no-IRQ? Controller is prob
ably using the wrong IRQ.

This is how far I got. The system DID NOT boot up in Linux mode.
Hope someone can help me with this.
Rgds Afrika

---

### Post by ds[de] on 2005-09-14
I'm new to this as well, but it looks like it's a problem with usb.

So maybe starting the Live-CD with "live debian-installer/probe/usb=false" (when you are asked for boot-options or [enter] to continue) could help.

---

