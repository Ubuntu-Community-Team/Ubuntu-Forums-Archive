---
title: "macbook 5,1 trackpad configuration"
date: 2009-04-19
forum: Apple Hardware Users
---

### Post by knaveofdiamonds on 2009-04-19
Hi,

I have installed Intrepid on my macbook (5,1), but am having some issues getting the trackpad working as I would like. I have installed most of the packages from the mactel ppa repo, including the bcm5974-dkms package, and followed the instructions for setting them up, although I'm not using the tap-to-click options.

My problem is that you cannot click to select a window and then drag it with a second finger - I guess it thinks you're trying to do a two-fingered scroll. I have tried changing the values of the options input.x11_options.VertTwoFingeredScroll and HorizTwoFingeredScroll from "1" to "0" (in /etc/hal/fdi/policy/11-x11-synaptics.fdi) but that had no effect.

Any suggestions? I'd rather have click-and-drag over other features (its pretty unusable otherwise), so I don't mind losing the two fingered scroll.

TIA,
Roland

---

### Post by cyberdork33 on 2009-04-19
This was reported and work was done to create a patch, but it has not be merged yet.

---

### Post by knaveofdiamonds on 2009-04-23
Hi,

Thanks for the response. I've tried searching launchpad for the patch, but couldn't find it - could you point me in its direction? Does the patch fix these configuration problems?

Thanks,
Roland

---

### Post by volanin on 2009-04-23
> **knaveofdiamonds said:**
> My problem is that you cannot click to select a window and then drag it with a second finger - I guess it thinks you're trying to do a two-fingered scroll.

If you have installed the xserver-xorg-input-synaptics from mactel-support, please remove it and use the original ubuntu package instead. Indeed, the package from mactel-support (patched by me), won't allow you to drag a window with a second finger, **because cursor movement is disabled while multiple fingers are touching the touchpad.**

It is disabled by design, because one of the reasons of the patch is to make the cursor more stable: It allows the users to easily press the button while having multiple fingers on the touchpad (using the clickfinger option), without the cursor dancing all around the screen.

The patch would be too intrusive if implemented otherwise, but maybe, I might simply disable this restriction if clickfinger is set to false. But please, test it with the original package before.

Thank you.

---

### Post by petersphilo on 2010-08-21
Hello,
i'm a newcomer to Ubuntu, so please forgive my ignorance..

I have a MacBookPro 5,2 and the exact same problem as described above.

Disabling xserver-xorg-input-synaptics did not help at all for me.
However, after reinstalling it, i installed a package called:

Pointing Devices

You can find it in the standard Ubuntu software search thingy; it provides sort of a solution (with quite a few side-effects).

indeed, turning on drag lock allows me to click-and-drag in almost all situations.
The only annoying side-effect is that i also have two-finger scrolling turned on, so every time i scroll, it starts selecting whatever is under my pointer as soon as it moves again...

Are there any news on this issue?
i guess i am running Lucid Lynx; it is 10.04.1 x64

Thank you!!
PS: really glad to finally try Ubuntu!:D

---

### Post by krolaw on 2011-02-12
Bug report can be found here: [https://bugs.launchpad.net/ubuntu/+bug/367399](https://bugs.launchpad.net/ubuntu/+bug/367399)

Please add info to it and/or vote for it.

Cheers.

---

