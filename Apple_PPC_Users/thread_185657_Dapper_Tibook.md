---
title: "Dapper Tibook"
date: 2006-06-01
forum: Apple PPC Users
---

### Post by shriver on 2006-06-01
Well, I've got Dapper running on my tibook (Powerbook G4 DVI 800mhz). I'm impressed so far. I've got OS X running under Mac-on-linux for extra fun. Here are the issues I have as of now (this is both a rant and a cry for help). I've been looking into them various places, and so far have come up short.

- Tap to click: My synaptics touchpad works great, but I would really like to enable the tap-to-click feature. I've found a million places telling me how to disable it, but none so far on how to enable it

- Right/middle click: I find the f11/f12 keys annoying for right/middle clicking. What I'd really prefer is to map it as close to how it's done in Mac OS-- something like ctrl+click for right click and command+click for middle click.

- The command Key: Can I just map this to CTRL?

- Suspend: This machine suspends perfectly (for instance, when I close the lid). Resuming is another story. When it tries to resume, the backlight comes on and the disks spin up as if it were coming back alive, but the screen stays blank indefinetely.

- Boot up time: This one is specific to my own busted-*** hardware. The CD ROM drive on this machine is dead, and so when it boots, it hangs on a black screen for an extended period of time. I _assume_ that this is due to the kernel waiting for the CDROM to time out. Is there a kernel option I can pass at boot to have the kernel skip this drive?

So far I am extremely pleased, I may even just let this machine boot into Linux full time and use mol when I need mac-ish things. Any help or pointers on any of these issues would be appreciated.

Thanks,
-- Mike Shriver

---

### Post by rajif on 2006-06-02
> - Tap to click: My synaptics touchpad works great, but I would really like to enable the tap-to-click feature. I've found a million places telling me how to disable it, but none so far on how to enable it

You can control it with the "trackpad" command.
It's part of the powerpc-utils package.

J

---

### Post by onehotcutey on 2006-06-03
Thanks for the trackpad reference.... it's works very nice.

As for remapping the keys, there is a reference for remapping the keyboard in an older forum, however I couldn't quickly locate it in a search.  If someone knows how to do this from the command line, rather than the GUI, as I've tried with the GUI and R-click doesn't seem to be an option, it would be great...

---

