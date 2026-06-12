---
title: "Want to use my computer without monitor"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Usta_AsH on 2008-02-15
Hello I don't have monitor. So I connected my desktop by using my T.V Output. I installed Ubuntu 7.10. I can open my pc. I can see Ubuntu logo after Ubuntu logo, my screen goes, I cannot see any login page. when I tried CTRL+ALT+F2 I can see ssh. So Is there any remote desktop program like VNC that I can install by using only that ssh page?

---

### Post by dstew on 2008-02-15
If you can see the Ubuntu logo, you should be able to configure your xserver to give you a graphical output on your TV. Try```
sudo dpkg-reconfigure xserver-xorg
```
Also, there is the package **xrandr** that you can install using synaptic. This gives more flexibility to the xserver when it comes to displaying TV. [Here]("http://www.joshgerdes.com/blog/2007/10/29/s-video-tv-out-with-ubuntu-710-on-dell-xps-m140-laptop/") is an example of someone using xrandr.

---

### Post by Usta_AsH on 2008-02-15
> **dstew said:**
> If you can see the Ubuntu logo, you should be able to configure your xserver to give you a graphical output on your TV. Try```
sudo dpkg-reconfigure xserver-xorg
```
Also, there is the package **xrandr** that you can install using synaptic. This gives more flexibility to the xserver when it comes to displaying TV. [Here]("http://www.joshgerdes.com/blog/2007/10/29/s-video-tv-out-with-ubuntu-710-on-dell-xps-m140-laptop/") is an example of someone using xrandr.

thanks I reconfigured and it is working on my tv now!

---

### Post by fatality_uk on 2008-02-15
> **Usta_AsH said:**
> thanks I reconfigured and it is working on my tv now!

Cool. Can you mark your thread as solved then Ash, cheers ;)

---

