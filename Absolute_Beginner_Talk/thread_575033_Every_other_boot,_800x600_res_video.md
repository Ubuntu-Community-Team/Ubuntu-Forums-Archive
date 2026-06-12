---
title: "Every other boot, 800x600 res video"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by neander on 2007-10-13
I installed 7.04 on a new box that has nvidia geforce 8400 gs video and was surprised to see the video come up at my lcd screen's default high resolution. Some other ubuntu installs needed TLC in the video driver dept but not this one I thought. But, it seems that about 50% of my boots result in 800x600 res max. What's the scoop with this?

---

### Post by neander on 2007-10-14
Strange, I posted a reply to this about 18 hours ago and it seems to have vanished.

In that post I thought I had success with this issue after installing Envy; but not so. Now my new pc boots in 640x480 only.

I hope someone can help with this.

I wonder why video drivers seem to be a problem with ubuntu, which does so many other things so well? I mean, the massive stack of packages that are 7.04 installs perfectly; but something as fundemental as video drivers is left to happenstance? That's just weird. It's not like I'm using some archaic video cards. All of my ubuntu installs have had issues with both ATI and nVidea cards. There must be some reason that ubuntu fails to cover this essential aspect, but what is it?

---

### Post by ghost_ryder35 on 2007-10-14
reconfigure X.

---

### Post by neander on 2007-10-14
In case anyone else runs into the same issue you can recofigure x with

sudo dpkg-reconfigure xserver-xorg

This forum software won't let you search on 'x' which is not helpful.

At the end of may dialogs which are complete mysteries to a newb the reconfig ended wtih

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20071014114433

Have no idea what that meant. The reconfig process ended abruptly with no warning, so I was not sure if it aborted or just ends like poof. After a reboot (there is no instruction re need to reboot) I do have higher screen res but I don't know if that will persist.

It's a lousy process and I'd still like to hear something about why video support seems to be so weak. Too, why in my orginal cofig, and the config after envy, would I have radically diff screen res when rebooting, at random?

---

