---
title: "OpenGL Not Really Working with Nvidia Driver"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by tman elite on 2008-02-26
I'm using the nvidia accelerated graphics driver in the Restricted Drivers Manager, and OpenGL doesn't seem to work.  Glxgears runs fine with anywhere from 300 to 3000 fps depending on how many windows I have open at the time, but games or other applications that use OpenGL usually show up as a black screen or crash my computer.  For example, Supertux version 1.3 has an option for OpenGL.  It runs fine when OpenGL's not being used, but as soon as I enable it, nothing shows up but a black screen with a blue rectangle in the middle.  I've been using Ubuntu for a while but I don't know much about hardware and stuff.  Anyway here's some of the information from nvidia-settings:

> Operating System: Linux-x86
NVIDIA Driver Version: 1.0-9639

Graphics Processor: GeForce4 MX Integrated GPU
VBIOS Version: 0.4.1f.00.08.09
Memory: 128 MB
Bus Type: AGP 4X
Bus ID: 2:0:0

By the way, the whole time nvidia-settings is running, the terminal is giving me:

```
ERROR: Unable to assign attribute DigitalVibrance specified on line 19 of
       configuration file '/home/tman/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 20 of
       configuration file '/home/tman/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 21 of
       configuration file '/home/tman/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 22 of
       configuration file '/home/tman/.nvidia-settings-rc' (no Display
       connection).

(and on, and on, and on, etc.)
```


If you need anymore information, just tell me what to look up and where to find it.

Any suggestions are appreciated.  If anyone had a similar problem and can explain how they fixed it, that could help too.

---

### Post by natirips on 2008-02-27
There is a possibility that your graphics card itself (hardware) or graphics drivers (software) is/are mulfunctioning, or that you have wrong drivers installed (for a diffrent graphics card). There is also a small possibility that you do not have OpenGL installed (although I don't think this is the case).
Try installing the drivers from [www.nvidia.com](www.nvidia.com) (if you aren't using them already) (but be warned that I won't hold myself responsible if it brakes you computer, or turns it into a human-blood-thirsty monster).

---

### Post by The Cog on 2008-02-27
Try disabling the special effects (System->Preferences->Appearance->Visual Effects) which can sometimes conflict with 3d games.

---

### Post by tman elite on 2008-02-27
The system effects are already disabled.

I reinstalled the nvidia driver straight from the website, and it worked and everything (no flesh-eating machines) but I'm still having the same problems with OpenGL.

---

### Post by natirips on 2008-02-28
P.S.: If you have some very important data in your compuuter and are very afraid of getting your display ruined, do not do the following.

Try doing the following in the console:```
cd
sudo cp .nvidia-settings-rc .nvidia-settings-rc_backup_kopy
sudo nvidia-settings
```Now there SHOULD be less errors, try exiting the nvidia-settings. If it only messes up something, do the following:```
sudo cp .nvidia-settings-rc_backup_kopy .nvidia-settings-rc
``` to revert to the old .nvidia-settings-rc file (if it asks you (it didn't ask me when I tried but...) do overwrite the file). At some point, if you wish to remove the backup copy file (the one with _backup_kopy appended to its filename) you can do the following:```
sudo rm .nvidia-settings-rc_backup_kopy
```The only thing you lose by doing so is the old settings, doing so will not alter your system, only it's (manual) "backup" data.

Edit: If that doesn't help, and noone posts any replies here in a longer while, you can try contacting Nvidia support [http://www.nvidia.com/page/support.html](http://www.nvidia.com/page/support.html) .

---

### Post by tman elite on 2008-02-28
Thanks.  I'm not getting any errors anymore when I run nvidia-settings.  The OpenGL problems haven't changed though.

---

### Post by natirips on 2008-02-28
I'm not sure how good you are with the console, but here's a little explanation of why it helps against the errors: "sudo command" means you're running the "command" with administrative privilegies (it is necessary for some commands to make sure you don't use them accidentally). The "cp source destination" is the command for copying files (alot like CTRL+C when source is selected and CTRL+V when you've found destination). The "cd" alone just makes sure you're in your home directory, and "rm some_file" deletes some_file. So basically, the main part of everything was "**sudo** nvidia-settings", so if you're to use nvidia-settings again without those errors, that part alone is enough. The rest is just for the case something goes wrong.

---

### Post by tman elite on 2008-02-28
Yeah I knew what the cp, rm, and cd did but I didn't know what sudo did so that should be useful in the future.

---

