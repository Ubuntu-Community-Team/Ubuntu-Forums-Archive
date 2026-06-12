---
title: "Error message when install Nvidia Drivers"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by rosdahale on 2006-08-16
Im having a nightmare of a time trying to install the nvidia drivers. I have added Nvidia-glx to the Synaptic package manager, BUT it wont allow me to install the nvidia-settings without removing the Nvidia-glx first. Having just the Nvidia-glx loaded up when I try this "sudo nvidia-glx-config enable" I just get this error message :

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

So, how do i get both the above files loaded and install the driver. Do i have to manual change the "NV" setting like the messge says ??

---

### Post by meng on 2006-08-16
You don't need to install the nvidia-settings package, it is included in the nvidia-glx package, that's why the two are incompatible. The suggested manual change to xorg.conf seems quite straightforward, why not do that?

---

### Post by rosdahale on 2006-08-16
Ok, thanks I just wanted to make sure it was ok to do it before I changed it, this is my first day with ubuntu, dont want to mess things up and have to start again :)

---

### Post by meng on 2006-08-16
The worst that can happen is that you'd have to change the xorg.conf back to "nv". And the first day is the best day to break your system, you would prefer not to do it once it's all nicely set up already.

---

### Post by davidsxls on 2006-08-16
as the message says, run this command
$ md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
$ sudo nvidia-glx-config enable

the nvidia-settings is included in nvidia-glx package.

---

### Post by rosdahale on 2006-08-16
Well it seems to have done the trick, everything is a lot sharper and faster now, the only problem now is the screen resolution is still only a max of 1024x at 24bit how do I go about changing this ?

---

### Post by steve.horsley on 2006-08-16
The standard reply to that question (gets asked every day without fail) is to backup /etc/X11/xorg.conf and then run:
**sudo dpkg-reconfigure xserver-xorg**
from the command line. Accept the default where you're not sure. For some reason, it seems to like setting a pc104 keyboard rather than pc105 though.

---

### Post by rosdahale on 2006-08-16
Ok, I typed in the commands it told me to in the message (md5sum ect....) and then used the sudo nvidia-glx-config enable. Everything seemed to work fine, restarted and got this error message : Failed to start the xserver liely it is not set up correctly. The log said this at the bottom :

(ww)NVIDIA : No matching device section for instance (busid pc1:1:0:0)

(ee)No devices detected.

I had a backup of the old xorg.conf so wrote over it. It starts up fine now, (obviously with no nvidia driver) but now nothing is working - internet, drive gone from my computer).

Ill try sudo dpkg-reconfigure xserver-xorg command now (i have to keep booting in to windows to get online and check this page) But what went wrong before ????? I have a geforce 6800gt

---

### Post by rosdahale on 2006-08-16
Ok...things seem to be ok, (did the reconfigure) im getting the nvidia logo now on start up and the screen res is now ok...BUT Ive lost my internet connection and cant get it back up (ive noticed I have two firmware folders now). Went through the same steps I did before but still no joy (speedtouch 330). :(

---

