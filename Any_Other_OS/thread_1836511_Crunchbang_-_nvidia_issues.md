---
title: "Crunchbang - nvidia issues?"
date: 2011-08-31
forum: Any Other OS
---

### Post by mips on 2011-08-31
I have read and applied:
[http://crunchbanglinux.org/forums/topic/14856/how-to-survive-backports-upgrades-using-apt-preferences/?login=1](http://crunchbanglinux.org/forums/topic/14856/how-to-survive-backports-upgrades-using-apt-preferences/?login=1)
[http://crunchbanglinux.org/forums/topic/11900/how-to-nvidia-drivers-in-or-debian-stable/](http://crunchbanglinux.org/forums/topic/11900/how-to-nvidia-drivers-in-or-debian-stable/)

Did a fresh xfce 64bit statler install this morning. Enabled backports and followed the info in the above two links.

```


*user@host*:~$ sudo apt-get install nvidia-kernel-dkms nvidia-glx nvidia-xconfig nvidia-settings nvidia-vdpau-driver vdpau-va-driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vdpau-va-driver is already the newest version.
nvidia-settings is already the newest version.
nvidia-xconfig is already the newest version.
nvidia-kernel-dkms is already the newest version.
nvidia-vdpau-driver is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-glx : Depends: xorg-video-abi-6.0 or
                       xserver-xorg-core (< 2:1.7.7) but it is not going to be installed
E: Broken packages

```

Xorg.0.log
```

[  4655.472] (II) LoadModule: "nvidia"
[  4655.472] (WW) Warning, couldn't open module nvidia
[  4655.472] (II) UnloadModule: "nvidia"
[  4655.472] (II) Unloading nvidia
[  4655.472] (EE) Failed to load module "nvidia" (module does not exist, 0)
[  4655.472] (EE) No drivers available.
[  4655.472] 
Fatal server error:
[  4655.472] no screens found
[  4655.473] 
```

So how do I fix this and get my nvidia drivers installed?

---

