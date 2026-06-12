---
title: "kdm running, but screen blank...?"
date: 2007-10-24
forum: Apple PPC Users
---

### Post by prairie_dad on 2007-10-24
G4 PPC, quicksilver, 768 meg RAM, 667 MHz cpu, old 17" apple flat panel monitor (studio.)  ran 7.04 fine, now updated to 7.10 (after fixing the stupid ide_core glitch, shame on testers...)

So, it appears to boot fine, splash comes up, blue bar beneath "Kubuntu" fills nicely left to right, and then...a flash ... and nothing.

```

Loading, please wait...
Kinit: name_to_dev_t(/dev/disk/by-uuid/...device uuid
kinit: No resume image, doing normal boot...

```

I *think* this flashes briefly before the screen goes blank, and I know it's what is there when I hit control + alt + F1 to get to a login prompt.  I can log in fine, uname -r gives correct kernel, xorg.conf looks right...(same as on my identical hardware, gentoo box)  Ethernet is also fine, i can use lynx to get to internet...but no KDE.  maybe kdm is the culprit...but I doubt it.  

If, at a command prompt, I type "startx" I get the error message that the server is already running...where?

in gentoo I could find how to turn kdm (or gdm or xdm) off, and only get them from typing startx at command prompt, how do I do that in Ubuntu...?  The directory I'm accustomed to, /etc/conf.d is not present in Debian, I guess...

Any thoughts.  I suspect the whole box will work great save for one line is some config file, but how to find it?

thanks

---

### Post by BladeMelbourne on 2007-10-25
It might be something like
/etc/init.d/gdm stop
or
/etc/init.d/kdm stop

or you could always
sudo killall kdm which is recommended for any machine with KDE on it. I jest ;-)

You should then be able to type X or startx...

---

### Post by helixblue on 2007-10-25
This shows how to disable gdm in Ubuntu, you should be able to apply it to kdm: 

[http://www.howtogeek.com/howto/ubuntu/prevent-xorg-from-starting-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/prevent-xorg-from-starting-in-ubuntu/)

Worst case, if you rename/delete /etc/X11/default-display-manager, it should do the trick too.

One thing you should try, especially if you have an ATI chipset, is to go to console (Ctrl-Alt-F1) and then swap back (Cmd-F7)

---

### Post by prairie_dad on 2007-10-27
> **helixblue said:**
> ...
One thing you should try, especially if you have an ATI chipset, is to go to console (Ctrl-Alt-F1) and then swap back (Cmd-F7)

That doesn't work for me...for some reason.  By Cmd you mean the "Apple" or "cloverleaf" key, I assume...

I rebuilt the thing overnight, with Ubuntu Gutsy (as opposed to Kubuntu) since I have KDE on my Gentoo box already, thought I'd try the opposition (XFCE on an old, slow PC, where it belongs...and Fluxbox on a virtual machine at work) but of course the issue remains...have fixed the ide_core absence in modules...

Again, I am sure everything is ready to fly, save some x-windows issue...which I can't resolve...help!

---

