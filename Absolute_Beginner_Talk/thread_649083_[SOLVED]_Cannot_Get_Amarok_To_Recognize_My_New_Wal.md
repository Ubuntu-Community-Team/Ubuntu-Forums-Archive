---
title: "[SOLVED] Cannot Get Amarok To Recognize My New Walkman Media Player."
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Epic Plecostomus on 2007-12-24
It's a NWZ S615F if that matters.  It's asking me for the mount point mount command and eject commands...  None of which I know how to set up.

---

### Post by the Didey on 2007-12-24
you need to decide or find out where the media player mounts....then you tell amarok then it can connect.

To fin the mount point either check in "/media" and see if you see what you're looking for.

to get the settings in amarok straight. go to the settings--->configure devices and tell amarok where that mount point is.

also if the media player shows up on the desktop then you can use right-click properties to find out the mount point.

---

### Post by the Didey on 2007-12-24
Here's a more detailed description.

MY Ipod is named "I MEAN"....Note that when I first plugged it int it was called by some device=like name and I had to change the name in gksudo nautilus.

When I plugged it in....I went to computer-->filesystem-->media and made sure it was there. Then I double click the ipod and get the path (aka Mount point) which is /media/I MEAN

I actually got this wrong in the other post.....In Amarok it's Settings-->Configure Amarok then go to the media devices tab. click add device and fill in the box.

Also note that, after all this,  when you plug it in you have to tell amarok to connect to it.

---

### Post by Epic Plecostomus on 2007-12-24
That solved it.  Up and running now.   Happy holidays!

---

