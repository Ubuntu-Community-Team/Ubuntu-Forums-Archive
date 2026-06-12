---
title: "Graphics card"
date: 2010-04-29
forum: Apple Hardware Users
---

### Post by wutzi on 2010-04-29
Hi everyone, 

My Macbook Pro 5,1 has obviously two graphics cards. Is there any way two change between the two? I'm asking because the big one uses a lot of battery and I would like to use the small one when I'm on battery.


Thank You

Wutzi

---

### Post by zeroti on 2010-04-29
I'm not sure if it's a feature of Ubuntu at this point, but you can check this out in the meantime:

[http://www.phoronix.com/forums/showthread.php?t=21879](http://www.phoronix.com/forums/showthread.php?t=21879)

---

### Post by P4man on 2010-04-29
its still very experimental on linux at this point. I think its called VGA switcheroo, but its not yet for the faint hearted and not anywhere as smooth as apple's implementation (think it even requires restarting X).

Feel free to google on it and experiment, but its really bleeding edge right now. At least afaik.

---

### Post by wutzi on 2010-08-02
vga-switcheroo doesn't seem to work for me, maybe im to inexperienced. Any other ideas or a good how-to? The how-to on the switcheroo site doesn't seem to be for ubuntu

---

### Post by P4man on 2010-08-02
I dont know what howto you followed, but afaik, using switcheroo involves compiling your own  kernel.  Very short how-to here:
[http://www.phoronix.com/forums/showthread.php?p=131571#post131571](http://www.phoronix.com/forums/showthread.php?p=131571#post131571)

If you need help compiling a kernel, google on it (and dont ask me, im not geekish enough lol).

Note that poster has an ATI card while i guess you have an nVidia card. Also note they compiled from the git tree as apparently there was a bug fixed recently.

---

### Post by alexmurray on 2010-08-02
To switch to the 9400M you'll first have to boot via EFI, then you can simply specify the correct PCI device ID in you xorg.conf to choose which GPU to use - the MacBook Pro disables the 9400M when doing a legacy bios boot (which is the way which it will be booting unless you've specifically set it up to boot via EFI).

See here for a bit more info [https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#EFI](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Jaunty#EFI) (note this was for Jaunty so it may not work anymore on the later versions of Ubuntu)

---

