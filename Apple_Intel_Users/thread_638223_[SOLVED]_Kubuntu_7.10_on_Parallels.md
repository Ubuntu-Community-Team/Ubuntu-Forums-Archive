---
title: "[SOLVED] Kubuntu 7.10 on Parallels?"
date: 2007-12-11
forum: Apple Intel Users
---

### Post by street spirit on 2007-12-11
Hi.

I'm having a hard time trying to install Kubuntu Gutsy on Parallels 3.0. The live CD boots up, but kdm never finishes loading. There is no error message; I can see the blue kdm background for a while, and I get a high-resolution mouse cursor, then I drop back to the terminal.

I have tried:
  - safe graphics mode
  - reducing all allocated resources (RAM, etc) back to the Parallels defaults
  - the "all_generic_ide" option (from [[COLOR="Blue"]this post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3013895&postcount=11"))
  - the line *Option "LVDSBiosNativeMode" "false"* in the Device section of xorg.conf.

A manual "startx" gives the following warnings/messages:
(WW) VESA(0): Failed to set up write-combining range (0xc0000000,0x1000000)
(EE) AIGLX: Screen 0 is not DRI capable

I would consider installing Feisty instead, because a few people seem to have had better success with it, but i can't even find the ISO on the kubuntu website anymore.
Oh, and Gutsy is running fine when I boot it on the same box without virtualization.

I'm running OSX 10.5 on a Mac Pro with an NVidia GeForce 7300 graphics card, 5GB or RAM, and 2 x 2.66GHz Xeons. The monitor is an Eizo FlexScan S2431W with a native resolution of 1920 × 1200.

Any ideas what to do next?

---

### Post by cyberdork33 on 2007-12-11
reduce memory in the VM

---

### Post by street spirit on 2007-12-12
I was already down to 512MB, and even setting the limit to 256MB did not solve the problem.

What did help: boot from the alternate install CD and use the textmode installer. Then, after rebooting, either wait for X to crash again, or boot in single user mode - anything that gives you a shell. Install the Parallels Tools (there's a menu option in Parallels for that).

After that, I could start X normally, and had the full 1920x1200 resolution.
Even resizing the display dynamically works as it should.
Neat. :-)

---

### Post by jamescoy on 2008-01-25
I tried exactly the same thing and ended up with being returned to a prompt in the terminal which said:

Running local boot scripts (etc.rc.local)

After that, nothing happened at all.

Any other ideas?

---

### Post by street spirit on 2008-01-25
> Any other ideas?

I have since switched from Parallels to VMware Fusion. The price is exactly the same, and Fusion already seems to be more mature, although Parallels had a nice head start at Mac virtualization. I also like the way the special keys on the Apple keyboard are handled a lot better in Fusion. If you haven't invested too much time yet in Parallels, you may want to give it a try:

[http://www.vmware.com/products/fusion/]("http://www.vmware.com/products/fusion/")

edit (PS): VMware also offer an import tool for Parallels images (haven't tried it though).

---

### Post by alek66 on 2008-02-18
so ....how does this get solved??

---

### Post by street spirit on 2008-02-19
> **alek66 said:**
> so ....how does this get solved??

How does *what* get solved?
I described what I did to get Gutsy working in the 3rd post of this thread, and in the 5th post I pointed out an alternative to Parallels that works even better.
Could you be a little more specific?

---

