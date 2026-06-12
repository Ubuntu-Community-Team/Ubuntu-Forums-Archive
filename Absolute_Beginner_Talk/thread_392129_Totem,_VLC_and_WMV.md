---
title: "Totem, VLC and WMV"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Campingman on 2007-03-24
I know this question has been asked hundreds of times and apologise in advance. 
Due to a bad experience with Beryl (again).  I ended up having to reinstall Ubuntu and know I cannot get Totem to play WMV files, I had all this working last time, I have follwed instructions here
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
and also installed the w32 codec package.  It still will not play WMV (this was so simple last time!)
Life is too short for this, 
Any ideas before I go back to XP!

---

### Post by tommcd on 2007-03-24
Try installing all the gstreamer plugins from the restricted formats web page, if you have not done so already. If you still can't play wmv videos, see this:
[http://ubuntuforums.org/showthread.php?p=1649012](http://ubuntuforums.org/showthread.php?p=1649012)

---

### Post by Campingman on 2007-03-24
Thanks tommcd,

This did it for me, very odd why it did not work in the first place?

rm -rf ~/.gstreamer-0.10
gst-inspect-0.10

Just need to resolve my VO problem with mplayer now (that worked first time last time as well), I really do not like Beryl at the moment!

---

