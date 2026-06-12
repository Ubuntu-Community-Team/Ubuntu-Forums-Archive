---
title: "WMV file needs new Codec"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Linc1 on 2007-03-12
Ok, so how do I make this thing play these files?

Linc

---

### Post by Timtro on 2007-03-12
My strong recommendation is VLC media player. I also think you can simply,
```

sudo apt-get install vlc

```

---

### Post by Linc1 on 2007-03-12
Well I don't know much about this stuff, so I assumed what you gave me was a terminal command to which I got the following in reply


Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc


So what next? Did I do something wrong?

Linc

---

### Post by russell.h on 2007-03-12
You probably need to enable more repositories. You should be able to go to "System > Administration > Software Sources" then enable "universe" and "multiverse" (not sure which one VLC is in).

Or you could use Automatix which can install all the codecs you'll ever need (just google Automatix I think, unless its in the repos, I can't remember).

Edit: after you enable universe and multiverse run the command Timtro said again and it should work.

---

### Post by Adam_GUI on 2007-03-12
> **Linc1 said:**
> Well I don't know much about this stuff, so I assumed what you gave me was a terminal command to which I got the following in reply


Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc


So what next? Did I do something wrong?

Linc

There's a link to VLC here:
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

You need to enable the Universe repos.
ALT+F2 and type ```
sudo synaptic
```
Settings > Repositories
Then check the box with (Universe) at the end of the line.
Then you can either search for VLC, do the apt-get in command line, or follow directions given in the link to the VLC page.

Hope that helps!  :)

---

### Post by Timtro on 2007-03-12
> **Linc1 said:**
> Well I don't know much about this stuff, so I assumed what you gave me was a terminal command to which I got the following in reply


Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc


So what next? Did I do something wrong?

Linc

Whoops! I'm sorry to add confusion. Yes, indeed a terminal command, and it looks like our friends have helped us with the package not found.

Give VLC a try. Its a very nice player and comes with many needed codecs, although this Automatix business seems quite cool! :) I can't wait to try it. Thanks

---

### Post by towsonu2003 on 2007-03-13
this link should be helpful not only for codecs but also dvd and other stuff: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

