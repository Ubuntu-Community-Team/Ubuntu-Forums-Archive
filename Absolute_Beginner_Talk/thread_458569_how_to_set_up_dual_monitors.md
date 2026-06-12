---
title: "how to set up dual monitors?"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by raymond1234 on 2007-05-29
I am using a dell 600m inspiron notebook any one know what I need  to do to enable dual monitor support 

thanks!

---

### Post by guernicaaa on 2007-05-29
What kind of video card does it have?  I know with NVIDIA (this is from my own experience, I've never used ATI) you have to install the latest NVIDIA driver, then in terminal type in ```
sudo nvidia-settings
``` and you should see two monitors, one probably grayed out.  click on that one and hit configure and then I prefer to use TwinView to span the desktop across both.  You'll have to search around the forums or wait for someone who is smartter than me to reply about ATI cards.

---

### Post by raymond1234 on 2007-05-29
**sorry I did not post enough info the first time I guess I may have to re post this one**


01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 01be
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at fc000000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by Rocket2DMn on 2007-06-03
I spent a lot of time researching this problem on forums because I have the same model laptop and the same issue.  In the end, I believe this is the case:
   The ATI RADEON MOBILITY 9000 and other cards of the same generation are no longer supported by ATI, and since the upgrade to Feisty, the support for dual head (esp. using BigDesktop which seemed to be the way to go) has been lost.  We are pretty much out of luck, unless somebody fixes the problem in the future.
However, all is not lost as Beryl has proven to be a good alternative.
I followed this guide to setting up Beryl: [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") and it is working well for me.  Some people have had issues with the resolution, so I pointed them to this guide as well.

Sorry 'bout the dual-head, I really wish we could, too...

---

