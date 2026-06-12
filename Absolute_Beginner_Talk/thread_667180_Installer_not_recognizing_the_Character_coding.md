---
title: "Installer not recognizing the Character coding"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by crazyeye on 2008-01-14
Alright, On basically anything I make an attempt on installing I could never install.

I can download everything perfectly well but when I go to open the file to install I get this

[http://i7.tinypic.com/8admmo7.png](http://i7.tinypic.com/8admmo7.png)

can someone please help me with this.

I cannot watch flash videos until this problem is resolved and It is annoying.

---

### Post by jken146 on 2008-01-14
That's not the easiest way to install things.  [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) might be worth looking at.

---

### Post by erginemr on 2008-01-14
Hello,

Apparently you are trying to install the driver for NVIDIA graphics card from the binary installer package you have downloaded from the NVIDIA web site. Speaking of which, what is your graphics card model?

Beware though, you should try to install your graphics card driver from within Ubuntu repositories (by using Main Menu -> Administration -> Synaptic Package Manager or better off, by following Main Menu -> Administration -> Restricted Drivers Manager) 

Apart from the fact that installing from an NVIDIA-*.run package is not so easy, the NVIDIA installer creates more problems than solutions. I know that because I did that before and ran into trouble (the X window refused to open) after a kernel update via Update Manager. So, I'd say, stay away from it.

Do you receive any feedback when you run "Restricted Drivers Manager" above? If not, you may try installing nvidia-glx-new from under Synaptic. First, backup your original xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
```
and after installing the binary package with:
```
sudo aptitude install nvidia-glx-new
```
make sure that your graphics driver has been configured correctly by issuing:
```
gksudo nvidia-xconfig
```
and changing the settings accordingly. 

Restart the X server by issuing Ctrl+Alt+BackSpace. You should now see a sleek NVIDIA logo.

You can also check that; if your binary NVIDIA driver has been installed correctly, the following config file:
```
less /etc/X11/xorg.conf
```
should have a line that says:
```
Driver    "nvidia"
```
instead of the default open-source equivalent:
```
Driver    "nv"
```

and the following command:
```
glxinfo | grep rendering
```
should yield:
```
Direct Rendering: Yes
```

This will make sure that the binary NVIDIA driver is in use and the 3D has been enabled.

Only if you cannot install NVIDIA, should you attempt to install it from the web package you have downloaded. We can discuss more if that happens...

---

