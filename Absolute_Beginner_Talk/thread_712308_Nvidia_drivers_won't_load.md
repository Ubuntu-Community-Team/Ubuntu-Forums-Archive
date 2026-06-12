---
title: "Nvidia drivers won't load"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by TattooedRunes on 2008-03-01
After downloading the drivers from nVidia, I can't seem to get Ubuntu to recognize them... is there possibly a set of instructions out there that one of you would be kind enough to direct me in the general direction of?

BTW, when trying to run the driver package, I am getting this error:

Could not open the file /home/bmac/Desktop/NVIDI…Linux-x86-169.09-pkg1.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

I know this is probably a total newb request but I am frustrated and I really would appreciate any help.  Thanks.

---

### Post by FrozenFox on 2008-03-01
If you are NOT using ubuntu 8.04 Hardy (the testing version. unless you specifically looked for the testing version, you probably have gutsy and envy will work fine), the best and easiest way to install them is to download and install envy (envy ng is being made for hardy, but its not available yet). Envy can install one of multiple versions of the nvidia drivers. Note that if you have problems, you may want to uninstall the drivers with envy and install a different version (for instance, I have issues with the newest drivers with massive texture glitches in ut2004 and such, so i stick with the older 100.x drivers. they work just fine for some people though.)

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

And run it. It is a piece of cake.

---

### Post by Rocket2DMn on 2008-03-01
Did you try to install the restricted drivers from within Ubuntu by going to System->Administration->Restricted Drivers Manager?
If you're set on installing from nvidia's file, this is how you're supposed to go about it (it is not for the timid):
```
sudo apt-get remove nvidia-glx nvidia-new-glx
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
^^ignore any file not found errors ^^
sudo apt-get install linux-headers-`uname -r` build-essential xserver-xorg-dev
```
CTRL+ALT+F1 to get to a tty
```
sudo /etc/init.d/gdm stop
sudo chmod +x /path/to/NVIDIA*
sudo /path/to/NVIDIA*
sudo /etc/init.d/gdm start
```
Now in the GUI, open a terminal and run
```
gksu nvidia-settings
```

This is not terribly easy, I would suggest using the Restricted Drivers manager first.  I hear envy is really convenient, but you should note that you will need to uninstall envy before doing a dist-upgrade to Hardy when it is released.

---

### Post by TattooedRunes on 2008-03-01
Actually already one step ahead of you on that one.

I tried running that and I get this error:

Error: Dependency is not satisfiable: xserver-xorg-dev


...BTW I am running Gutsy

---

### Post by TattooedRunes on 2008-03-01
> **Rocket2DMn said:**
> Did you try to install the restricted drivers from within Ubuntu by going to System->Administration->Restricted Drivers Manager?
If you're set on installing from nvidia's file, this is how you're supposed to go about it (it is not for the timid):
```
sudo apt-get remove nvidia-glx nvidia-new-glx
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
^^ignore any file not found errors ^^
sudo apt-get install linux-headers-`uname -r` build-essential xserver-xorg-dev
```
CTRL+ALT+F1 to get to a tty
```
sudo /etc/init.d/gdm stop
sudo chmod +x /path/to/NVIDIA*
sudo /path/to/NVIDIA*
sudo /etc/init.d/gdm start
```
Now in the GUI, open a terminal and run
```
gksu nvidia-settings
```

This is not terribly easy, I would suggest using the Restricted Drivers manager first.  I hear envy is really convenient, but you should note that you will need to uninstall envy before doing a dist-upgrade to Hardy when it is released.

I'm gonna newb myself again, but here goes: Where am I inputting this code?  I know how to get to the terminal but is this something different?

The restricted drivers screen in the GUI gives me this error message:
The software source for the package

   nvidia-glx-new

 is not enabled.

---

### Post by Rocket2DMn on 2008-03-01
OK, start by going to System->Administration->Software Sources and checking the boxes for universe, multiverse, and proprietary (restricted), then close.  It should ask you to "update", so do that, otherwise you need to run "sudo apt-get update" in a terminal.
Open a regular terminal and start running the code, one line at a time.
When I say do CTRL+ALT+F1 to get to a tty, make sure everything is saved and closed because we are going to stop GNOME.  Run those 4 lines from the tty (the black screen terminal you see, you will have to log in first).
Then once back in the GUI, you can run the nvidia-settings command from a regular terminal.

---

