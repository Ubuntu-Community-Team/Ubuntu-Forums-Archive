---
title: "Driver trouble."
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Zummy on 2008-03-04
I need a display driver for my Nvidia 8800 GT graphics/display card.  I found a link to download it on a Linux 32 bit system (which I have) from their main website. ([http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html))

After I download it and I go to install the site says to type in > sh NVIDIA-Linux-x86-169.12-pkg1.run

When I do I get:
> zummy@zummy-desktop:~$ sh NVIDIA-Linux-x86-169.12-pkg1.run
sh: Can't open NVIDIA-Linux-x86-169.12-pkg1.run
zummy@zummy-desktop:~$ 


Any help is appreciated! Thanks!

---

### Post by taurus on 2008-03-04
Are you sure NVIDIA-Linux-x86-169.12-pkg1.run is in your $HOME directory instead of ~/Desktop?

```
cd ~/Desktop
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-169.12-pkg1.run
```

---

### Post by billgoldberg on 2008-03-04
Get this program here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and install the driver that way.

It's easier

---

### Post by Zummy on 2008-03-04
Thanks for envy billgoldberg!!

It is installing right now.

Thanks taurus for letting me know its supposed to go in the /home/ directory first lol.

---

