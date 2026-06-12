---
title: "Do I need to install NVIDIA Legacy drivers?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by Hishgraphics on 2007-03-10
I am wondering if I need to upgrade my video card driver.

Sometimes if I scroll a window too fast or change a picture file's brightness or contrast or saturation on GIMP the entire computer hangs. I can play avi video files, but if there's too many things happening onscreen it drops some frames.
 
When I typed [COLOR="DarkRed"]**lspci | grep VGA**[/COLOR] in Terminal I get:

```
01:00.0 VGA compatible controller: nVidia Corporation NV5 [Aladdin TNT2] (rev 20)
```

Based on [this thread (NVIDIA LIST of videocards supported through LEGACY DRIVER)](http://www.ubuntuforums.org/showthread.php?t=233241), should I install the legacy (propriety) Legacy driver? Or any other sort of driver even... I'm new to this, sorry.

```
sudo aptitude install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig linux-restricted-modules-`uname -r`
sudo nvidia-xconfig
```
Do I need to install the drivers as per the above code?

Thanks.

---

### Post by xopher on 2007-03-10
Installing the legacy driver might improve the performance, yes. So that's what I'd do too.

The only command you'll need to run for installing, though, is:

```
sudo apt-get install nvidia-glx-legacy
```
Then run the config-app, if you don't want to manualy do it. Apt-get will tke care of the needed dependencies. And since edgy, apt-get is starting to get as smart as aptitude too ;)

---

### Post by RomeReactor on 2007-03-10
Hi. I suggest installing:

```
sudo apt-get install nvidia-glx-legacy
```

and after the installation finishes:

```
sudo nvidia-glx-config enable
```

As per the instructions on Synaptic.

---

### Post by Hishgraphics on 2007-03-10
Awesome. Thanks guys.

It actually worked!

Scrolling windows are smoother now. And so does playing avi files. It especially slowed down during Stargate SG-1's opening credits because of all the graphics flying around onscreen. Now plays it smoothly as well.

This forum rocks.

Thanks again.

---

