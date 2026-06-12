---
title: "Change resolution"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Crisuntu on 2007-03-19
I cannot configure my screen resolution to "1024x768". The only options it gives me are "800x600" and "640x480"
I tried to edit my xorg.conf file to add it, but as soon as I rebooted the only thing the screen showed was "out of range"

Also, I have a 64MB NVidia geforce 2 MX 400. I've been trying to install the driver, but this error appears:

"The file '/tmp/.X0-lock' exists and appears to contain the process ID
'3708' of a runnning X server."

So, this "out of range" screen appears because I don't have the drivers installed? If so. How can I install them

Bye,

Cristian

---

### Post by Kobalt on 2007-03-19
Open a Terminal and type this :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the space bar, then press Enter. 
Finally, restart X with Ctrl+Alt+Backspace.

---

### Post by enharrin on 2007-03-19
If you are really not running X, I think you could probably go ahead and delete that file, if it causing driver installation problems.

---

### Post by Kobalt on 2007-03-19
You can follow the instructions I gave you even before logging in : press Ctrl+Alt+F1 at the login screen and log from the command line. Then follow the instructions as I wrote before...

---

### Post by vijayanand_sodadasi on 2007-03-19
This might help:
[http://ubuntuforums.org/showthread.php?t=258484]("http://ubuntuforums.org/showthread.php?t=258484")

---

### Post by Crisuntu on 2007-03-19
> **Kobalt said:**
> Open a Terminal and type this :
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Select the resolutions you want as available by hitting the space bar, then press Enter. 
Finally, restart X with Ctrl+Alt+Backspace.
Well, I don't know which configuration is the right one
I chose vga "1024x768". After I restarted I couldn't access because of a problem with the xserver. So,  I set it back to "800x600"

> **enharrin said:**
> If you are really not running X, I think you could probably go ahead and delete that file, if it causing driver installation problems.
I don't know what is the xserver. What does it do?
If it is not useful, How can I get rid of it?
See you

---

### Post by Kobalt on 2007-03-20
The xorg.conf file is not useful : it's essential. So don't delete it I suggest...
I think you need to [install the nVidia drivers]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper").

---

### Post by enharrin on 2007-03-20
Sorry, X is basically the graphical environment in Linux.

Definitely do NOT delete the xorg.conf or X itself.  But it would be safe (if you are not running X, i.e., you are at a command line login) to delete this file:

```
rm /tmp/.X0-lock
```

---

### Post by Crisuntu on 2007-03-20
Well, I installed the driver. I had to exit the X server using this code

```
sudo /etc/init.d/gdm stop
```

It seems "Ctrl+Alt+F1" was not enough.
Now, the problem with the resolution is still here. I don't know how to solve it. I've followed the recommendations above, however I can't make it "1024x768"

---

### Post by Crisuntu on 2007-03-22
Checking the xorg.conf file, I didn't see any difference before and after installing the driver
While installing it, it mentioned it couldn't find a "precompiled kernel interface"

> **vijayanand_sodadasi said:**
> This might help:
[http://ubuntuforums.org/showthread.php?t=258484]("http://ubuntuforums.org/showthread.php?t=258484")

This howto seems to be very good. It requires you to save the file you change, but I don't know how to save changes from the terminal.

Is there any other information that I can provide you in order to understand the problem better?

Bye,

Cristian

---

