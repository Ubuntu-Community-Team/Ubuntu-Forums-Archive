---
title: "Display issues"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by SDREnate on 2006-06-14
I had this problem back when I installed Breezy, but I can't remember exactly how I fixed it..

I just did a fresh install of Dapper. Everything loads fine, but right when the login screen should be displayed, my screen becomes unreadable with weird colors and patterns. Also, when I exit recovery mode, it says "Cannot display this video mode" on the screen. 

I'm using a nvidia geforce 6800 gs video card. I've been trying to install the drivers from recovery mode by using ```
sudo apt-get install nvidia-glx
``` but it's not working. Do I need to enable multiverse and universe repositories? If so, how would I do this from recovery mode? sudo gedit /etc/apt/sources.list isn't working. Do I need to edit xorg.conf? Meh. Any help?

---

### Post by em0j on 2006-06-14
I myself had a display problem only on the grub splash screen. After the scrambled loading screen (black background with scrolling text) the gui login screen came up fine. Is this the problem you are having, if so I freakin fixed it.

---

### Post by nalmeth on 2006-06-14
[http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation](http://wiki.serios.net/wiki/Ubuntu_NVIDIA_proprietary_display_driver_installation)

---

