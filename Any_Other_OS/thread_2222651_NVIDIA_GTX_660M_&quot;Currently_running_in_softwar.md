---
title: "NVIDIA GTX 660M &quot;Currently running in software rendering&quot;"
date: 2014-05-07
forum: Any Other OS
---

### Post by andrew-miller57 on 2014-05-07
[COLOR=#333333][FONT=Lucida Grande]Recently installed Mint 16 on my Lenovo Y580 . After the headache of booting up and getting a black screen every time (fixed by adding nomodeset=1 boot parameter), I now get a message on my screen that says video acceleration is disabled and that I am operating in software rendering mode. I have been trolling the internet trying to find a solution and have gotten nowhere other than I have installed bumblebee.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]inxi -Gx gives me :

[/FONT][/COLOR]```
[COLOR=#2E8B57][FONT=Monaco]andrew@andrew-laptop ~ $ inxi -Gx[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Graphics:  Card-1: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]           Card-2: NVIDIA GK107M [GeForce GTX 660M] bus-ID: 01:00.0 [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]           X.Org: 1.14.5 drivers: vesa,intel (unloaded: fbdev) Resolution: 1920x1080@0.0hz [/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.3, 256 bits) GLX Version: 2.1 Mesa 9.2.1 Direct Rendering: Yes[/FONT][/COLOR]
```[COLOR=#333333][FONT=Lucida Grande]

[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]Please, any help would be much appreciated. I really enjoy this distro and don't want to move from it. [/FONT][/COLOR][IMG]http://forums.linuxmint.com/images/smilies/icon_biggrin.gif[/IMG]

[COLOR=#333333][FONT=Lucida Grande]Also, here is my bumblebee.conf
[/FONT][/COLOR][COLOR=#333333][FONT=Lucida Grande]
[/FONT][/COLOR]```
[COLOR=#2E8B57][FONT=Monaco]# Configuration file for Bumblebee. Values should **not** be put between quotes[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]## Server options. Any change made in this section will need a server restart[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# to take effect.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][bumblebeed][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# The secondary Xorg server DISPLAY number[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]VirtualDisplay=:8[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# Should the unused Xorg server be kept running? Set this to true if waiting[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# for X to be ready is too long and don't need power management at all.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]KeepUnusedXServer=false[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# The name of the Bumbleblee server group name (GID name)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]ServerGroup=bumblebee[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# Card power state at exit. Set to false if the card shoud be ON when Bumblebee[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# server exits.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]TurnCardOffAtExit=false[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# The default behavior of '-f' option on optirun. If set to "true", '-f' will[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# be ignored.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]NoEcoModeOverride=false[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# The Driver used by Bumblebee server. If this value is not set (or empty),[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# auto-detection is performed. The available drivers are nvidia and nouveau[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# (See also the driver-specific sections below)[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Driver=nvidia[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# Directory with a dummy config file to pass as a -configdir to secondary X[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]XorgConfDir=/etc/bumblebee/xorg.conf.d[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]## Client options. Will take effect on the next optirun executed.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][optirun][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# Acceleration/ rendering bridge, possible values are auto, virtualgl and[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# primus.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]Bridge=auto[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# The method used for VirtualGL to transport frames between X servers.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# Possible values are proxy, jpeg, rgb, xv and yuv.[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]VGLTransport=proxy[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# List of paths which are searched for the primus libGL.so.1 when using[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# the primus bridge[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]PrimusLibraryPath=/usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# Should the program run under optirun even if Bumblebee server or nvidia card[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# is not available?[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]AllowFallbackToIGC=false[/FONT][/COLOR]


[COLOR=#2E8B57][FONT=Monaco]# Driver-specific settings are grouped under [driver-NAME]. The sections are[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# detection resolves to NAME).[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# PMMethod: method to use for saving power by disabling the nvidia card, valid[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# values are: auto - automatically detect which PM method to use[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]#         bbswitch - new in BB 3, recommended if available[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]#       switcheroo - vga_switcheroo method, use at your own risk[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]#             none - disable PM completely[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]## Section with nvidia driver specific options, only parsed if Driver=nvidia[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][driver-nvidia][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# Module name to load, defaults to Driver if empty or unset[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]KernelDriver=nvidia[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]PMMethod=auto[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# colon-separated path to the nvidia libraries[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# comma-separated path of the directory containing nvidia_drv.so and the[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]# default Xorg modules path[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]XorgConfFile=/etc/bumblebee/xorg.conf.nvidia[/FONT][/COLOR]

[COLOR=#2E8B57][FONT=Monaco]## Section with nouveau driver specific options, only parsed if Driver=nouveau[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco][driver-nouveau][/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]KernelDriver=nouveau[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]PMMethod=bbswitch[/FONT][/COLOR]
[COLOR=#2E8B57][FONT=Monaco]XorgConfFile=/etc/bumblebee/xorg.conf.nouveau[/FONT][/COLOR]
```[COLOR=#333333][FONT=Lucida Grande]
[/FONT][/COLOR]

---

