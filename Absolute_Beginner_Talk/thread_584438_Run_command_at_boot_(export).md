---
title: "Run command at boot (export)"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by swedishlf on 2007-10-21
Hey guys I've set up a few things to run via the /etc/init.d/rc.local file, and so far no problems.  However the following command doesn't stick:

export SDL_VIDEO_X11_DGAMOUSE=0

even with it in the rc.local file, I can switch to a terminal and type echo $SDL_VIDEO_X11_DGAMOUSE and I get a null return.

The listed command is required to get my mouse properly functioning in both kvm and dosbox, so I'd like it just to run at boot.  Anyone have any suggestions?

---

