---
title: "Can't get nvidia drivers to install manually"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by darkop16 on 2008-01-01
I've got a 8800gts and i am trying to install the correct drivers for it. I tried using the restricted drivers first and it worked better than it did without out it but the windows would lag when i moved them accross the screen. So i am trying to install the drivers manually.

I downloaded the lastest drivers:
[drivers]("http://www.nvidia.com/object/linux_display_ia32_169.07.html")

Im following what this guy did:
[http://ubuntuforums.org/showthread.php?t=630464](http://ubuntuforums.org/showthread.php?t=630464)

Instead of

```
sudo ./NVIDIA-Linux-x86-169.07-pkg1.run
```

I used 

```
sudo sh ./NVIDIA-Linux-x86-169.07-pkg1.run
```

Since it wouldn't take the command without the "sh."

So it starts up and asks me to accept the license and i accept it.

But i get this after accepting the license:
```
No precompiled kernel interface was found to match your kernel; would 
you like the installer to attempt to download a kernel interface for your kernel 
from the NVIDIA ftp site (ftp://download.nvidia,com)?
```

So im like OK, lets try it (*hits yes), and this is what i get:
```
No matching precompiled kernel interface was found on the NVIDIA ftp 
site; this means that the installer will need to compile a kernel interface for 
your kernel. 
```

I can only click OK, so i hit enter and this is what i get:
```
ERROR: You do not appear to have libc header files installed on your 
system. Please install your distribution's libc development package
```

Again i can only select OK, so i hit enter and i get:
```
ERROR: Installation has failed. Please see the file 
'/var/log/nvidia-installer.log' for details. You may find suggestions on fixing
 installation problems in the README available on the Linux driver download 
page at www.nvidia.com
```

I can only click OK, so i hit enter and it dumps me back into the command line screen i started with when i git [ALT] + F2 on the login screen.

I did check out the README file hoping it would tell me i need to download a specific package and i could do that through the Synaptic Package Manager but it doesn't and i am a complete linux newb (just started using ubuntu) so i wouldn't really know what to look for without a specific name.

Any help would be apperciated,
darkop16

---

### Post by PmDematagoda on 2008-01-01
Install the build-essential package using:-
```
sudo apt-get install build-essential
```

That should allow you to complete the install properly.

---

### Post by overdrank on 2008-01-01
You could also try Envy, It has worked for many users
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Good luck!

---

### Post by GSF1200S on 2008-01-01
You may also need to do this one:
```

sudo apt-get install libc6-dev
```

Let us know what it says. Post in this thread if you have configuration problems or it doesnt work- ill keep an eye on this one..

---

### Post by darkop16 on 2008-01-01
It worked with only:

```
sudo apt-get install build-essential
```

I rebooted after it was done. It feels much better too. The Window dragging still produces some lag (jaggedy edges when i move it around the screen), but not as bad as with the restricted drivers installed.

Thanx for the help,
darkop16

---

### Post by PmDematagoda on 2008-01-01
Glad we could help:).

---

### Post by darkop16 on 2008-01-01
Thanx again.

I just went back to XP and i can notice the same thing with XP if i look close enough. I guess its just the new setup is making me picky. But i still see a big difference installing the drivers manually over using the restricted drivers.

darkop16

---

### Post by GSF1200S on 2008-01-01
> **darkop16 said:**
> Thanx again.

I just went back to XP and i can notice the same thing with XP if i look close enough. I guess its just the new setup is making me picky. But i still see a big difference installing the drivers manually over using the restricted drivers.

darkop16

Im the same way with CPU usage for some reason. If my system is using over 10% and I dont know why, I get angry :)

As said above, glad he could help ;)

---

