---
title: "Nvidia drivers install"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by jmasgalas on 2007-05-29
Can someone let me know where I could find a guide as to how to install the nvidia drivers in a way that I will not have to reinstall them after every kernel update? Is there such a way?

---

### Post by taurus on 2007-05-29
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by jmasgalas on 2007-05-29
So should I uninstall the nvidia drivers. then go into the restricted drivers manager and enable them? Or do I need to uninstall. Reinstall form the Synaptic Package manager and then enable them? Sorry about the confusion. I followed a guide that installed the drivers fine but with the kernel update yesterday everything got screwed. I can boot into the old kernel but the only way to boot into the new kernel is to uninstall the nvidia drivers. Reinstalling them following the directions I used before does not work.

---

### Post by Blender on 2007-05-29
Are you talking about the nvidia driver package (the run file)? You have to uninstal it, **nvidia-installer --uninstall**, I think.

---

### Post by jmasgalas on 2007-05-29
No I used method 1 from [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html). When the kernel update came it bonked everything. I just can't see why I cannot seem to find an install that will not go bonkers with what should be a routine update. I am new to ubuntu and loved it until this!

---

### Post by Ti317 on 2008-02-28
I got the message that I need to quit X server to install the "run" package. I killled the service and it still won't install. Now I cannot get it to boot into anything but command line. Anyone know how to get the Graphic logon back?
25 years of DOS, Windows in all its iterations and even UNIX, have never been this frustrating. At least UNIX is compiled for the hardware being used.

---

### Post by Ti317 on 2008-02-28
The link helped me solve my gdm problem. Still working on getting the drivers to work. Thanks

---

### Post by keenboy on 2008-02-28
There is an application called envy which is designed to aid the installation of nvidia and ati drivers.

---

### Post by bumanie on 2008-02-28
ctrl-alt-F7 should get you back into gui.
However to install the .run file, you will have do that via command line in console mode. It was the only way I could get a legacy driver operating in gutsy gibbon. It won't sort out your problems with kernel upgrades, but there probably won't be anymore kernel upgrades with Hardy Heron only 6-7 weeks away.
_Method._
Stopr xserver ctrl-alt-F1
enter username and password
> Sudo /etc/init.d/gdm stop --> hit enter
> sudo cd ~/Desktop --> hit enter [if the file is not on your desktop, change /Desktop to the path your file is located]
> sudo sh NVIDIA-Linux-x86-96.43.05-pkg1.run --> hit enter [substitute the run file number 96.43.05 for your file number, if it is different]
> sudo /etc/init.d/gdm start --> hit enter
If gui doesn't start either sudo reboot or try ctrl-alt-F7
Hope this helps.

---

