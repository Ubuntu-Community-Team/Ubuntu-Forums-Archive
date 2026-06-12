---
title: "adding printer/scanner to xsane?"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-01-25
Hi,
I recently succesfully installed the Brother mfc6800 on Ubuntu 7.10. It prints great from all my applications. I even wrote a how-to. It's in the "hardware and laptops" section. Strange cause this is a Desktop but that's where the moderators chose to put it.

Anyway, my problem is that xsane defaults to the Haupage tv tuner card and doesn't recognise either of the two printer/scanners I have installed right now. How do I add a scanner to xsane?

I've tried editing one of the xsane conf files, changing the usb vendor ID as I read in some other posts and this does nothing. I'm not sure if I use the add printer under the copy tab in xsane or load device settings if that would work, but either way I don't know what the command would be for the add printer or where divice settings would be for loading divice settings.

I have installed sane, libsane, sane-utils, like other posts say. I don't think brother is supported in xsane, so is there a work around or another app that will work with it?

Thanks

---

### Post by AgentZ86 on 2008-01-27
> **iansane said:**
> Hi,
I recently succesfully installed the Brother mfc6800 on Ubuntu 7.10. It prints great from all my applications. I even wrote a how-to. It's in the "hardware and laptops" section. Strange cause this is a Desktop but that's where the moderators chose to put it.

Anyway, my problem is that xsane defaults to the Haupage tv tuner card and doesn't recognise either of the two printer/scanners I have installed right now. How do I add a scanner to xsane?

I've tried editing one of the xsane conf files, changing the usb vendor ID as I read in some other posts and this does nothing. I'm not sure if I use the add printer under the copy tab in xsane or load device settings if that would work, but either way I don't know what the command would be for the add printer or where divice settings would be for loading divice settings.

I have installed sane, libsane, sane-utils, like other posts say. I don't think brother is supported in xsane, so is there a work around or another app that will work with it?

Thanks

Yes it works with Xsane, however depending on your model etc. the install instructions for the scanner could vary.

I've installed my MFC-240C like so:
See this post I'm working on some details regarding using the scan key tool as regular user, and xsane as well, but anyhow I've put together some basic info and I'll hash out the full instructions once I get it completely figured out as far as running the xsane as regular user I currently can run xsane as root using the brother install instructions with a few minor modifictations.

See this other post:

[http://ubuntuforums.org/showthread.php?t=675684](http://ubuntuforums.org/showthread.php?t=675684)

should be number 13 regarding the scanner stuff that I have so far.

I hope this helps

---

