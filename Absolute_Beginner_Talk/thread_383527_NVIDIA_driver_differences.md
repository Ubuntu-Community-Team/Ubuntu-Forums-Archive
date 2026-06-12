---
title: "NVIDIA driver differences"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by civilmonkey on 2007-03-13
Im new to Ubunto but liking it already.  I'm going to install the latest drivers for my Nvidia 7600GT graphics card and had a few quick questions.  I'm running 6.10 using Gnome.

The unofficial Ubuntoguide ([http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)) says to install Nvidia drivers with:
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

Since I'm used to Windows, I went right ahead and downloaded the latest linux x86 nvidia driver (v9755) and figured I'd just run install the package with the sh command.

What is the difference, and is there a location to look up exactly what 'nvidia-glx' is so I can try and answer these questions myself in the future :) 

Thanks.

---

### Post by overdrank on 2007-03-13
> **civilmonkey said:**
> Im new to Ubunto but liking it already.  I'm going to install the latest drivers for my Nvidia 7600GT graphics card and had a few quick questions.  I'm running 6.10 using Gnome.

The unofficial Ubuntoguide ([http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)) says to install Nvidia drivers with:
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

Since I'm used to Windows, I went right ahead and downloaded the latest linux x86 nvidia driver (v9755) and figured I'd just run install the package with the sh command.

What is the difference, and is there a location to look up exactly what 'nvidia-glx' is so I can try and answer these questions myself in the future :) 

Thanks.

Hi and welcome, I reinstalled my ati drivers yesterday and used this link
[http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/](http://discoverx.wordpress.com/2007/03/12/a-fast-way-to-install-ati-and-nvidia-drivers-in-ubuntu/)
It works with nvidia and ati drivers. I tried it and it installs the lastest drivers and configures your x for you. As for the differnt drivers I cannot help with that question  but to goggle search and see what you can find. Hope this helps and good luck!

---

### Post by russell.h on 2007-03-13
They're essentially the same driver, although the one on nvidia's site might be newer (I've lost track - it shouldn't really matter).

But (and I'm a little vague on this myself) you sometimes/always have to build a kernel module or somesuch when you install using the nvidia provided driver, whereas if you install nvidia-glx from the repositories it comes with everything all ready to go. Also if you get the one from the repositories it will show up in the various package management systems, and is less likely to get broken (dumping you to the command line) when certain updates come along.

I would go with ```
sudo aptititude install nvidia-glx
```
(or you can use apt-get in place of aptitude, it won't matter that much).

---

### Post by civilmonkey on 2007-03-13
Sounds like using the Ubuntu repository is safer for new guys like me.  I'll go for that.

---

### Post by tipsqueal on 2007-03-13
I've gotten the drivers for my 7600 GT through Nvidia. I like them better because in the system tools section there is an Nvidia configuration program that lets you see the options on your GFX card, with the official Nvidia drivers (not the Ubuntu repository) it is much better and has more options, one of the options I like is that it will make an xorg.conf file for you, which I did. The configuration file it spits out is much cleaner and actually solved some issues I was having. I wouldn't suggest letting the program write over your xorg.conf. I would suggest saving it to your desktop, reading it, then make any edits you want to it, then copying it over, but only after you back up your original one.

---

### Post by Outrunner on 2007-03-13
The 97.55 drivers are for the new G80 series cards as far as I know, so you shouldn't use them with a 7600. Just use synaptic to install your drivers.

---

### Post by civilmonkey on 2007-03-13
> **tipsqueal said:**
> I've gotten the drivers for my 7600 GT through Nvidia. I like them better because in the system tools section there is an Nvidia configuration program that lets you see the options on your GFX card, with the official Nvidia drivers (not the Ubuntu repository) it is much better and has more options, one of the options I like is that it will make an xorg.conf file for you, which I did. The configuration file it spits out is much cleaner and actually solved some issues I was having. I wouldn't suggest letting the program write over your xorg.conf. I would suggest saving it to your desktop, reading it, then make any edits you want to it, then copying it over, but only after you back up your original one.

The Nvidia driver readme states that I might need to compile and install platform specific kernel if one does not exist.  Will I need to do this for a AMD 32 bit processer and Ubunto 6.10?

---

### Post by Bachstelze on 2007-03-13
> **Outrunner said:**
> The 97.55 drivers are for the new G80 series cards as far as I know, so you shouldn't use them with a 7600. Just use synaptic to install your drivers.

Just because support for the newest cards was added doesn't mean they won't work with other ones, too. I'm currently running the 97.55 installed with the nvidia package on my Go 7600 without any problem - not in Ubuntu, though.

---

