---
title: "karmic on MacbookPro5,2: no proprietary hardware drivers"
date: 2010-02-27
forum: Apple Hardware Users
---

### Post by extralooping on 2010-02-27
i finally got karmic installed on my MacbookPro5.2, but when trying to install the hardware drivers for wireless and gfx, it just shows an empty list, saying no proprietary drivers are used... please help

---

### Post by inclusivedisjunction on 2010-02-27
Your question is kind of vague. If you have not installed any proprietary drivers, then obviously none are in use. Or are you saying that no proprietary drivers are presented to you and you expected there to be?

---

### Post by extralooping on 2010-02-27
> Or are you saying that no proprietary drivers are presented to you and you expected there to be?
exactly.. according to the instructions in the wiki and in the forum, there should be broadcom STA and nvidia drivers

---

### Post by howefield on 2010-02-27
You say you have just finished installing, have you updated your package lists yet ?

Open a terminal and type

```
sudo apt-get update
```

Or load Synaptic Package Manager and press the reload button.

Then try your Hardware Drivers again.

---

### Post by inclusivedisjunction on 2010-02-27
Of course, that will only work if he has a working internet connection, such as via Ethernet.

I actually almost never use the proprietary drivers manager. While it may make them easier to install / remove, the NVIDIA drivers it provides are always several versions behind the latest NVIDIA release, so I usually download the latest package from NVIDIA's site. The wireless driver should be installable by installing the bcmwl-kernel-source package.

[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

---

### Post by linuxopjemac on 2010-02-27
[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)
post#1

then 
```
sudo apt-get update
sudo apt-get upgrade
```

then look under hardware again if you find nvidia driver

otherwise
```

sudo apt-get install nvidia-glx-185
```

---

### Post by extralooping on 2010-02-27
i just figured (via this thread: [http://ubuntuforums.org/showthread.php?t=1368699&highlight=proprietary+hardware+drivers](http://ubuntuforums.org/showthread.php?t=1368699&highlight=proprietary+hardware+drivers)) how to get broadcom drivers from the livecd, and can now find the nvdia drivers with the package manager!

thanks a lot for your help

---

