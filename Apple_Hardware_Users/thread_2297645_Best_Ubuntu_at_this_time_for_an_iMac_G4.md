---
title: "Best Ubuntu at this time for an iMac G4?"
date: 2015-10-05
forum: Apple Hardware Users
---

### Post by Roger-H on 2015-10-05
Hi, I've been trying (unsuccessfully) to get Debian Jessie installed on an iMac G4 "desk lamp" that I was given. Unfortunately I am having a problem with the video driver - the machine's display fades out when it gets to the login prompt. I can use the "nomodeset" option from yaboot to get to a strangely-colored screen with a mouse pointer, then use ctrl-alt-F1 to get to a text login.

From what I am told, this is not uncommon and has to do with a known problem using the nouveau vs. nv driver. However, at some point I will be throwing in the towel and trying a Ubuntu-based distro. The question is which one? Lubuntu? Ubuntu MATE? 15.10? Maybe an earlier one like 12.04? Please let me know what the path of least resistance will be. Thanks.

---

### Post by rican-linux on 2015-10-05
I would try Lubuntu 12.04 or 14.04. However 12.04 I believe is end of support.

---

### Post by rsavage on 2015-10-05
> **rican-linux said:**
> However 12.04 I believe is end of support.

Only if you are pedantic (like a mod).

Assuming you have imac 700/800 which doesn't work with nouveau.

The xserver in 12.04 was the last to work with nv on PowerPC.  Although you can install that version of xserver in 14.04 too so you can use nv in 14.04 too.  See known issues page.

But you can also use fbdev with the nvidiafb framebuffer.

Easy.

---

### Post by Roger-H on 2015-10-05
> **rsavage said:**
> Assuming you have imac 700/800 which doesn't work with nouveau.Yes, this seems to be the exact problem that I am having. If I give up on Debian I will try Lubuntu 12.04. Thanks.

---

