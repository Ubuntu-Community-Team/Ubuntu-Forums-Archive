---
title: "Nvidia driver options???"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Koti on 2006-08-23
I've got a computer here at work I've been playing around with. It's an 800MHz with 750M Ram. It's got a Nvidia GeForce3 Ti 200 Pro graphics card. I've loaded the latest Nvidia drivers from the repository, but for some reason I can not get any 3D rendering or a resolution greater than 1024x768. I went to Nvidias site to download a driver from them, but I need to install it without the xserver running. ??? Now I understand that I can boot up in recovery mode and install it from root, but how dangerous is this. How bad can I fubar this system that way? Is there a place I can go to downlaod a deb file of the driver or other means to load a driver. The repository one just doesn't seem to be working for me. 

Oooor.... is there something in the xorg.conf I need to modify that will facilitate the items listed above?

---

### Post by Koti on 2006-08-23
Another question regarding this graphics card... Does anyone know if it's considered legacy or not? I thought I had checked previously and found that it wasn't, but then a friend mentioned that it was. How can I determine this for sure?

---

### Post by Koti on 2006-08-24
Bump

Sorry. I'm not trying to be impatient...:-\"  I'd just like someones opinion on this. If at least get my resolution up from 1024x768. 

Any help would be great!:mrgreen:

---

### Post by luvr on 2006-08-24
[ NVIDIA LIST of videocards supported through LEGACY DRIVER]("http://www.ubuntuforums.org/showthread.php?t=233241")

To stop the X Window Server, type the folowing command (but replace *"gdm"* with *"_k_dm"* if you run KDE instead of GNOME):
```
sudo /etc/init.d/gdm stop
```
[More information on how to install the NVIDIA proprietary drivers.]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by Koti on 2006-08-24
Awesome! Thanks for your help! I'll let you know how it turns out.

---

### Post by Koti on 2006-08-24
No luck with either Method 1 or 2. Method 1 reconfigures my xorg.conf and then my xserver won't start and I need to restore it from the backup. Method 2 had several problems. It seems that it can't write to the Nvidia.ko file and there are some conflicts with the kernel. It said something to the effect that the kernel was generated improperly. For now I'm going to give up. 

Thank you again for your help.

---

### Post by luvr on 2006-08-25
I'm planning on installing the NVIDIA module myself one of these days; I'll be using the most recent version that I downloaded from the NVIDIA web site, and see if I can get that to work.

In preparing for the installation, here's the steps that I have already taken (through the Synaptic Package Manager):
[LIST]
[*]I uninstalled the *"restricted"* modules.
[*]I upgraded my kernel. I selected an *"i686"* variant (since the machine runs on a Pentium IV), and made sure that the source code for this exact same kernel version was available as well.
[*]I installed the corresponding kernel source, too. Apparently, this just downloaded an archive file, but didn't unpack it.
[/LIST]
I'll let you know if I get any further with this.

---

### Post by nudnik on 2006-08-25
Uninstall any Nvidia drivers using synaptic. 

Boot to the command line and type the following:

sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure -phigh xserver-xorg

Reboot the machine. Access synaptic package manager and install the Nvidia glx legacy package. Open a terminal and type:

sudo nvidia-glx-config enable

Reboot the machine. You should see the Nvidia logo during bootup if all went well. 

](*,)  Ubuntu can be trying at times.

---

### Post by wheels5894 on 2006-08-25
I too have the 1024 x 768 problem. I am using a Ti4600 graphics card. Have any of the above suggestions worked for amyone to enable a higher resolution?  As I am using an LCD monitor the screen looks a whole lot better at 1280 x 1024 and I was surprised to be offered this when setting up but no sign of it now, so I hopesome of the above helped.

---

### Post by luvr on 2006-08-25
> **wheels5894 said:**
> As I am using an LCD monitor the screen looks a whole lot better at 1280 x 1024 and I was surprised to be offered this when setting up but no sign of it now, so I hopesome of the above helped.
If you cannot go any higher than 1024x768, then merely installing the binary NVIDIA driver is unlikely to help you out.

You will have to modify the X Window System configuration file, and add in the 1280x1024 resolution.

Me too, I am running an LCD screen that works best at 1280x1024, and Ubuntu (like most other Linux distros, at that) didn't configure it appropriately. After messing around with I don't remember which system settings, I even found myself at 1600x1400 or some such resolution at one point in time--which totally messed up the display.

Anyway, quite a while ago, I had configured Slackware on this computer, and I keep its Xorg.conf file handy (since that worked great); ever since, whenever I cannot get some Linux distro to properly configure the display, I just copy over the appropriate sections from my former Slackware file. Works like a charm!

---

### Post by d3a1i0 on 2007-10-13
> **nudnik said:**
> Uninstall any Nvidia drivers using synaptic. 

Boot to the command line and type the following:

sudo /etc/init.d/gdm stop

sudo dpkg-reconfigure -phigh xserver-xorg

Reboot the machine. Access synaptic package manager and install the Nvidia glx legacy package. Open a terminal and type:

sudo nvidia-glx-config enable

Reboot the machine. You should see the Nvidia logo during bootup if all went well. 

](*,)  Ubuntu can be trying at times.



I just want to thank nudnik for writting this post.  This worked for me but I have to look up how to boot to command line, [CTRL][ALT][F1], and once I did the dpkg-reconfigure command I was not expecting the configuration tool to come up and I was not sure how to use it.  I made it through the first time and I mostly picked the defaults.  Then I tried to enable the nvidia-glx-config using the Tilda program and I kept getting some silly error.  So I tried it with gnome-terminal and it worked.  I rebooted and I did not see and NVIDIA logo, and I was still not able to get the resolution bigger then 1024x768.  I then booted back into the command line and stopped gdm again.  I went through the dpkg-configure tool again and had to figure out how to add the 1280x1024 resolution to the list of modes.  Then I rebooted again and I was able to use 1280x1024.  Still never saw the NVIDIA logo on boot.

---

