---
title: "update new drivers for my NVIDIA geforce 7 series card using ubuntu 7.04"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Nyxess on 2007-06-29
i recently installed beryl, and i asked me to change my color to 24. the only way i know how to do that is to run the command 

$  sudo dpkg-reconfigure xserver-xorg

that command also resets the drivers for your graphics card i found out.....

Envy wont work, and the instruction listed at [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)
didnt help either.

STEP 2: Install nvidia drivers

Option 1:

Lupine's repos is now no-longer availiable.
You may use Envy, a Python script that eases installation of the official Nvidia and ATI drivers. Please see [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (>=9631 driver needed...)

Option2:

If you would prefer to install the nvidia drivers from nvidia's script, you may simply download the NVIDIA drivers from here, then:

Code:

sudo nano /etc/default/linux-restricted-modules-common

Make the last line look like
Code:

DISABLED_MODULES="nv"

ctrl+x and y to save.

Then
Code:

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start

The Nvidia script should change your xorg.conf to enable nvidia drivers & compositing.

i got to "sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common". after that no command would work. help plz =)

---

### Post by Bachstelze on 2007-06-29
"It doesn't work" doesn't help us much. What does it do instead of working ?

---

### Post by Nyxess on 2007-06-29
when i try to install the nvidia driver through envy it comes up with this in the terminal 

python pulse.py nvidia
root@nyx:/usr/share/envy# python pulse.py nvidia
ENVY ERROR: Your Operating System does not seem to be supported by envy

which i find odd, 7.04 doesnt work with envy?

if i try to Install the NVIDIA driver manually (selecting version 9631) i get the same thing.

if i follow the direction at [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851), which are:

STEP 2: Install nvidia drivers

Option 1:

Lupine's repos is now no-longer availiable.
You may use Envy, a Python script that eases installation of the official Nvidia and ATI drivers. Please see [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (>=9631 driver needed...)

Option2:

If you would prefer to install the nvidia drivers from nvidia's script, you may simply download the NVIDIA drivers from here, then:

Code:

sudo nano /etc/default/linux-restricted-modules-common

Make the last line look like
Code:

DISABLED_MODULES="nv"

ctrl+x and y to save.

Then
Code:

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
sudo nvidia-xconfig --add-argb-glx-visuals
sudo /etc/init.d/gdm start

The Nvidia script should change your xorg.conf to enable nvidia drivers & compositing.

Remember that following this method requires a reinstillation of them every time the kernel changes.

i get up to "sudo rm /etc/init.d/nvidia-*" when i run that command i get:

rm: cannot remove `/etc/init.d/nvidia-': No such file or directory

which im assuming leaves me with no driver because after i restart i have just the shell (i think that the terminology) and have to run "sudo dpkg-reconfigure xserver-xorg" which puts me back to square one.

---

