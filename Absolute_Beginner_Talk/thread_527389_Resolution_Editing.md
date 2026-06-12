---
title: "Resolution Editing"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-16
I have Ubuntu 7.04 running in Virtual Box but everything looks
really big the icons are pretty large and the text just seems to
be large as well.  I know that I can play around with the Font
Settings and Stretch the icon but I think it's the Resolution.

The highest I can set it to is 1024 X 768
My Monitor supports 1280 X 1024.

I went in and looked at xorg.conf but am not sure what to do
Could someone tell me what to do.  thank you.

[IMG]http://img106.imageshack.us/img106/3303/resolutionshotwq2.png[/IMG]

---

### Post by S15_88 on 2007-08-16
where it says Depth 24, the last one there near the bottom add "1280 X 1024", then save it, ctrl+alt+backspace to restart your xserver.  it may change automatically or u might have to select it under resolutions, if neither work try reconfiguring your xserver:
> sudo dpkg-reconfigure xserver-xorg 
and where it asks for your desired resolution just add all the ones you want and that should work!

Thanks, Alain

---

### Post by kellemes on 2007-08-16
Before editing xorg.conf create a backup.

Edit the modeslines to be.. "1280x1024" "1024x768" "800x600" "640x480"
So just insert "1280x1024" into the current lines and see what happenes.

---

