---
title: "Steps for Easy installation of nvidia .run (from nvidia.com , linux drivers page)"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Tayyeb on 2007-08-15
I tried it and it worked
Steps for Easy installation of nvidia .run (from nvidia.com , linux drivers page) in ubuntu feisty fawn 7.04:
1. Download .run package from nvidia site.
2. Uninstall nvidia-glx  (sudo apt-get remove nvidia-glx --purge)
    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

3.(not necessary ,depends) make a file named nvidia in /etc/modprobe.d/ (if it isn't there already) any put this in it:

options nvidia NVreg_DeviceFileUID=0 NVreg_DeviceFileGID=33 NVreg_DeviceFileMode=0666           


The NVreg_DeviceFileGID number should be the GID for the video group.
Here you can find the GID (I think the last two digits):  
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html) 

4. I removed the package linux-restricted-modules-common, commented out the line in /etc/modprobe.d/lrm-video that said to use the lrm/video script with the nvidia module, added nvidia to /etc/modules.

5. Press CTRL+ALT+F2 to go to console mode.  Then type     

sudo /etc/init.d/gdm stop

the above will exit X server.

6. Now type 
init 3

OR TYPE

cd /sbin

telinit 3 

The above will change the runlevel to 3.

7. Now use 
cd
command to browse to the folder where Nvidia .run file is present.
Then type:

sh <name of package>.run

Then Answer yes when asked to "compile kernel module". Again answer YES when asked to run "nvidia-xconfig" to setup your xorg.conf file.

8. If you answered NO when asked for "nvidia-xconfig". You can run it again by typing:

nvidia-xconfig

9. Type

sudo /etc/init.d/gdm restart

The above will bring you back to the X server (GNOME in Ubuntu Feisty).

ALL DONE ! You may see a nvidia logo ! Now you can also enable desktop effects.

NOTE:
STEPS 5 to 9 are done in console mode.
I tried the above method in Ubuntu Feisty Fawn 7.04 (Kernel: 2.6.20.5-15-generic).
STEP 4 solved the following problem:
NVIDIA: Could not open the device file /dev/nvidiactl (No such device or address)
ERROR ( EE ): Cannot initialize nvidia-kernel
Check if you have a supported GPU.

I searched many forums for its solution. Then made this list.

---

### Post by Conano on 2007-09-24
I attempted this, but i could neither delete or remove one of the nvidia files, as well as i couldnt edit the restricted moduals file. said i didnt have permission... go figure and far as i know i was administrator.. 

why cant it be simple as download and double click.

---

### Post by aysiu on 2007-09-24
> **Conano said:**
> 
why cant it be simple as download and double click. It can be. Read this:
[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia)

---

### Post by Conano on 2007-09-24
i have tried that, when i click system > administration > Restricted Drivers manager. Iit will then pop up and ask for my password, i give it, and it then pops up with "your hardware does not need any restricted drivers"

I mean if this is the case, that wouldnt that mean i already have the latest drivers? or should i uninstall the ones i have, then run the restricted drivers manager?

---

### Post by Shazaam on 2007-09-24
What video card do you have?

---

### Post by alienexplorers on 2007-09-25
I still prefer Envy script to load my drivers.  Did it two times by hand and had to reload Ubuntu both times to fix the mess I made.

---

