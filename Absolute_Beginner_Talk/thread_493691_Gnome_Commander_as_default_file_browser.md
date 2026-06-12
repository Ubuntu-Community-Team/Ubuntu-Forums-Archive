---
title: "Gnome Commander as default file browser?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by tabithaboof on 2007-07-06
Just a quick one, I love Gnome Commander and would be very happy if somone could let me know how to make it my default file browser/manager!

Thanks alot

---

### Post by KIAaze on 2007-07-06
I was about to suggest to simply replace the nautilus executable with a link to the gnome commander executable, but since nautilus is used to draw the desktop, this might not be such a good solution.

This trick here seems much more appropriate:
[http://ubuntuforums.org/showthread.php?t=48169]("http://ubuntuforums.org/showthread.php?t=48169")
It's for replacing nautilus with rox-filer, so you'll have to adapt step 5 as follows:
```
NAUTILUS_REPLACEMENT=/usr/bin/gnome-commander
TRASHDIR=$HOME/.Trash
export TRASHDIR NAUTILUS_REPLACEMENT

```
Another link of interest:
[http://ubuntuforums.org/showthread.php?t=105517]("http://ubuntuforums.org/showthread.php?t=105517")
> **Evil Whisper said:**
> to have a wallpaper without the nautilus desktop install feh:

```

sudo apt-get install feh

```

and then look here for how to set your wallpaper under the background section: [https://wiki.ubuntu.com/Openbox?highlight=%28Openbox%29](https://wiki.ubuntu.com/Openbox?highlight=%28Openbox%29)

Hope This Helps,
- Evil Whisper

---

