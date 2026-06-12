---
title: "Newbie NVIDIA Install help - GUI Crashes on startup"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by beaker on 2006-12-12
Hi all,

Have successfully installed 6.06 from The Official Ubuntu Book DVD, and resolved an issue with the Bootloader, but am now having an issue with the PC locking up when the GUI is displayed.

I have an NVIDIA GeForce FX 5200 card, and dual EIZO monitors.  I noticed there was the same problem when booting the install DVD and trying to use the GUI installer, so used the Text install and that installed ok.

When the Ubuntu splash screen has finished and it switches into the GUI, I get the logon box on one monitor and garbage on the other.  Then after about 5 seconds the mouse & keyboard freezes, and I can't do anything but a restart.

I have searched the forums for information on NVIDIA and there seems to be lots of people who have problems, and lots that don't.  I just don't know where to start to diagnose and resolve the problem ](*,) 

Any help is appreciated.

BeakZ

---

### Post by renzokuken on 2006-12-12
I would start by, for now, unplugging the second monitor, and getting it to work on just the one first. Then when that is working, use something like Twinview to get the second going properly.

Have you installed the nVidia drivers yet?

You can do this from the command line so you dont need to boot into a GUI to do it......

I cant remember the exact packages that need installing, so DONT do this till i've checked, (this gives you an idea of what you need to search for) but its something like

```
sudo apt-get install nvidia-glx
```

Then to configure your xorg.conf, do

```
sudo nvidia-xconfig
```

Dont

---

### Post by beaker on 2006-12-12
Thanks renzokuken but it doesn't matter if the monitor is plugged in or not, the desktop still freezes.

I haven't installed anything additional, the installer did all the work :) 

I'll have a look around for code as you suggest, but look forward to hearing back from you with the outcome.

BeakZ

---

### Post by renzokuken on 2006-12-12
i'm looking now, but for the moment, can you post your xorg.conf? or at least the driver it is using?

if you boot into safe mode then do

```
sudo nano /etc/X11/xorg.conf
```

scroll down to the Device section and let us know what the driver is.

EDIT: the best way to install the latest nVidia drivers is to go to [http://www.ubuntuforums.org/showthread.php?t=263851&highlight=seerofsouls+nvidia+edgy](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=seerofsouls+nvidia+edgy) and follow [color=red]Step 2 : Installing Nvidia drivers - Option 1[/color]

This can be done from the command line so if your not sure how then let us know

EDIT 2: actually, an easier way is the way i described in the first post ( i confirmed that works). its just an older version of the driver (but probably more stable)

---

### Post by beaker on 2006-12-12
Ok, I have completed the steps in your first post and that seemed to go OK.  I've restarted and I now have two more options in the bootloader menu as follows:


```
Ubuntu, kernel 2.6.15-27-386
Ubuntu, kernel 2.6.15-27-386 (recovery mode)
Ubuntu, kernel 2.6.15-23-386
Ubuntu, kernel 2.6.15-23-386 (recovery mode)
```


When I boot the newest item I see the NVidia logo flash up just before the logon prompt, but then the desktop locks up again.  There isn't anything on the second monitor so assume something is working better.

When I try booting the older Kernel this fails and displays:

```
[4294697.446000] hci_usb_intr_rx_submit: hci0 intr rx submit failed urb f7ebe143 err -28
[4294697.447000] hci_cmd_task: hci0 command tx timeout

Ubuntu 6.06 LTS Voyager tty1
```

and then I get the logon prompt, but thats frozen too :S

Do you think I'm beyond a video card issue and have something else going on?

---

### Post by renzokuken on 2006-12-12
i think your right, it may be another issue alltogether.

at least now you have the nVidia drivers installed which will improve everything when it is working. from now on choose the second option on Grub as that is the one with nVidia support.

hci0 appears to be associated with bluetooth.

do you have any usb bluetooth or any other non-essential usb devices attached?

---

### Post by Rucko on 2008-01-23
A common problem with video drivers is that the old driver is still installed.
If the "nv" driver, the original driver, is still installed it will crash on boot up because the old and new drivers are both trying to load. 

You need to blacklist the old driver, by editing this file: /etc/default/linux-restricted-modules-common
and enter this line DISABLED_MODULES="nv" and save.

If the above fails:

Then go to a shell prompt and type  "uname -r" to see the name of your kernel. 
Make sure before compiling the new module, that the appropriate kernel headers are installed. Then recompile.

Good luck.

---

