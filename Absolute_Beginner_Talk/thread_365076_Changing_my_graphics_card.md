---
title: "Changing my graphics card"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by panti19 on 2007-02-19
I have an ATI radeon 9600 with  256 mb DDRII video memory which i bought for Vista ( stupid, stupid me) ..
i had an Nvidia GeForce card with 128 mb memory.
if i simply change it, how will it affect the system?
i installed beryl with the ati tutorial and it didn't work (xgl) .. will i have to roll back the installation of beryl, or will it just work?

---

### Post by STREETURCHINE on 2007-02-19
yes i think if you put the nvidia card in ,you will have to install the drivers for nvidia,
then reinstall beryl,

---

### Post by anaconda on 2007-02-19
I would uninstall beryl, then shutdown, change the videocard, Then boot to recovery mode
and install Nvidia drivers following these instructions: 

Make sure you have both the Universe and Multiverse repositories enabled.
sudo apt-get install nvidia-glx
sudo nvidia-xconfig

Then reboot and reinstall beryl..

More info:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by Patrick K on 2007-02-19
If the ATI card is already installed and you are changing to Nvidia, before shutting down, edit the line in xorg.conf that says "ati" (or something like that, whatever the ATI driver is called) to "nv". That way when you boot up, the nvidia card will have a working driver. If going the other way, reverse this. If you don't do this, you will be kicked to a command line interface upon booting and will have to do it from there.

Once the system is running, use the ENVY Script to install the nvidia or ati drivers (the newest version works for both). I would suggest using Envy to remove the old drivers since you won't need them anymore. As for beryl, I don't know, maybe disable it or uninstall it till you get the proper driver installed. 

If you have another OS on the system, be sure to deal with it. In Windows, you should change the driver to VGA and uninstall the ATI drivers before installing the card.

---

### Post by panti19 on 2007-02-19
heeelp.
i changed the xorg.config so that it contained "nv" , but it didn't load the system..
i logged in and typed sudo apt-get install nvidia-glx..
it downloaded the packae,but then i get this error:


dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.7-11.1_i386.deb (--unpack):
subprocess pre-installation script returned error exit status 2
Errors were encountered while processing /var/cache/apt/archives/nvidia-glx_1.0.8776+2.6.17.7-11.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

heeelp:confused:

---

### Post by taurus on 2007-02-19
Boot into recovery mode and change the Driver to **vesa** in /etc/X11/xorg.conf.  Reboot and install nVidia driver with this guide.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by panti19 on 2007-02-19
/etc/X11/xorg.conf: Permission denied
i logged in with the login command
and it said the same thing

---

### Post by taurus on 2007-02-19
```
nano -Bw /etc/X11/xorg.conf
```
And when you are done editing, hold down <Ctrl> and press x to exit.  Then Y to the question and Return key.  Reboot and see if X is running again.

```
shutdown -r now
```

---

### Post by panti19 on 2007-02-19
the file is empty :confused:

---

### Post by taurus on 2007-02-19
What's the output of this command then?

```
ls -la /etc/X11
```

---

### Post by panti19 on 2007-02-19
it's alot to type :) , but it contains (related to xorg) these lines:

-rw-r--r-- 1 root root 5139 2007-02-19 19:39 xorg.conf
-rw-r--r-- 1 root root 5142 2007-02-19 19:39 xorg.conf~
-rw-r--r-- 1 root root 4377 2007-02-19 19:39 xorg.conf_backup_200702151749
-rw-r--r-- 1 root root 5016 2007-02-19 19:39 xorg.conf.fglrx-0
-rw-r--r-- 1 root root 4441 2007-02-19 19:39 xorg.conf.original-0

---

### Post by taurus on 2007-02-19
> **panti19 said:**
> it's alot to type :) , but it contains (related to xorg) these lines:

-rw-r--r-- 1 root root 5139 2007-02-19 19:39 xorg.conf
-rw-r--r-- 1 root root 5142 2007-02-19 19:39 xorg.conf~
-rw-r--r-- 1 root root 4377 2007-02-19 19:39 xorg.conf_backup_200702151749
-rw-r--r-- 1 root root 5016 2007-02-19 19:39 xorg.conf.fglrx-0
-rw-r--r-- 1 root root 4441 2007-02-19 19:39 xorg.conf.original-0

I don't know why you said it was empty because there it is.

```
-rw-r--r-- 1 root root **_[COLOR="Red"]5139[/COLOR]_** 2007-02-19 19:39 xorg.conf
```

Try it again.

```
nano -Bw /etc/X11/xorg.conf
```

---

### Post by panti19 on 2007-02-19
no waay. now i o into the file.. i edit to driver and change it to "vesa"
and now when i want to save it says:
Error writing /etc/X11/xorg.conf: Permission denied

---

### Post by taurus on 2007-02-19
Are you in a recovery mode?  If not, then you need to use the sudo command.

```
sudo nano -Bw /etc/X11/xorg.conf
```

---

### Post by panti19 on 2007-02-19
ok. i did it ,but now should it boot into GNOME , 'cause apparently it doesn't , it just takes me back to the terminal?

---

### Post by taurus on 2007-02-19
What happens when you type this from a prompt?

```
startx
```

---

### Post by panti19 on 2007-02-19
it doesn't start the X window.
i think i know what the problem is.
i installed beryl using a tutorial for ati.
i changed then the "ati" to "fglrx" in 2 places
now i only changed it to vesa in only one.
i think i should change it in both

and i chaned it and still doesnt work

---

### Post by taurus on 2007-02-19
Or you want to use the original xorg.conf instead.

```
-rw-r--r-- 1 root root 4441 2007-02-19 19:39 xorg.conf.original-0
```

```
sudo cp /etc/X11/xorg.conf.original-0  /etc/X11/xorg.conf
startx
```

---

### Post by panti19 on 2007-02-19
i think i'm gonna reinstall ubuntu.
it's much easier.
i will load the live cd and copy the files i want to my ipod and i'm done
on second thought, no :)

---

### Post by panti19 on 2007-02-19
i couldn't get the cd working. i've burned it at 4x and it didn't work..
ok..
what's next?

---

### Post by taurus on 2007-02-19
Boot into recovery mode and at the prompt, run

```
dpkg-reconfigure xserver-xorg
```
And if you are not sure about a question, just use the default and use **vesa** driver for now.

---

### Post by panti19 on 2007-02-19
it worked. i chaned to vesa, double checked..and it booted finally, thanks
shouldn't i just install the nvidia drivers using Add/Remove or with EasyUbuntu?

---

### Post by taurus on 2007-02-19
> **panti19 said:**
> it worked. i chaned to vesa, double checked..and it booted finally, thanks
shouldn't i just install the nvidia drivers using Add/Remove or with EasyUbuntu?

I thought you have an ATI graphic card!  

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by panti19 on 2007-02-19
yes..but i changed it to an nvidia card. :)

---

### Post by taurus on 2007-02-19
The link in my previous post would apply for nVidia card too.

---

### Post by panti19 on 2007-02-19
i followed the tutorial and after downloading the driver i get this in the terminal:

Unpacking linux-restricted-modules-2.6.17-11-386 (from .../linux-restricted-modules-2.6.17-11-386_2.6.17.12-1_i386.deb) ...
Unpacking nvidia-glx (from .../nvidia-glx_1.0.9746+2.6.17.12-1_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1.0.9746+2.6.17.12-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1.0.9746+2.6.17.12-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by panti19 on 2007-02-19
it said to enable Universe and Multivers repositories.
how do i do that?

---

### Post by taurus on 2007-02-19
[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

---

### Post by panti19 on 2007-02-19
they were enabled ..
so what's the problem, then?:(

---

### Post by punkybouy on 2007-02-19
Install Automatix and then have it install your nvidia drivers, PLUS you can have Automatix install a lot more too.

---

### Post by taurus on 2007-02-19
Did you remember to press Reload?  Otherwise, post the output of this command here?

```
cat /etc/apt/sources.list
```

---

### Post by panti19 on 2007-02-19
i reloaded ..twice..
i even tried automatix and it didn't work:confused:

---

### Post by panti19 on 2007-02-19
i opened xorg.conf and it still thinks i have an ATI radeon card (vesa driver):confused: 
i think that's why i can't install the NVIDIA drivers.
how do i make it "know" i have an Nvidia card?

---

### Post by Repent on 2007-02-19
Have you tried this? [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

---

