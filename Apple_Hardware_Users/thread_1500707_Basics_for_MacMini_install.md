---
title: "Basics for MacMini install"
date: 2010-06-03
forum: Apple Hardware Users
---

### Post by poconnell2005 on 2010-06-03
So... I managed to get the latest LT install onto my MacMini (intel) without much of an issue. I am currently having an issue with a couple of things though.

1. I am unable to connect to my wireless network. Does anyone have very dumbed down instructions for this? It has been a long time since using Linux and I am very very very rusty :)

2. I am using a 26" Sanyo LCD TV as the monitor and the Ubuntu display is too large for it. I run into the same issue on the OSX side but there I am able to simply mark a check box and it shrinks it down. On the Ubuntu side, I don't know where to begin. It is oversized to the point where I am unable to see the menus at the top or bottom. Any suggestions?

---

### Post by poconnell2005 on 2010-06-03
Oddly enough, when I logged into the Ubuntu install tonight, I got a pop up stating that my wireless had detected networks so I was able to select mine, add my password and presto I was online. Weird especially since I spent a good hour or so trying to figure it out last night.

I am still having issues with my monitor though. The display is still cut off along all sides (is it technically called overdriven?). I can't see the top or bottom menus and both left and right are off the screen as well. When I open up my display properties, I can't change any options (resolution, refresh rate, etc). I assume that I am missing something VERY basic, but I just can't figure it out. Any suggestions?

Thanks in advance for any help.

---

### Post by tmette on 2010-06-03
I have my Ubuntu hooked up to my Samsung HDTV/Monitor and had the same problem with everything being cut off.  I had to go into the Video properties under the TV menu.  I had it forced to widescreen or something and that was making it get cut off.  Once I changed it to accept whatever ratio the source was, it fixed it.

Try your video settings on the TV.

---

### Post by poconnell2005 on 2010-06-08
Thank you for the advice.

Sadly, my TV/Monitor does not offer this option. I have 4 available views 2 versions of 4:3 and 2 versions of 16:9. None of these work as a solution to this problem.

Is there any way to adjust the screen size via Ubuntu? When I bring up the adjustments for my monitor under Ubuntu, it shows my TV, but does not allow for any adjustments. Perhaps I am missing something very basic? I hope that that is the case as it is unusable as it is.

Thank you in advance.

---

### Post by linuxopjemac on 2010-06-08
try to find the right modelines with cvt and add them in the monitor section of xorg.conf

[http://mac.linux.be/content/setting-xorgconf-manually-xrandr](http://mac.linux.be/content/setting-xorgconf-manually-xrandr)

---

