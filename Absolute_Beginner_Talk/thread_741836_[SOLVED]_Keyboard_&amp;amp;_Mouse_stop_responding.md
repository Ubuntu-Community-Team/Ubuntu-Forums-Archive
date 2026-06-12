---
title: "[SOLVED] Keyboard &amp;amp; Mouse stop responding"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Stunts on 2008-04-01
Hello all!
I'm having this ackward problem:
When I'm playing Neverwinter Nights, my mouse and keyboard both stop responding after something like 45minutes. The only thing I can do to get out of this situation is press the power button for 4 seconds to reboot. The games keeps running, the internet connection remains active, the rest of the OS keeps running fine. I just can't input any commands into it. Even tried to get to tty 1-6 but the keyboard doesn't even respond to that.
I forgot to check whether the caps lock lights can be turned on and off... 
This only started happening a few days ago. The only system change I have made is an install of the latest Nvidia drivers using Envy. 
It seems farfetched that the display drivers are causing a keyboard/mouse crash, but not so much that I didn't think of it myself...
BTW, neither the USB mouse nor the touchpad work when this happens.
The graphics card is an Nvidia 8600 M GT with 512Mb. I know there were some issues with this card and windows drivers, but they were related with the cooling fan not stopping...
Anybody got any ideas? Because I'm also not sure how to revert to the older drivers, since they were installed with Envy.

Thanks in advance!

---

### Post by mick8985 on 2008-04-01
The keyboard and mouse are directly part of the xserver, so it is entirely likely that the keyboard and mouse will stop working if your graphics driver causes the xserver to crash. I would advise using the packaged nvidia drivers from the repositories. Why exactly did you decide to use envy? probably reading too much phoronix :p

---

### Post by Stunts on 2008-04-01
Well, that does sort of confirms my suspicions.
I use Envy because of the Nvidia settings manager - tough I can live without that.
So if I just use Envy's driver uninstall option, will I be able to use the repros' drivers again?
Thanks for your help!

---

### Post by mick8985 on 2008-04-01
Yeah it will work fine, I know its annoying how they make it so the nvidia-settings package conflicts with the nvidia-driver package isn't it? I don't really understand why they did that in gutsy, its something the packagers  add to the settings in the deb package before they build it. Fortunately in Hardy they seem to have removed the conflict.

---

### Post by Stunts on 2008-04-01
Ok, so I uninstalled the Nvidia drivers with Envy. That went well.
I restarted, and Ubuntu booted fine, wich is good.
Compiz was also gone, but I expected that due to having no Nvidia driver installed.
Then I installed the resticted drivers from the repros (Had to change my source, since the repro I was using was giving me a 404 not found error).
Sencond restart and... Owo, jerky X and no Compiz?
I'll try to reinstall compiz and see what happens...
Expect another post soon.

---

### Post by Stunts on 2008-04-01
Ok, so before reinstalling compiz, I tried running in a terminal:```

francisco@MegalaptopII:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

and what I saw was not pretty...
Any tips?

Update:
I checked the Restricted drivers manager and I found that altough the driver is enabled, it says "Not in use".
Humm... Maybe something with the xorg.conf?
I'll check it out next....

---

### Post by mick8985 on 2008-04-01
try lsmod | grep "nvidia" you should get
```
michael@michael-laptop:~$ lsmod | grep "nvidia"
nvidia               8858052  36 
i2c_core               28544  1 nvidia

```

If you don't try sudo modprobe nvidia

---

### Post by Stunts on 2008-04-01
When I try what you suggested:
```
francisco@MegalaptopII:~$ sudo lsmod | grep "nvidia"
francisco@MegalaptopII:~$ sudo modprobe nvidia
FATAL: Could not open '/lib/modules/2.6.22-14-generic/nvidia/nvidia.ko': No such file or directory
francisco@MegalaptopII:~$ 
```

OK, i'm starting to thik this is somewhat messed up.
When i try to do:
sudo dpkg-reconfigure -phigh xserver-xorg I get:
```

xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080401175702
francisco@MegalaptopII:~$ 

```

Darn...

---

### Post by mick8985 on 2008-04-01
Alright, do the following, 

```
sudo apt-get install nvidia-glx-new
```

Then edit the xorg.conf, may aswell restore from your backup, because your mouse and keyboard may not be configured properly after your ran the dkpg-reconfigure, and there might be some other modules related to desktop effects not added.

```
gksu gedit /etc/X11/xorg.conf.20080401175702
```

now look for the Device section and change

```
 Driver          "nv" 
```

to

```
 Driver          "nvidia"
```

go to save as and replace the xorg.conf, now restart,

when it restarts

sudo lsmod | grep "nvidia"

should show the nvidia module is loaded

Hopefully :)

---

### Post by Stunts on 2008-04-01
It's ALIVE!
Thank you!
Worked like a charm!
I'll mark the thread solved!
Once again, thank you for your help!
I also feel I have learned a bit more about xserver configuration.

---

### Post by mick8985 on 2008-04-01
NP, gutsy spoils people sometimes with its easiness, its good to break it once in a while.

---

