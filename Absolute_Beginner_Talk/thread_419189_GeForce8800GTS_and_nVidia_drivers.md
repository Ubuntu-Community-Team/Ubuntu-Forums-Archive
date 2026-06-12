---
title: "GeForce8800GTS and nVidia drivers"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by awesomepatrol on 2007-04-22
Hello all,

I recently installed Fiesty and through some editing of the xorg.conf file (described [here]("http://www.wahlau.org/samsung_225bw_with_xorg_on_ubuntu_linux")), I've been able to get 1680x1050 resolution working properly with the 'nv' driver and my Samsung 226bw.  Whenever I try to install the new nVidia drivers, however (which I suppose I need to use Beryl and some of the other eye candy), X refuses to start.  I've tried to install the drivers manually, using Envy, and using Automatix, and the result is always the same.  

Any suggestions?

Thanks

---

### Post by strider1551 on 2007-04-22
Well, I can't say I'm an expert myself, but I did get my relatively new nVidia card working with Beryl.  Have you at least done the following?

```
sudo apt-get install nvidia-glx
sudo gedit /etc/X11/xorg.conf
```

In the device section, make sure it reads
```
Driver          "nvidia"
```

---

### Post by overdrank on 2007-04-22
> **awesomepatrol said:**
> Hello all,

I recently installed Fiesty and through some editing of the xorg.conf file (described [here]("http://www.wahlau.org/samsung_225bw_with_xorg_on_ubuntu_linux")), I've been able to get 1680x1050 resolution working properly with the 'nv' driver and my Samsung 226bw.  Whenever I try to install the new nVidia drivers, however (which I suppose I need to use Beryl and some of the other eye candy), X refuses to start.  I've tried to install the drivers manually, using Envy, and using Automatix, and the result is always the same.  

Any suggestions?

Thanks

Hi maybe this thread will help 
[http://ubuntuforums.org/showthread.php?t=328379&highlight=GeForce8800GTS](http://ubuntuforums.org/showthread.php?t=328379&highlight=GeForce8800GTS)
but with feisty I am not sure, Good luck!

---

### Post by awesomepatrol on 2007-04-22
Thanks for the help so far; no dice yet, though.

I've installed the newest drivers available from nVidia.  To be clear, the 'nv' driver does work for me, but the proprietary 'nvidia' driver does not.  

I think the problem lies with the kernel compilation for the nVidia drivers.  

Has anyone successfully used the 'nvidia' driver with an 8800?

---

### Post by frodon on 2007-04-23
You need the latest drivers for this card, just install the "nvidia-glx-new" package and make sure that your xorg.conf use the nvidia driver and it should be good.

---

### Post by Terl on 2007-04-23
There are some very new drivers on the nvidia site.  Click the archive for the Linux versions and you will see listed a beta for the newest driver.  See the link:  [Driver 100.14.03]("http://www.nvidia.com/object/linux_display_archive.html").  You would have to uninstall what you have and install this manually.  Per the read-me's for this driver it adds more support for the newer cards.

---

### Post by frodon on 2007-04-23
You don't need to bother installing manually this nvidia drivers version (100.14.03.), the one in the repositories under nvidia-glx-new (version 1.0-9755) already offer 8800 series support and using them you won't have to re-install nvidia drivers on each kernel update. So except if you have a special need of the 100.14.03 nvidia drivers i advice you to use theone in the repositories.

---

### Post by xtreme35967 on 2007-04-23
I have the 7600GT and the  nvidia-glx-new worked for me with no problems. It is the only one that did work. I tried the original  nvidia-glx and I kept getting the blue x cannot load screen.

---

### Post by awesomepatrol on 2007-04-23
Thanks for the new responses.  

I had tried the new 100.14.03 drivers to no avail; similarly, the 9755 drivers did not work for me.  Perhaps I need to go through more elaborate procedures to uninstall all drivers beforehand; I'll check the nVidia readme on that, but I think that I ran all the correct commands upon installation.

The error that the log keeps giving me is "Cannot launch NVIDIA kernel; screens were found, but no working configuration"--that's not word for word, but it's the gist of it.

I've edited the xorg.conf to add the necessary modeline information for my monitor: could this be interfering with the nVidia driver for any reason?  Note that installing the drivers actually didn't work before I edited the modeline anyway....

---

### Post by Terl on 2007-04-23
Could you post your xorg.conf file here?  That would be helpful.

---

### Post by awesomepatrol on 2007-04-23
Yes, I'll have to do that later today, though, as I'm not currently at my linux PC.  I'll post it as soon as possible.  Thanks.

---

