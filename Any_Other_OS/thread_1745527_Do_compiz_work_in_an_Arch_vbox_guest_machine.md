---
title: "Do compiz work in an Arch vbox guest machine?"
date: 2011-05-01
forum: Any Other OS
---

### Post by LarsKongo on 2011-05-01
So I'm running Arch in VirtualBox 4.0.6 and a Windows 7 x64 host.

Ubuntu with compiz works just fine.
Arch with compiz just displays a white screen/or no window borders. (Guest additions are installed and 3D support is enabled.)
I don't get any errors when I run glxgears.

I've installed compiz-gtk and even the gtk window decorator. I've also imported the standard compiz settings from an Ubuntu maverick minimal install. 

When I run *compiz --replace* I don't get any errors, but all my window borders disappear. 

If I run *fusion-icon* my desktop gets completely white with a standard black cursor. All I can do is to switch tty and reboot the machine. Killing all compiz and then switching back to tty7 doesn't work.

If I run *compiz-manager* my desktop gets white, but switching tty and killing compiz do work. So I can get back to tty7 without any problems after that. (And do a metacity --replace because the borders doesn't display.)

---

