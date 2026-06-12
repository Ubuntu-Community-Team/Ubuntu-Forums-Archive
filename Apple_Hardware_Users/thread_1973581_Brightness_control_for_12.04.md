---
title: "Brightness control for 12.04"
date: 2012-05-05
forum: Apple Hardware Users
---

### Post by Hatsune Miku on 2012-05-05
Hey everyone, is there a solution yet for brightness control on Macbook Pro/Air yet for 12.04? I cannot for the life of me get it working with the NVIDIA drivers.

---

### Post by DanTheDane on 2012-05-05
It's working great here on a MacBook Pro 6,2 using the recommended version of the Nvidia drivers (Nvidia-current).

Just before I upgraded to 12.04 yesterday from 11.10, I had an issue after an update to the Nvidia drivers, which resulted in the brightness not working (full power all the time) which continued after the upgrade to 12.04.

I then removed all traces of the Nvidia driver and deleted the xorg.conf file. After a reboot I re-installed the nvidia-current driver and ran nvidia-xconfig. Since then I haven't had any issues.

---

### Post by Hatsune Miku on 2012-05-05
Ill try doing that, as I did the same thing. Installed the latest NVIDIA drivers. Could you write a small step-by-step for me, just so I dnt miss anything? :)

---

### Post by DanTheDane on 2012-05-05
No Problem.

First back up your current xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then run the following command in the terminal:
```
dpkg-query -l  'nvidia*' | grep ii
```
This will find all nvidia packages installed. Mine gave the following output:
```

ii  nvidia-common                                  1:0.2.44                                      Find obsolete NVIDIA drivers
ii  nvidia-current                                 295.40-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                                295.33-0ubuntu1                               Tool of configuring the NVIDIA graphics driver

```

I know that Ubuntu desktop depends on nvidia-common, so DON'T delete that!. But based on my output I would then run:
```
sudo apt-get purge nvidia-current nvidia-settings
```
It will first tell you which packages it will remove. Ensure that no unexpected packages will be removed.
The above command will remove the nvidia drivers including config files.

After this, reboot the computer (or restart X) to ensure that everything is safely uninstalled. 
Then remove the xorg.conf file, to ensure that the Nvidia configuration don't use this as a base:
```
sudo rm /etc/X11/xorg.conf
```

After this run the following command to install the Nvidia drivers:
```
sudo apt-get install nvidia-current nvidia-settings
```

And then run the following command to create the xorg.conf file:
```
sudo nvidia-xconfig
```
Reboot, and enjoy a working setup :-)

It can probably be fixed much easier, but this is the steps I used. Also be aware that you could risk loosing your graphical environment if you're doing something wrong.

---

### Post by Hatsune Miku on 2012-05-05
> **DanTheDane said:**
> No Problem.

First back up your current xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then run the following command in the terminal:
```
dpkg-query -l  'nvidia*' | grep ii
```
This will find all nvidia packages installed. Mine gave the following output:
```

ii  nvidia-common                                  1:0.2.44                                      Find obsolete NVIDIA drivers
ii  nvidia-current                                 295.40-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                                295.33-0ubuntu1                               Tool of configuring the NVIDIA graphics driver

```

I know that Ubuntu desktop depends on nvidia-common, so DON'T delete that!. But based on my output I would then run:
```
sudo apt-get purge nvidia-current nvidia-settings
```
It will first tell you which packages it will remove. Ensure that no unexpected packages will be removed.
The above command will remove the nvidia drivers including config files.

After this, reboot the computer (or restart X) to ensure that everything is safely uninstalled. 
Then remove the xorg.conf file, to ensure that the Nvidia configuration don't use this as a base:
```
sudo rm /etc/X11/xorg.conf
```

After this run the following command to install the Nvidia drivers:
```
sudo apt-get install nvidia-current nvidia-settings
```

And then run the following command to create the xorg.conf file:
```
sudo nvidia-xconfig
```
Reboot, and enjoy a working setup :-)

It can probably be fixed much easier, but this is the steps I used. Also be aware that you could risk loosing your graphical environment if you're doing something wrong.

AWESOME! I'll give this a try when I get home, I thought it was going to be something like this, but I would of probably deleted the NVIDIA-Common(Been out of the Linux game for about 2 years, until recent). Thank you!

---

### Post by DanTheDane on 2012-05-05
You're welcome.

If you by accident include nvidia-common, you would see that it would try to uninstall ubuntu-desktop as well. As explained, if it tells you that it will install other things than what you have specified, you definitely should ensure that it's not some vital packages....

After removing the drivers and rebooted, you can also re-install them by using the additional drivers program, and select it from that. You still however still need to run nvidia-xconfig afterwards to have the xorg.conf file configured.

---

### Post by Hatsune Miku on 2012-05-05
> **DanTheDane said:**
> You're welcome.

If you by accident include nvidia-common, you would see that it would try to uninstall ubuntu-desktop as well. As explained, if it tells you that it will install other things than what you have specified, you definitely should ensure that it's not some vital packages....

After removing the drivers and rebooted, you can also re-install them by using the additional drivers program, and select it from that. You still however still need to run nvidia-xconfig afterwards to have the xorg.conf file configured.

That I do remember, I used to be a Hard core debian user, till I had to stop a bit as my job required a Windows environment. But now they have UNIX support I'm moving back to a Linux/Mac multi :)

---

### Post by Hatsune Miku on 2012-05-05
Just tried it, didnt work my friend :/

---

### Post by DanTheDane on 2012-05-05
And the nvidia driver is the active one? (run nvidia-settings. it will complain if that's not the driver used).

Below is my xorg.conf, if it's of any use (notice that the lines "Option  "Coolbits" "1"" & "Option  "RegistryDwords" "PowerMizerEnable=0x1;" is not necessary. They are just to ensure that the GPU run in powersave mode)

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.40  (buildmeister@swio-display-x86-rhel47-06.nvidia.com)  Thu Apr  5 22:40:54 PDT 2012

Section "Screen"
	Identifier     "Default Screen"
	Device         "Device0"
	SubSection "Display"
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "keyboard"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Device0"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
	Option	"NoLogo"	"True"
	Option  "Coolbits" "1"
	Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x3; PowerMizerDefaultAC=0x3"
EndSection

```

Edit: Noticed that I have been pretty lazy when I originally edited my xorg.conf file. So it references a default layout, screen keyboard and mouse, which I removed, but the system haven't complained :-) )

---

### Post by Hatsune Miku on 2012-05-05
> **DanTheDane said:**
> And the nvidia driver is the active one? (run nvidia-settings. it will complain if that's not the driver used).

Below is my xorg.conf, if it's of any use (notice that the lines "Option  "Coolbits" "1"" & "Option  "RegistryDwords" "PowerMizerEnable=0x1;" is not necessary. They are just to ensure that the GPU run in powersave mode)

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 295.40  (buildmeister@swio-display-x86-rhel47-06.nvidia.com)  Thu Apr  5 22:40:54 PDT 2012

Section "Screen"
	Identifier     "Default Screen"
	Device         "Device0"
	SubSection "Display"
		Modes      "nvidia-auto-select"
	EndSubSection
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "keyboard"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Device0"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
	Option	"NoLogo"	"True"
	Option  "Coolbits" "1"
	Option  "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2222; PowerMizerLevel=0x3; PowerMizerDefaultAC=0x3"
EndSection

```

Edit: Noticed that I have been pretty lazy when I originally edited my xorg.conf file. So it references a default layout, screen keyboard and mouse, which I removed, but the system haven't complained :-) )

I saw a different entry for the keyboard drivers. I modified it to match your settings, rebooting now.

EDIT: Nope :/

---

### Post by DanTheDane on 2012-05-05
BTW: Are you able to adjust the brightness under system settings -> brightness? (I wasn't when I had the issue)

---

### Post by DanTheDane on 2012-05-05
This has not been necessary for me, but maybe it could help you:

[http://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver](http://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver)

---

### Post by Hatsune Miku on 2012-05-05
> **DanTheDane said:**
> This has not been necessary for me, but maybe it could help you:

[http://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver](http://askubuntu.com/questions/76081/brightness-not-working-after-installing-nvidia-driver)

Got it working from installing the old Nvidia-bl packages from the Mactel repo for Natty. Everything seems to be working fine and no derps from the drivers.

Thanks for all the help you gave me!!!

---

### Post by DanTheDane on 2012-05-05
Glad to hear you got it working!

You're welcome (although none of my suggestions worked :-) )

---

### Post by Hatsune Miku on 2012-05-05
> **DanTheDane said:**
> Glad to hear you got it working!

You're welcome (although none of my suggestions worked :-) )

Hey, it was something, and it did lead me to suspect it was missing a driver call. Either way you did something :)

Also Are you in BIOS or EFI mode?

---

### Post by DanTheDane on 2012-05-06
To be honest I'm actually a little unsure. 
I initially tried to install it via USB, which I had to drop because of too many issues, and ended using an install DVD instead. So I think I'm in bios mode, but again I'm not sure.....

---

### Post by soumadeep on 2012-05-07
[QUOTE=Originally Posted by DanTheDane  
No Problem.

First back up your current xorg.conf file:
Code:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
Then run the following command in the terminal:
Code:
dpkg-query -l  'nvidia*' | grep ii
This will find all nvidia packages installed. Mine gave the following output:
Code:
ii  nvidia-common                                  1:0.2.44                                      Find obsolete NVIDIA drivers
ii  nvidia-current                                 295.40-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                                295.33-0ubuntu1                               Tool of configuring the NVIDIA graphics driver
I know that Ubuntu desktop depends on nvidia-common, so DON'T delete that!. But based on my output I would then run:
Code:
sudo apt-get purge nvidia-current nvidia-settings
It will first tell you which packages it will remove. Ensure that no unexpected packages will be removed.
The above command will remove the nvidia drivers including config files.

After this, reboot the computer (or restart X) to ensure that everything is safely uninstalled. 
Then remove the xorg.conf file, to ensure that the Nvidia configuration don't use this as a base:
Code:
sudo rm /etc/X11/xorg.conf
After this run the following command to install the Nvidia drivers:
Code:
sudo apt-get install nvidia-current nvidia-settings
And then run the following command to create the xorg.conf file:
Code:
sudo nvidia-xconfig
Reboot, and enjoy a working setup 

It can probably be fixed much easier, but this is the steps I used. Also be aware that you could risk loosing your graphical environment if you're doing something wrong.[/QUOTE]




Well I apparently did something wrong.Now I have lost my graphical interface on Ubuntu 12.04.Any suggestions on how to bring it back ???

---

### Post by soumadeep on 2012-05-07
> **DanTheDane said:**
> No Problem.

First back up your current xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then run the following command in the terminal:
```
dpkg-query -l  'nvidia*' | grep ii
```
This will find all nvidia packages installed. Mine gave the following output:
```

ii  nvidia-common                                  1:0.2.44                                      Find obsolete NVIDIA drivers
ii  nvidia-current                                 295.40-0ubuntu1                               NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                                295.33-0ubuntu1                               Tool of configuring the NVIDIA graphics driver

```

I know that Ubuntu desktop depends on nvidia-common, so DON'T delete that!. But based on my output I would then run:
```
sudo apt-get purge nvidia-current nvidia-settings
```
It will first tell you which packages it will remove. Ensure that no unexpected packages will be removed.
The above command will remove the nvidia drivers including config files.

After this, reboot the computer (or restart X) to ensure that everything is safely uninstalled. 
Then remove the xorg.conf file, to ensure that the Nvidia configuration don't use this as a base:
```
sudo rm /etc/X11/xorg.conf
```

After this run the following command to install the Nvidia drivers:
```
sudo apt-get install nvidia-current nvidia-settings
```

And then run the following command to create the xorg.conf file:
```
sudo nvidia-xconfig
```
Reboot, and enjoy a working setup :-)

It can probably be fixed much easier, but this is the steps I used. Also be aware that you could risk loosing your graphical environment if you're doing something wrong.
Well I apparently did something wrong.Now I have lost my graphical interface on Ubuntu 12.04.Any suggestions on how to bring it back ???

---

### Post by needtosearchforum on 2012-05-10
Cant seem to get this working. I have added the options to xorg.conf but brightness controll doesnt work. If i add the option "nvidia" my screen goes black on reboot and i have to revert the changes by booting the USB stick.

Im running ubuntu 12.04 on my Macbook 5.5.

---

