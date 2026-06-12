---
title: "No Live Stream from Internet"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by ProPilot on 2005-10-02
Get following error:
<<Totem could not play 'fd://0' - There were no decoders found to handle the stream, you might need to install the corresponding plugins.>>

lspci | grep audio gives:
(stuff) ALI Corp M5451 PCI AC-Link Controller Audio Device.

Applications- Sound&Video-Volume Control-Device gives ALI 5451 (alsa mixer)

What do I have to do to get streaming sound running?

Thanks
Tom

---

### Post by Martin Witte on 2005-10-02
Install appropriate codecs. I used the program mentioned here [http://ubuntuforums.org/showthread.php?t=64629](http://ubuntuforums.org/showthread.php?t=64629) to do that for me - pay attention to the version for hoary and for breezy a version is available.

---

### Post by ProPilot on 2005-10-02
Thanks. Did it. Ran it.

Still no live streaming - no longer get the error I posted above.

Any more suggestions.

Thanks
Tom

---

### Post by poofyhairguy on 2005-10-02
What sort of stream is it? I find that Realplayer works the best.

[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer#head-59a79c66f6fef0a9350390de31797a457ed85cd8](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=RealPlayer#head-59a79c66f6fef0a9350390de31797a457ed85cd8)

I sometimes have problems with Windows Media streams (go figure, the first word gives away why).

---

### Post by poofyhairguy on 2005-10-02
[QUOTE=ProPilot]Thanks. Did it. Ran it.

Still no live streaming - no longer get the error I posted above.

Any more suggestions.

Thanks
Tom[/QUOTE]


Also try this command:

> sudo apt-get install totem-xine

and try again

---

