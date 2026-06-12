---
title: "Building custom drivers for a mac keyboard and trackpad with a non-Mac laptop"
date: 2013-04-21
forum: Apple Hardware Users
---

### Post by nikomatsakis on 2013-04-21
Summary:

Can anyone point me to advice on building and installing a custom hid_apple module and a custom synaptics driver? I have some modifications I'd like to do to the source to make a mac keyboard/trackpad integrate better. (Thorough description below in case there is a better alternative)

Details:

I am trying to use a bluetooth Apple keyboard + magic trackpad with a Lenovo x230 laptop running Ubuntu 12.  Mostly I am happy but for two problems:

1. I want Option to be Super and Command to be Meta (this is the opposite of the default).

I am currently doing this via Xmodmap, but this means that the role of the Windows and Alt key on the built-in keyboard are reversed. The best solution seems to be the patch found here:

    [https://patchwork.kernel.org/patch/10259/](https://patchwork.kernel.org/patch/10259/)

But as far as I can tell this patch is not available in my driver.

2. I want the click-and-drag gesture to be activated with a different key

The click-and-drag gesture is a reasonable replacement for the Mac's three-finger-drag (which accomplished the same thing, basically).  In fact, I prefer the click-and-drag gesture, at least with LockedDrag=1.  However, I find that it gets confused with a normal click far too often for my taste.  Perhaps I just need to fine-tune the timeouts, but what I would prefer is to *initiate* the click-and-drag gesture with a different button.  There doesn't seem to be an option for this but I imagine it wouldn't be too hard to patch the source and add on.

Any advice on building custom drivers or (better yet...) other solutions that don't require such drastic steps would be most appreciated!


thanks,
Niko

---

