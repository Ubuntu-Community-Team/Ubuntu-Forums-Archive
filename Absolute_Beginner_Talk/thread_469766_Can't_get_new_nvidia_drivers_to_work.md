---
title: "Can't get new nvidia drivers to work"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by bldgengineer on 2007-06-10
Been trying to get the latest drivers to work since they came out on Friday with no luck. These drivers are the only drivers for the 8600gts. I gotten this command to work once but it doesn't seem to have done anything: 

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-100.14.09-pkg1.run 
sudo /etc/init.d/gdm start
```

And whenever I try nvidia's way I get: 
> ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).


Even though the only thing I have open is terminal.

Also, in my xorg file(?) it says my nvidia drivers currently are the nv drivers and whenever I try to open restricted drivers manager it tells me > Your hardware does not need any restricted drivers.

This is driving me nuts! ](*,)  I know I must be missing something stupid but any help I can get will be really appreciated.

---

### Post by Nythain on 2007-06-10
you could just try sudo apt-get install nvidia-glx-new
then run gksudo nvidia-settings

---

### Post by Kobalt on 2007-06-10
Once you've typed this in the Terminal : ```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
```You need to log out and press Ctrl+Alt+F1 to access a command line, then you can enter the rest of your command lines : ```
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-100.14.09-pkg1.run 
```
Also make sure your xorg.conf file is well set with ```
sudo nvidia-xconfig
```
And finally : ```
sudo /etc/init.d/gdm start
```

---

### Post by bldgengineer on 2007-06-10
Kobalt,

Thanks for the help! That got me a little bit further but now when I restart the X server its telling me my kernel doesn't match the driver being used. 

The only way I was able to restart the GUI was to go back into the xorg.conf and change the "nvidia" driver back to "nv"

any advice?

---

### Post by Kobalt on 2007-06-10
Do you use the generic or the i386 kernel ? It may require the i386, though it has been working it the past with generic...

---

### Post by bldgengineer on 2007-06-10
I thought that this line was supposed to get rid of the old kernel
```
 sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
```

And the new nvidia driver package contained the new kernel:confused:

---

### Post by Kobalt on 2007-06-10
This doesn't remove your kernel, it removes the nvidia drivers and its kernel module (nvidia-kernel-common). 
To know which version of the kernel you use type in the command line :```
uname -r
```

---

### Post by bldgengineer on 2007-06-10
2.6.20-16-generic

---

### Post by bldgengineer on 2007-06-10
still can't get it to work :( 

Here is my error log

---

### Post by bldgengineer on 2007-06-11
aaarrrggghh!!](*,)

---

### Post by Malta paul on 2007-06-11
I don't know if this puts any light on your problem?
I had installed the latest graphic driver for my Nividia card and it ran fine with kernel 2.6.20-15.
Saturday I upgraded the Kernel to 2.6.20-16, on rebooting StartX would no work and I was stuck in text mode.
Rebooting again in -15 it still worked fine. 
My fix was to boot using the live CD, copy the Xorg.conf file to my usb pen drive. Reboot into the -15 kernel then rename the Xorg,config file to backup and with the usb installed copy the live disk Xorg.config fill in its place.
Then it was boot up the -16 kernel and it all now works fine!  :Dsarum

---

### Post by bldgengineer on 2007-06-11
do you think that this would work with an 8600GTS though?

---

### Post by Nythain on 2007-06-11
> **Malta paul said:**
> I don't know if this puts any light on your problem?
I had installed the latest graphic driver for my Nividia card and it ran fine with kernel 2.6.20-15.
Saturday I upgraded the Kernel to 2.6.20-16, on rebooting StartX would no work and I was stuck in text mode.
Rebooting again in -15 it still worked fine. 
My fix was to boot using the live CD, copy the Xorg.conf file to my usb pen drive. Reboot into the -15 kernel then rename the Xorg,config file to backup and with the usb installed copy the live disk Xorg.config fill in its place.
Then it was boot up the -16 kernel and it all now works fine!  :Dsarum
your problem there lied in the fact that you installed the drivers via the .run install package downloaded from nvidia's site, wich need to be re-installed every time you upgrade your kernel.
installing the drivers via apt-get will keep your drivers up to date with kernel upgrades... all you effectively did by loading the livecd and copying its xorg.conf over and then using that with hte new kernel is switch the driver x is using from the proprietary "nvidia" driver to the open "nv" driver that ubuntu uses by default... efectively backstepping the entire nvidia driver process.

---

### Post by Nythain on 2007-06-11
as for installing the correct driver manually and fixing that conflict of kernel vs. module do this for me
at command line (NOT terminal)(command line can be accomplished by hitting control+alt+f2 or i believe a safe login at grub will boot you straight to cl) type
```

sudo nano /etc/default/linux-restricted-modules-common

```
and nv between the "" on the line that says DISABLED_MODULES=""
hit control+x, y, enter    to save and exit nano
```

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4  xserver-xorg-dev

```
```

sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

```
```

sudo rm /etc/init.d/nvidia-*

```
cd into the directory containing the .run package you downloaded from the nvidia site (hopefully its the 9755 package cause thats what im using in the syntax here)
```

sudo /etc/init.d/gdm stop

```
```

sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run

```
```

sudo nano /etc/X11/xorg.conf

```
make sure this section
```

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

```
reads "nvidia" and NOT "nv"
once again, hit control+x, y, enter to save and exit nano
```

sudo /etc/init.d/gdm start

```
hopefully log back into gnome error free this time

i know most of this was already explained, the only issue im having is the fact that if done correctly, the install script will check for previously installed versions of the module and delete them, and create the right one...

since that DIDNT happen, aparently something went horribly wrong during the first attempt, so im trying to make it a little easier to follow, and adding that very important part about adding nv to linux-restricted-modules-common that most people tend to forget about

---

### Post by bldgengineer on 2007-06-11
Nythain,

Thanks for all the help even though all of those have commands have been done before I re-did them all just like you said. I did however change the 9755 package to match my own (100.14.09). 

So I re-did everything just like you said and no luck. I get the same error I've been getting. Everything matched except in the xorg.conf under identifier, its not say my cards name like it does yours.
```
Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection
```

Mine says
```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default card"
    Driver         "nvidia"
EndSection
```

And the only way for me to get back to the GUI is by changing Driver "nvidia" back to "nv"

---

### Post by ububug on 2007-06-11
I've been having the same problem w/ the same driver, I've followed all of those steps and I have to reinstall the driver everytime I reboot. My guess is that the install routine is loading the nvidia kernel, but not installing it so that it's loaded everytime you reboot. I'm trying to find the name of the nvidia kernel is it a module that I can install via insmod?

---

### Post by ububug on 2007-06-12
Ok, I got it to work, I purged all of the existing nvidia packages and deleted

/etc/init.d/nvidia-kernel
and
/etc/default/nvidia-kernel

reinstalled the driver and rebooted. Everything works perfectly now.

---

### Post by Malta paul on 2007-06-12
Hi Nythain, thanks mate for your detailed info, I will have another try when I get home from work this evening and will post results. ;)

---

### Post by bldgengineer on 2007-06-12
just did the samething with no luck

---

### Post by ayenack on 2007-06-12
Try doing it in recovery mode. From boot options.

---

### Post by Pumalite on 2007-06-13
> **ayenack said:**
> Try doing it in recovery mode. From boot options.

Make sure that your kernel-headers match your kernel version. Also you should make sure you have 'make', 'automake', and the latest gcc ( 4 or 4.1 I think it is ), and autoconf.

---

### Post by bldgengineer on 2007-06-13
ok, I enabled automake and autoconf and I already had the latest gcc and make installed but I just had something really wierd happen. I didn't get the kernel did not match error, instead it went straight back to the command prompt with a "screens found but none matched" and a few other things. I did an nvidia bug report and zipped it with a few other things if anyone is interested.

---

### Post by Malta paul on 2007-06-14
Well I had a go at getting my kernel 2.6,20-16, x/graphics to work, but I had a conflicted with the -15 X/graphics. In fact I mess every thing up! 
My fix was to start with a clean sheet by booting the live disk and manually formating the root partition ONLY, and reinstalling just root files. As I have 4 partitions on my HD  my personal files were not touched.
I then booted the -15 kernel, left the the graphics in the generic mode and down loaded the upgrade 2.6.20-16 kernel. After rebooting the -16 kernel I installed the Nvidia driver for my graphic card.
Now I have colour rendering and accelerated graphs! :D
By the way before formating my root files, I exported my email and bookmark files to one of my partitions so I didn't loose then. On rebooting into the -16 kernel I imported them back into Firefox and Thunderbird ;)
Hope this info helps someone.

---

### Post by samuraiCat on 2007-06-14
> **Malta paul said:**
> Well I had a go at getting my kernel 2.6,20-16, x/graphics to work, but I had a conflicted with the -15 X/graphics. In fact I mess every thing up! 
My fix was to start with a clean sheet by booting the live disk and manually formating the root partition ONLY, and reinstalling just root files. As I have 4 partitions on my HD  my personal files were not touched.
I then booted the -15 kernel, left the the graphics in the generic mode and down loaded the upgrade 2.6.20-16 kernel. After rebooting the -16 kernel I installed the Nvidia driver for my graphic card.
Now I have colour rendering and accelerated graphs! :D
By the way before formating my root files, I exported my email and bookmark files to one of my partitions so I didn't loose then. On rebooting into the -16 kernel I imported them back into Firefox and Thunderbird ;)
Hope this info helps someone.

Good to know! Thanks!

---

### Post by BlahMan_of.Doom on 2007-06-14
Use [Envy](http://www.albertomilone.com/nvidia_scripts1.html). I just installed it about 5 minutes ago and it's working smoothly.

---

### Post by Malta paul on 2007-06-15
BlahMan_of.Doom, another good tip. Thanks mate ;)

---

