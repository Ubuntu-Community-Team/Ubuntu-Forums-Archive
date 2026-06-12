---
title: "Someone please read this I need some help"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by brainslug on 2007-01-30
Hello everyone
I recently bought a HP pavilion dv6000, it has a nVidia Ge Force Go 7200
graphics card. I have tried installing both Fedora Core 6 and Ubuntu but
I still get the same problem and am about to give up on Linux. After both installs and after I reboot the Laptop both distros start to load but just before the GUI is about to load I get a blank black screen and nothing hapens anymore. I'm gesing there is a problem with linux recognizing my graphics
card or maybe I'm doing something wrong. Can anyone help me?

Thanks!

---

### Post by mikewhatever on 2007-01-30
Have you been able to run Ubuntu from the Live CD?

---

### Post by Shatrat on 2007-01-30
You might try installing the official nvidia drivers from command line.
If you print out the how-to I dont think it should be too difficult in recovery mode.
{edit}
also you could try editing your xorg.conf ```
nano /etc/X11/xorg.conf
```
and changing the driver in the device section from "nv" to "vesa"
And that might get you back to a limited graphical environment to easier install the nvidia blob drivers.

---

### Post by zeifertstc on 2007-01-30
> **Shatrat said:**
> You might try installing the official nvidia drivers from command line.
If you print out the how-to I dont think it should be too difficult in recovery mode.


```
 sudo apt-get install nvidia-glx
``` if you can get into a terminal or boot into terminal mode. 

For the most part, though, if you can get the graphical environment working, I'd recommend going with Automatix2 located at [http://www.getautomatix.com](http://www.getautomatix.com) and click on installation. Follow the directions for apt-get as it works the best out of everything and automatically resolves your dependencies for this particular package. The nvidia drivers work well if Automatix2 handles the process and you don't even really have to manipulate xorg.conf unless you're forced into it. My Geforce FX5200 didn't require any extra configuring after Automatix2 did it's thing.

Even if you get nvidia-glx and it works, I'd recommend getting Automatix2 to make sure that you have everything that you need.

---

### Post by seshomaru samma on 2007-01-30
To get into terminal mode press ctrl+alt+F1
then you can input the commands suggested by shatrat and zeifertstc

 But first ,please read [this page]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29") concerning your laptop model

---

### Post by Heerm on 2007-05-09
Ok, I've got the exact same problem, and i'm soon thinking of give up Linux - it just don't work :( If you guys cant help dough.. 

First;
I've tried changing the xorg.conf file.. Under "device" it sys "nv" and not "nvidia".. Ive also tried "vesa", but with no luck. 

I do however make it do boot up with the Live CD, if i set VGA to 1280x768x32. From here i've tried install automatix and install Nvidia drivers, but doesn't seem to work.. 

Neither can i get into terminal mode, because i dont get further than the "ubuntu loading" ..The "GRUB loader works fine though.. And I can sucsessfully boot up Vista, which is in the harddrive, but another partition. :)

Still I have this one black screen and I cant find an answer. Please, I beg you, take a look at my case and see if you come up with a solution?

Thanks in advance!

---

### Post by Heerm on 2007-05-27
Bump :)

---

### Post by hyper_ch on 2007-05-27
Plz use the next time a descriptive title!

---

