---
title: "How to install Nvidia driver without envy"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Dapman01 on 2007-10-19
does anyone know how to install the nvidia drivers without envy

---

### Post by Dapman01 on 2007-10-19
bump

---

### Post by 5-HT on 2007-10-19
You can either install the appropriate nvidia packages in the repos (easiest/quickest/most 'ubuntu way'), or build the module from the package provided on nvidia's site (only really needed if you want a newer version than available in the repos or you're rolling your own kernel). There are step-by-step instructions on nvidia's site for the latter. 
cheers,

---

### Post by Wiebelhaus on 2007-10-19
Restricted driver installation functon worked perfect for me.

---

### Post by eyemou on 2007-10-19
Have you tried installing and running the package 'restricted-manager'? 

I did this last night, and it worked like a charm, more or less*. I just ran it, w/sudo (well, kdesu), and it displayed my adapter, with an empty checkbox marked "enable". I ticked the box, and the manager proceeded to download and install the proper driver.

Just make sure to make a backup copy of your /etc/X11/xorg.conf file, in case you need to restore it.

As a disclaimer, this is only my experience. I cannot claim to be a Linux hardware guru by a longshot... I'll admit, I was a bit nervous after reading all of the video-related horror stories, and thus immensely relieved when it worked.

** = I had to adjust the horizontal position on my monitor very slightly, and had to reset my refresh rate via the 'nvidia-settings' tool, as the KDE display manager was only allowing me 57hz...*

---

### Post by PPAAUULL on 2007-10-19
Ya I would suggest the "Restricted Driver" function in the menus. It works perfectly for nvidia cards.

---

### Post by Dapman01 on 2007-10-19
> **PPAAUULL said:**
> Ya I would suggest the "Restricted Driver" function in the menus. It works perfectly for nvidia cards.

I did that and it keeps breaking my ubuntu

---

### Post by PmDematagoda on 2007-10-19
Then you may be better off doing it the manual way.

1) Download the Linux driver from the Nvidia website. The installation instructions are given there as well.

2) Reconfigure your X-server with:-

```
sudo dpkg-reconfigure xserver-xorg
```

Then see if you can get it running.

---

### Post by bruce89 on 2007-10-19
```
sudo aptitude install nvidia-glx
sudo nvidia-glx-config enable
```

---

### Post by JohnSGruber on 2007-10-19
> **Dapman01 said:**
> I did that and it keeps breaking my ubuntu

In what way is Ubuntu broken for you? What isn't working?

---

