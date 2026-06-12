---
title: "8800gts nvidia with gnome"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by prostock3 on 2007-06-26
Hi,

I've been trying to get gnome installed for a while but with no success.  I think it has to do with my 8800gts nvidia video card.

First i installed my video card via instruction from another post:
1.  sudo apt-get install nvidia-glx-new
2.  wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)
3.  sh NVIDIA-Linux-x86-1.0-9755-pkg1.run -x
4.  cp -f NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules
5.  cd /usr/lib/xorg/modules
6.  sudo ln -s libnvidia-wfb.so.1.0.9755 libwfb.so
7.  sudo nvidia-glx-config enable

Then I installed gnome with:

apt-get install x-window-system-core xserver-xorg gnome-desktop-environment 


I get error message when trying to run startx:
FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to kiad the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
         after 0 requests (0 known processed) with 0 events remaining.


Does anyone know how I go about debugging this?

Thanks!:popcorn:

---

### Post by avik on 2007-06-26
Can you post your /etc/X11/xorg.conf file?

---

### Post by bodhi.zazen on 2007-06-26
Well, I install it like this :

```
sudo aptitude install build-essential xserver-xorg-dev linux-headers-`uname -r`
sudo sh ./NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

Note those tics are NOT single quotes ' they are just to the left of the number "1" key `

I may have forgotten a dependency, but I that should get you most of the way :)

---

### Post by prostock3 on 2007-06-26
i dont know yet how to get /etc/X11/xorg.conf  from my server...i don't have putty yet..is there a way without installing ssh?


also, tried the installation method u use, but i still get the same error about the kernel not being found.

Do you still have to do the following steps with your method?
4. cp -f NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules
5. cd /usr/lib/xorg/modules
6. sudo ln -s libnvidia-wfb.so.1.0.9755 libwfb.so


Thanks again,

---

### Post by BobCFC on 2007-06-26
I have an 8800GTS it works great don't despair!  

You seem to be downloading the Legacy driver for old cards 

> 
Latest Version: **100.14.11** 
Latest Legacy GPU version (1.0-71xx series)



The 8800 series should be using the newest drivers in the 100.xx.xx family.


I am using the latest drivers from Nvidia website. I had to **remove the ubuntu restricted drivers completely via Synaptic**.  Otherwise when you reboot it will say kernel mismatch

Here is the latest driver for [x86 (32bit)]("http://us.download.nvidia.com/XFree86/Linux-x86/100.14.11/NVIDIA-Linux-x86-100.14.11-pkg1.run")

Here is the latest driver for [x86_64 (64bit)]("http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.11/NVIDIA-Linux-x86_64-100.14.11-pkg2.run")


run with 
```

sudo sh NVIDIA-Linux-MYVERSION.run     
```

where MYVERSION is either 32bit or 64bit.. (you can use tab to autocomplete)

Then installer will ask questions..  On mine it had to Compile new module.  I just click yes yes yes.. takes a few minutes. Makes changes to xorg.conf for you.

Then I could boot into X.   Nvidia gives you a nice control panel to set resolution or activate Twinview for Dual Monitors.

When in X  type  
```

gksudo nvidia-settings
```

Click save changes to xorg.conf or something.


EDIT:  I am going to bed soon it's nearly 7am in London I will check back here when I wake up

 [Here]("http://www.nvidia.com/object/unix.html") is the main page with all the Nvidia drivers
 [Here]("http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14") are the Nvidia Linux forums where you can get help find out about new drivers

---

### Post by bodhi.zazen on 2007-06-26
No, you can skip those steps.

---

### Post by prostock3 on 2007-06-26
thanks all.

i went to the website and got the latest driver and it worked fine.  one thing when i startx though...the window is larger than my screen size(i have 19 inch)..at window start up it said it could not resize..do i need to just simply change the resolution?

---

### Post by BobCFC on 2007-06-26
Good to hear!

There is a nice nvidia control panel for changing resolution, refresh rates etc.

press Alt-F2 and type 

```
gksudo nvidia-settings
```


Save settings to xorg.conf with the button when you're done

---

### Post by bodhi.zazen on 2007-06-26
> **BobCFC said:**
> Good to hear!

There is a nice nvidia control panel for changing resolution, refresh rates etc.

press Alt-F2 and type 

```
gksudo nvidia-settings
```


Save settings to xorg.conf with the button when you're done

**[size=2]THANK YOU[/size]** for spreading the word re: gksudo nvidia-settings

Old habits (manual edit of xorg.conf) are hard to break ;)

People "forget" to run nvidia-settings as root (thus they can not save the changes).

---

### Post by heldal on 2007-06-28
> **prostock3 said:**
> Hi,

I've been trying to get gnome installed for a while but with no success.  I think it has to do with my 8800gts nvidia video card.

First i installed my video card via instruction from another post:
1.  sudo apt-get install nvidia-glx-new
2.  wget [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)
3.  sh NVIDIA-Linux-x86-1.0-9755-pkg1.run -x
4.  cp -f NVIDIA-Linux-x86-1.0-9755-pkg1/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/lib/xorg/modules
5.  cd /usr/lib/xorg/modules
6.  sudo ln -s libnvidia-wfb.so.1.0.9755 libwfb.so
7.  sudo nvidia-glx-config enable

Then I installed gnome with:

apt-get install x-window-system-core xserver-xorg gnome-desktop-environment 



Unless you reboot before trying to start the X-server you may have to manually load the kernel-module installed in step 1 above using e.g.  "sudo modprobe nvidia"

---

### Post by sirius11 on 2007-07-01
how could someone install a  driver,  or write down any sudo command in a console when we don't even have an image to begin with..
total dark screen when trying to install

---

### Post by BobCFC on 2007-07-03
> **sirius11 said:**
> how could someone install a  driver,  or write down any sudo command in a console when we don't even have an image to begin with..
total dark screen when trying to install


I had a similar problem.  If you press F6 at the menu to edit the boot options you can change SPLASH to **NOSPLASH** which bypasses the logo so you can see what is happening underneath.  You can also remove the QUIET option to get even more detailed text if you are looking for error messages.   You can find them in a file called something like **/var/log/casper.log**

use *more* to read such as

```
more /var/log/casper.log
```

You can use enter/spacebar to scroll and **q** to quit.

Another idea if you have trouble starting the desktop is picking a different VGA mode to get started such as Vesa.  You can install proper drivers later.

If still stuck try the Alternate install CD with uses text mode installer instead of LiveCD.


If you have similar problems post install choose Recovery Mode from the boot menu and you will reach a command prompt where you can install drivers as root.

---

