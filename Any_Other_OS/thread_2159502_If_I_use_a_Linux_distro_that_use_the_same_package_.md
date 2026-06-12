---
title: "If I use a Linux distro that use the same package type can I use driver from another?"
date: 2013-07-03
forum: Any Other OS
---

### Post by JOSEISCOOL on 2013-07-03
Okay, so I'm looking for drivers for my laptop and I went to the website and the only drivers it really lists are for Ubuntu and for Fedora.
I want to use OpenSUSE, and it uses the .rpm package format just like Fedora, would it be safe to install drivers for Fedora on OpenSUSE?

Thanks for any help.

---

### Post by oldos2er on 2013-07-03
Moved to Other OS/Distro Support.

---

### Post by AdamWill on 2013-07-03
> **JOSEISCOOL said:**
> Okay, so I'm looking for drivers for my laptop and I went to the website and the only drivers it really lists are for Ubuntu and for Fedora.
I want to use OpenSUSE, and it uses the .rpm package format just like Fedora, would it be safe to install drivers for Fedora on OpenSUSE?

Thanks for any help.

No, not necessarily (in fact it's fairly unlikely). The package format is not as important as whether the contents of the package are actually compatible with your distribution. OpenSUSE and Fedora are fairly different; packages for either are not guaranteed to work on the other, and hardware drivers for either are fairly _unlikely_ to work on the other.

Having said that, it looks like you may be going about things a bit wrong, or rather, in the Windows way. 'Looking for drivers for your system' is kind of a Windows thing: Linux does not exactly work that way. What we usually aim for is simply that all the drivers for your hardware are already included in the distribution, and everything should just work fine 'out of the box'. If you want to try OpenSUSE I'd recommend you simply boot up an OpenSUSE live image and check that all your hardware works.

You only really need to go 'looking for drivers' if some bit of your hardware just isn't working, and even then, rather than go to the manufacturer's site, it would be better to post details about what's not working in the distro's official forums and wait for some help there; it's often the case that what you need is available in some official or semi-official way for the distro, rather than trying to get it from the manufacturer.

Many people prefer to use the NVIDIA or AMD proprietary graphics drivers for their graphics hardware rather than the open source ones, as they tend to have better 3D performance and power management. But still, if you want to do this, for any major distribution, there will be a 'standard procedure' for installing those drivers, you certainly shouldn't try and use packages from any other distribution. Just look in the forums for the distribution and you will almost certainly find a sticky thread with detailed instructions.

Good luck!

---

