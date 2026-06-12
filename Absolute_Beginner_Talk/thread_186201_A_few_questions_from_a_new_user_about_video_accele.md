---
title: "A few questions from a new user about video acceleration"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by King Blah on 2006-06-01
Hi! I'm downloading Kubuntu at the moment (x86) for my computer and am a bit confused about video acceleration.

Firstly, I have an ATi x800 Pro, will I get 3d acceleration automatically after installing or do i have to manually install drivers? I've had linux installations in the past (i'm a complete newbie still!) where I just have never got the ATi drivers to work.

Secondly, what is the difference between "fglrx" and ati drivers? Are they the same thing? I've heard people talk about them on these forums and if I want to update my video card drivers on linux which do i use?

Thanks!

---

### Post by dbd on 2006-06-01
To get proper 3d acceleration it is necessary to install some drivers, but don't worry, it is nice and easy, simply done by copying and pasting a couple of commands into the command line. See:
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

"fglrx" drivers a propriety drivers made by ATI, "ati" drivers are open source drivers that are automatically installed, and unfortunatly not as good for proper 3d acceleration stuff (so if your want to play graphically intensive games or use gl screensavers then you'll need them). So your probably will want to install the ati ones, see the link above.

Good luck :)

---

### Post by Rackerz on 2006-06-01
Well 'fglrx' as far as I know gives you 3d Acceleration. To install it just open up the Synaptic Package Manager and search for 'fglrx' and install it. 

After doing that you will need to edit your xorg.conf.

First of all you will need to backup your orginial xorg.conf, do this by:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then open up your xorg.conf with gedit;
```
sudo gedit /etc/X11/xorg.conf
```

Scroll down to where it says;
```
Section "Device"
```

Change
```
Driver   "ati"
```

To

```
Driver   "fglrx"
```

---

### Post by King Blah on 2006-06-02
Thanks! I tried that and it worked! First time I've had 3D acceleration working in linux, great!

Another thing, I couldn't find "Synaptic Package Manager" anywhere, instead I had to use something called Adept. Is that the same thing?

Thanks.

(By the way, I am in kubuntu if that makes a difference)

---

### Post by dbd on 2006-06-02
Yeah, "Adept" is the Kubuntu equivalent of "Synaptic Package Manage". It is pretty much the same thing, they look quite different but do the same basic jobs.

---

