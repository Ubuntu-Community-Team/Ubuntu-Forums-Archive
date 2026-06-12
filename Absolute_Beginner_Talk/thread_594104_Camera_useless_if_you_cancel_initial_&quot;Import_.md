---
title: "Camera useless if you cancel initial &quot;Import Photos&quot; dialogue"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-10-27
Using my Fugi FinePix S700 with a 2GB SD card, USB cord and Ubuntu 7.10, I can not find the volume of my camera.

The only time I can see the photos is when I actually accept the initial "Import Photos" but I don't like to use gthumb.

In "Removable Drives and Media" under 'Storage', 'Browse removable media when inserted' is checked on (which is what I want) but it doesn't work. As in, I want and like using nautilus to browse my photos but the volume does not seem to be detected.

I know under 'Camera' I can change 'gnome-volume-manager-gthumb %h' to whatever I'd like, but 'nautilus %h', 'nautilus %u' and 'nautilus' all still seem to bring up gthumb.

So in conclusion, my biggest worry is that Ubuntu can not detect my camera. What's going on!?

---

### Post by p_quarles on 2007-10-27
Could be that the camera's firmware doesn't play nice with Nautilus. You could install an alternative file manager, like Thunar, and see if that works any better. Alternately, you could just remove the SD card and plug it in directly (card readers are fairly affordable, if you don't have one built in). There are some cameras that won't work *well* with Linux, and this is a pretty foolproof workaround.

---

### Post by altonbr on 2007-10-28
So basically Linux doesn't support my camera.

I understand that's the vendors fault for not open sourcing their product tech sheets, but it's very frustrating.

Yes I can work around it, but Nautilus should at least see the volume, even if it's using a generic driver. Seems silly.

---

### Post by p_quarles on 2007-10-28
So, gthumb works, but Nautilus doesn't? That's not a good basis for concluding that your camera isn't supported by Linux. Like I said, try another file manager. Lots of people have problems with Nautilus, and just because it comes with the OS doesn't mean you can't use something else. 

Here's a good guide to setting up other file managers to run by default:
[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

