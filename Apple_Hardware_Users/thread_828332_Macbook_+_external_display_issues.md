---
title: "Macbook + external display issues"
date: 2008-06-13
forum: Apple Hardware Users
---

### Post by jopari on 2008-06-13
When I used OS X, I used my external monitor for two things: 1. watching fullscreen movies on and 2. extending my display to the right of the Macbook's screen. I've had no luck with either in Ubuntu, despite trying everything I've found (xrander/grandr, Screen Resolution, Screens and Graphics).

When I plug in the display, the external display presents a cloned version of my Macbook's 1280x800 display-only inexplicably squashed. Fullscreen video in Totem defaults to the external (which is how I want it). If I change the resolution of the Macbook's display, the external monitor's picture is no longer squished, but when I try to play fullscreen video in it, the fullscreen always plays on my Macbook's display. (Also Compiz acts strangely when the external's plugged in but I can deal with that).

I'm fine with the external display not extending to the right (workspaces solve my need to always have Banshee open), but I am curious as to why it was possible in OS X but not Ubuntu.

Thank you so much for your help!:)

---

### Post by buschi on 2008-06-14
hey there!

did you put the "virtual" section into your xorg.conf? it's described for example on this page: [http://ubuntu-tutorials.com/2007/11/25/extended-video-on-the-macbook-xrandr-ftw/]("http://ubuntu-tutorials.com/2007/11/25/extended-video-on-the-macbook-xrandr-ftw/")

they write that compiz does not work at this resolution or whatever -- you can find other opinions on that elsewhere: that the dimensions must both be not larger than ... (i forgot). this means that if your external monitor is so large that it would cross this limit when putting it beside your screen, it might still work putting it on top of your screen!

good luck,
sebastian.

---

### Post by fishes on 2009-02-04
This thread is probably resolved, but since everyone with an Ubuntu MacBook seems to run into this issue, I thought I would mention that I also found [http://ubuntu-tutorials.com/2008/04/28/extended-display-on-the-macbook-with-xorg-conf-ubuntu-804/](http://ubuntu-tutorials.com/2008/04/28/extended-display-on-the-macbook-with-xorg-conf-ubuntu-804/) to be very helpful when installing 8.10 on my 2.1 MacBook with a 22" 1680x1050 Dell Ultrasharp. The one difference is that I used the command

```
xrandr --output TMDS-1 --auto
```

from [https://help.ubuntu.com/community/MacBook2-1/Hardy](https://help.ubuntu.com/community/MacBook2-1/Hardy)

instead of

```
xrandr &#8211;output VGA &#8211;auto
```

I was able to arrange the monitors in Screen Resolution.  Compiz does not work as predicted. EDIT: However, this thread has a great explanation of why, and which screen layouts will actually get Compiz to work. I now have Compiz working with the 22 inch external and the internal set vertically, and it took only a little rearranging on the desk to make it physically work. See: [http://ubuntuforums.org/showthread.php?t=768761&highlight=compiz+resolution](http://ubuntuforums.org/showthread.php?t=768761&highlight=compiz+resolution)

I also noticed that it greatly streamlines the process of getting the monitors working if you install without an external monitor attached. This might be a no brainer, but I didn't do it the first time since my MacBook is basically a desktop.

Thanks.

---

