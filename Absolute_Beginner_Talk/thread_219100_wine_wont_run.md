---
title: "wine wont run"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Corey4666 on 2006-07-19
after installing wine with synaptic i configured it and then installed mame32k.exe on it dont tell me about a mame made for linux i seen it but i wanna use the windows version so i can play online i installed mame32k.exe and then it made a mame32k.Ink or .lnk i dunno what extension on my desktop so i tryed running it to play mame and it says "couldent display /home/corey4666/desktop/mame32k.lnk" i dont know how to run programs on wine once i install them here is the terminal's info that happened when i installed mame using wine

> corey4666@corey4666-desktop:~$ winecfg
wine: creating configuration directory '/home/corey4666/.wine'...
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:process_attach Could not create default context.
Xlib:  extension "GLX" missing on display ":0.0".
wine: '/home/corey4666/.wine' created successfully.
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
corey4666@corey4666-desktop:~$ wine /home/corey4666/Desktop/Stuff/mame32-067-414-ka09.exe
err:menubuilder:extract_icon32 LoadLibraryExW (L"C:\\Program Files\\MAME32k\\uninst.exe") failed, error 126
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
corey4666@corey4666-desktop:~$ winecfg
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
corey4666@corey4666-desktop:~$


---

### Post by Kilz on 2006-07-19
> Xlib: extension "GLX" missing on display ":0.0".

[You may need to install/update the binary drivers for your graphics card.]("https://help.ubuntu.com/community/BinaryDriverHowto")

---

### Post by Corey4666 on 2006-07-19
im very new to linux i dont know what that is or how to do it could you kinda help me start out? find the binary drivers and how to install them?

---

### Post by Kilz on 2006-07-19
> **Corey4666 said:**
> im very new to linux i dont know what that is or how to do it could you kinda help me start out? find the binary drivers and how to install them?

What video card do you have?

---

### Post by Mangledbmx on 2006-07-19
i couldnt even get wine to install. maybe later ill try again.

---

### Post by Kilz on 2006-07-19
> **Mangledbmx said:**
> i couldnt even get wine to install. maybe later ill try again.

Open a terminal and type
```
sudo apt-get install wine
```
If you are running the AMD64 version of Ubuntu look in my signature.

---

### Post by Corey4666 on 2006-07-19
> **Mangledbmx said:**
> i couldnt even get wine to install. maybe later ill try again.
you new to linux also? i kinda found it easy once i read the directions carefully on there website


> What video card do you have?
sorry i should of said earlyer i have a Nvidia FX5200 :oops:  its a peice of junk i bought a 170$ card off the internet a few days ago but it dont fit in my pc cuz its a pci-e so im stuck with it still

---

### Post by Kilz on 2006-07-19
> **Corey4666 said:**
> you new to linux also? i kinda found it easy once i read the directions carefully on there website



sorry i should of said earlyer i have a Nvidia FX5200 :oops:  its a peice of junk i bought a 170$ card off the internet a few days ago but it dont fit in my pc cuz its a pci-e so im stuck with it still
Well we need to know what is installed in your system. :-D

---

### Post by Corey4666 on 2006-07-19
nvidia fx5200

---

### Post by Kilz on 2006-07-19
> **Corey4666 said:**
> nvidia fx5200

This page
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Will give you step by step instructions on how to set up the drivers.

---

### Post by Corey4666 on 2006-07-19
i didnt know which driver to pick so i put down the legacy driver and then i did the next step and it gave me this error im using intel i dunno if that matters cuz i skipped the steps that had the words AMD in them

> corey4666@corey4666-desktop:~$ sudo nvidia-glx-config enable
Password:

Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
corey4666@corey4666-desktop:~$


---

### Post by Corey4666 on 2006-07-20
Bump? :confused:  ](*,)

---

### Post by henderb on 2006-07-20
you want the "nvidia" driver.
```
sudo gedit /etc/X11/xorg.conf
```
in this file you should find a
```
Section "Device"
```
with a
```
Driver "nv"
```
change the Driver to 
```
Driver "nvidia"
```

---

### Post by Corey4666 on 2006-07-21
this is what it says

> Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

should i change "vesa" to nvidia or whatever you said to change it to?

---

### Post by Corey4666 on 2006-07-21
Bump..? :neutral:

---

### Post by digby on 2006-07-21
yes - change vesa to nvidia

---

### Post by Lord Illidan on 2006-07-21
Do not use the nvidia legacy driver, though! Your card may be old, but it is still not legacy. legacy = riva TNT and all that.

---

### Post by Corey4666 on 2006-07-21
> yes - change vesa to nvidia
Done that now thx for help 


> **Lord Illidan said:**
> Do not use the nvidia legacy driver, though! Your card may be old, but it is still not legacy. legacy = riva TNT and all that.
i got rid of the legacy and used the other one thx for help


im stuck on a step 6 i dont know what to install im using a intel p4 and im using ubuntu not xubuntu or kubuntu or whatever else there is 
(only reason i mentioned the intel is cuz i see that it says image-amd-64-k8 im guessing it has to do with amd processor?)
> 
STEP 6
Find the appropriate module for your kernel. For example, if you have linux-image-amd64-k8 installed, then you should install linux-restricted-modules-amd64-k8.


---

### Post by Corey4666 on 2006-07-21
btw i installed automatix and install latest nvidia drivers when i boot linux is shows the nvidia splash screen so those are installed but im still confused on step 6 on what to pick

---

### Post by Corey4666 on 2006-07-22
Bump???

---

### Post by Corey4666 on 2006-07-28
well i got cedega instead of wine so nevermind

---

### Post by Corey4666 on 2006-08-09
i cedega to install world of warcraft then i went to log in and it said connecting thats all never goes past that screen so i use wine now to run it but it gets past connecting but then gets stuck at authenticating ](*,) 
can anyone help me i got the video drivers installed etc i dunno how to check if my wine version is the newest thats out someone help me out i just wanna make ubuntu my main os but i need to get these few problems out of the way

---

### Post by tuxcantfly on 2006-08-10
for the latest and greatest wine version check out

[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

---

### Post by tuxcantfly on 2006-08-10
really, the nvidia drivers shouldn't be that hard to set up.

sudo apt-get install nvidia-glx
sudo nvidia-xconfig

reboot, and you're done

---

