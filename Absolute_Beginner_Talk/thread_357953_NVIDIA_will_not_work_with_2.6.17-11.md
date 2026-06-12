---
title: "NVIDIA will not work with 2.6.17-11"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by mdurkin on 2007-02-10
Hi All,
I've today just installed ubuntu 6.10 fresh, works fine. I then install the updates and move to latest 2.6.17-11 kernel.
I then download envy to install the nvidia drivers. It fails so I install libc6 packages and it manages to make it through the install. Unfortunately X server then fails.

I am at a loss - I have re-installed half a dozen times today, read the 34 page posing about the new kernel release, read a whole heap of other posts and nothing i working for me! I have a 6150 GPU that was previously running like a dream under ubuntu (last week).

Can someone help with what I should be doing after a fresh install to get the nvidia drivers working properly with the new kernel?

Thanks,
Matthew

---

### Post by arochester on 2007-02-10
To install Nvidia I found the script "Envy" very good. It checks which video card exists, downloads and installs the correct drivers for Nvidia or ATI. Read about it at [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mdurkin on 2007-02-10
did you read my post? I am using envy and it does not work properly with the new kernel. This forum is full of suggestions to use envy, but I've just tried a fresh install, update system, then use envy and it doesn't work.
I've also tried to install the drivers directly from nvidia, using automatix, and have tried lots of suggestions around various posts on this forum.
To no avail so far. I'm not a linux newbie, but I don't have much experience with X - hence my current frustration! I can happily restore the old config file and use the vesa driver, but performance is really awful. I really need to find a solution!
Any help appreciated...

---

### Post by OffHand on 2007-02-10
> **mdurkin said:**
> did you read my post? I am using envy and it does not work properly with the new kernel. This forum is full of suggestions to use envy, but I've just tried a fresh install, update system, then use envy and it doesn't work.
I've also tried to install the drivers directly from nvidia, using automatix, and have tried lots of suggestions around various posts on this forum.
To no avail so far. I'm not a linux newbie, but I don't have much experience with X - hence my current frustration! I can happily restore the old config file and use the vesa driver, but performance is really awful. I really need to find a solution!
Any help appreciated...

Why don't you install the drivers from Nvidia manually?

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by 1001001 on 2007-02-10
I just did a new install of Ubuntu 6.10 and here are the steps I followed to get it working with my NVidia GeForce4 Ti4200.

1. Installed Ubuntu 6.10 using live CD
2. Installed all updates
3. Downloaded the following files:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
NVIDIA-Linux-x86-1.0-9631-pkg1.run (*** YOU MIGHT NEED 1.0-9746)

from gnome-terminal give the following commands:
sudo apt-get install linux-libc-dev
(this should download linux-libc-dev_2.6.17.1-11.35_i386.deb)

sudo apt-get install libc6-dev
(this should download libc6-dev_2.4-1ubuntu12.3_i386.deb)

sudo apt-get install xserver-xorg-dev
(this should download xserver-xorg-dev_1%3a1.1.1-0ubuntu12.1_i386.deb)

INSTALL linux-libc-dev, libc6-dev, and xserver-xorg-dev
(I do this by just right-click and selecting "Open with GDebi Package Installer")

4. run the following command in gnome-terminal:
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-glx-legacy

5. Logout and press CTRL-ALT-F1 to get out of desktop.
6. Login at a console with username and password.

7. Stop gdm using the following command:
sudo /etc/init.d/gdm stop

8. backup you existing X.org config file using the following command:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

9. Install the NVidia driver using the following command:
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
(LET THE INSTALL COMPILE A DRIVER FOR YOUR KERNEL)

10. prevent Ubuntu's restricted driver from loading at startup:
sudo nano -w /etc/default/linux-restricted-modules-common

--> put "nv" in the inverted comas after DISABLED_MODULES

11. Start gdm using the following command:
sudo /etc/init.d/gdm start

YOU SHOULD SEE THE NVIDIA LOGO FLASH JUST BEFORE THE LOGIN SCREEN.

I hope this helps with any problems you are having.
Good luck.

---

### Post by shane634 on 2007-02-10
mdurkin try this:

```
sudo /etc/init.d/gdm stop
```

  This will log you out of the Xserver. Once you get to a command prompt ( log in and password ) run envy and see if it installs. Then use:

```
sudo /etc/init.d/gdm start
```

  This will restart the Xserver. Or you can simply reboot.

---

### Post by Repent on 2007-02-10
What code do you enter to run envy?

---

### Post by shane634 on 2007-02-10
When you are at the command prompt you simply type:

```
envy
```

  Good luck.

---

### Post by Repent on 2007-02-10
When I type envy it just sits there nothing happens.  And yes I do have it installed my drivers worked just fine before the upgrade.

---

### Post by mdurkin on 2007-02-10
I think I know what's going on. The xserver-xorg-dev package wasn't coming down. What can cause problems with downloading packages? Do I have a naff repository in my sources list maybe??

---

### Post by shane634 on 2007-02-10
Not sure on the download deal. Open synaptic and click settings->repos, check everything on the first tab. Then close that and reload ( upper left ) and see if the xserver-xorg-dev package is there. If so click it and install it.  Envy should do that for you. If not get automatix2 and use it for your drivers. Also you may want to use the remove nvidia driver option first in envy then use it again to reinstall. Let me know how it goes.

---

### Post by mdurkin on 2007-02-10
all sorted - I eventually managed to get the package down after several attempt and the envy worked fine. hurrah!!
and thanks to everyone who replied!
Matt

---

### Post by shane634 on 2007-02-10
Glad we could be of assistance. Now enjoy your ubuntu as before lol.

---

### Post by Repent on 2007-02-10
I did every thing you said and I still don't have my drivers installed. when I enter envy and hit install drivers the screen go's black and I have to hit Alt-F1 to get back to enter user name and password.
Then I into the restart code you gave us but still no drivers, I don't get it I really don't want to reinstall but my games no longer work.

I just don't get it.:(

---

### Post by shane634 on 2007-02-10
Repent give me the output of this in terminal:

```
lspci
```

```
lsusb
```

  Then we can get ya some more help.

---

### Post by Repent on 2007-02-10
Thank you for your help I was able to fix the problem at this website.
[http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717) Man it was easy and fast.\\:D/ 

Thanks again.
Repent

---

