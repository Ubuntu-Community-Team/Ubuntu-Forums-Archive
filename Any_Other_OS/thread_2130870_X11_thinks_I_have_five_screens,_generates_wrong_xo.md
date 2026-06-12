---
title: "X11 thinks I have five screens, generates wrong xorg.conf"
date: 2013-03-30
forum: Any Other OS
---

### Post by mszegedy on 2013-03-30
I've started having problems with my window manager. (My OS is LM 13 MATE 64-bit. My hardware is a mid-range Lenovo Thinkpad T430; it's supposed to use mostly integrated graphics, until I start up something graphics-intensive, at which point it switches seamlessly to my Nvidia NVS 5400 discrete graphics card.) Whenever X11 generates an xorg.conf, it generates for some sort of confusing five-screen layout that I don't have. Then, when my computer starts starting up, when it tries to load the GUI, it freezes, and it gives me either a completely black screen or a single frozen underline cursor at the top left. Then I have to restart it and try again. I've made a temporary fix by copying /etc/X11 from my LiveUSB installer to /etc/X11 on my disk, booting up in recovery mode, going to root prompt, remounting / as rw, and purging xserver-xorg-video-intel, -nouveau, and -all, and then booting up in recovery mode again. This enables me to log in with a slightly buggy GUI, from which I reinstall the drivers. When I go to "Monitors" in the Control Center, it tells me that my monitor is "Unknown". When I reboot, it makes a new xorg.conf with the faulty five-monitor setup, and is broken again, so I have to repeat everything. How do I make X11 recognize my (1-monitor) setup again? I've tried adding [glasen's ppa]("https://launchpad.net/~glasen/+archive/intel-driver") for Intel cards, it broke just the same.

EDIT: Here is my xorg.conf: [http://pastebin.com/PRDCbZ2k](http://pastebin.com/PRDCbZ2k)

EDIT 2: I've solved this by installing the package "nvidia-settings". (Not before reinstalling my OS in vain, though. :\)

---

