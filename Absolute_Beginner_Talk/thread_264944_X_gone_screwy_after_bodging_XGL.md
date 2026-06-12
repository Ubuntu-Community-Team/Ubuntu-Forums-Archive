---
title: "X gone screwy after bodging XGL"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Kirky_D on 2006-09-25
After trying to instal xgl/compiz (in this thread: [http://www.ubuntuforums.org/showthread.php?t=264158](http://www.ubuntuforums.org/showthread.php?t=264158) )

I have managed to destroy my X. at first i thought it was due to this part of the guide

```

sudo gedit /etc/gdm/gdm.conf-custom

At the very bottom of the file add the following lines:

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
flexible=true

```

so i boot in recovery, use vi to edit the file, and get rid of the offending lines, no luck.

I have tried reconfiguring xorg again, no luck

Could somebody help me please, 

Also is there a way to access files on a hard drive while on the live cd?

Thanks in advance!

---

