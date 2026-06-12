---
title: "Edgy growth pains"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Pathos_ on 2007-01-24
I'm not exactly a newcomer to linux or ubuntu but I'll put my rants here anyway.

smbfs not installed by default: Why ? I spent hours trying to get smbfs and cifs to work to mount network partition and they just gave me unexplained numeric errors (-22 which is EINVAL after looking at the code). Not ubuntu's fault that cifs is so unfriendly but...yeah that was a pain but is now working perfectly.

Key bindings: Binding Ctrl+shift+F11 to play/pause in the Keyboard Shortcuts dialog did some odd things. First off it would discard the Ctrl+Shift modifiers and bind XFree86play or something like that to F11's keycorde. If you then made another shortcut to be Ctrl+F11 it would appear Ctrl+XFree86Play. Play would only need you to press F11 and any program where F11 was used to fullscreen wouldn't. Odd but I just disabled the multimedia shortcuts and it fixed itself after a restart.

SMB:// is rather broken: Can't play any media over it, is this a known design limitation ?. Which is why I mount with cifs.

Hardware support: yeah the motherboard GA-965P-S3 is partially supported. Ethernet doesn't work without a hack and lm-sensors needs a kernel patch which I haven't done yet.


Other than that, Ubuntu Edgy is absolutely gorgeous and wonderful to work with and administer...once your've run automatix :)

---

