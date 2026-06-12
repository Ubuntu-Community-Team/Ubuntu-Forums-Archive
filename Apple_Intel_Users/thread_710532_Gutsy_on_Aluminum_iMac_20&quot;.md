---
title: "Gutsy on Aluminum iMac 20&quot;"
date: 2008-02-28
forum: Apple Intel Users
---

### Post by berniejv on 2008-02-28
Hey all:

I've just installed Gutsy on my 20" aluminum iMac -- many thanks to the various posts (and authors of rEFIt), which made the install a breeze.  Don't get me wrong; I love OS X, but sometimes you just need the linux, right?  Especially when it has synaptic...

;)

There are, however, some interesting problems (besides the sound, which I'll have to try the patch for, and the AirPort Extreme, which I'm not sure works just yet (correct me if I'm wrong)?).  First, hibernate/sleep don't seem to work.  Any other corroborating experiences?

Also -- and this may expose me as a total novice -- I managed to muck up the display settings, rendering the graphical login useless.  Is there an easy way to remedy this by booting from the live cd or logging into the console at a lower runlevel to clobber/reset some GNOME settings?

...which reminds me...  the aspect ratio for the display seems wrong.  Stretched horizontally, that is.  The autodetected display settings can't seem to handle 1680 by 1050.  What are others using out there?  I think I had it on 1400 X <something> with a 60Hz refresh.  There didn't seem to be a matching display in the pulldown that made sense to me.

Thanks in advance for your help/advice -- I'm glad to have jumped aboard.

-J

---

### Post by cyberdork33 on 2008-02-28
Try this:
[http://ubuntuforums.org/showpost.php?p=4415752&postcount=10](http://ubuntuforums.org/showpost.php?p=4415752&postcount=10)

Your wireless requires ndiswrapper.

We will get back to suspend. First get the graphics working right as that usually prevents suspend anyway if anything.

You are likely using Gutsy which has some older ATI drivers. Try installing newer ATI drivers with [Envy]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by berniejv on 2008-02-28
Thanks man...

I'll try envy and see what happens...

any reason offhand to install 32-bit over 64?  I actually think I installed the 32-bit version...  but the core 2 duo architecture is x86_64, right?

also, regarding swap space; is this still required as a separate partition in the days of gigabytes of ram?

Thanks again...

---

### Post by cyberdork33 on 2008-02-28
swap is required for hibernate (since that is where it stores the system state) and it needs to be at least as big as the amount of ram you have. Some people do not use it at all.

I use 64bit exclusively. There are tools that make it pretty easy nowadays even with flash and java. 32bit is fine though, and you are likely to not see a difference. See differences here;
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by berniejv on 2008-02-28
I'm actually running Matlab (32-bit), so I may just go with the 32-bit to be safe...

Any tip for reverting to default display settings so I can actually use the graphical login and GNOME in the meantime?  Is that stuff stored in some hidden .gnome settings directory?  Or can I fix it from the live cd?

Thanks again for your help!

---

### Post by cyberdork33 on 2008-02-28
I really don't know what you did. You should be able to start in recovery mode (it is a kernel option in grub). If that stil doesn't work, then you have some issues. It might be easiest to just reinstall if you haven't used it much yet.

---

