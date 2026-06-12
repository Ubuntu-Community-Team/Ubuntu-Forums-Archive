---
title: "Randoly crashes Ubuntu6.06- Notebook compaq presario 1700"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by nnn25 on 2006-12-16
Hello,

I am new in UBUNTU. I installed it 3 weeks ago and till now everthing is fine, except the randons Crashes! I had tried many things about that but nothing improve the problem. I don't know where is the real source of the problem. I have a notebook Compaq Presario 1700.

It crash in a randonly way.

Please, I wonder if someone can give me some help about that.

Thanks
:confused:

---

### Post by Ecthelion on 2006-12-17
> It crash in a randonly way.

What do you mean with crashing?
Does your system just freezes or do you get a black screen or something.
Also, do you get any error?
Does this crashing happen since a period or was it always with your ubuntu install?

---

### Post by nnn25 on 2006-12-17
Thanks Ecthelion for the reply.

When the ubuntu crash, it doesn't let me do anything. I have to restart again the Notebook.

I don't get any error message.

This crash happen only in Ubuntu. I have dual boot, and in Windows the notebook work fine.

Thanks in advance for your replay to this message.

---

### Post by Ecthelion on 2006-12-18
> When the ubuntu crash, it doesn't let me do anything. I have to restart again the Notebook.

I don't get any error message.

As long as you don't have an error log it 'll be hard to help.

Some more questions:
*Can you move your mouse after it crashes? Or is everything freezed?
*When it crashes, does anything happen if you press Ctrl-Alt-Backspace
   (your xserver should normally restart)

If the answer on these two question is no mouse / nothing happens, then you'll have to search for logs.

Your logs can be found in /var/log/ .
The only way to see them (in Dapper) is to go with nautilus to /var/log/ and clicking on the logs and looking with the teksteditor for an error.

The logs in /var/log that you have to look to are:
auth.log
daemon.log
kern.log
messages
syslog
user.log
Xorg.0.log

Just use "find" to go to a date/time you know the system freezed on
If you see no error a that time (-5 min) just go to the next log.

If you find an error please post it here

---

### Post by nnn25 on 2006-12-18
Ok. 

On the next crash I will do that.

When it crash everthing is freezed and the Ctrl-Alt-Backspace does not work.

Really thnaks for the help.

As soon as possible, i will give you news about my problem.

Best Regards

---

### Post by nnn25 on 2006-12-19
Hello Ecthelion,

I had found the follows errors:

Xorg.o.log:

II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "pt"
(**) Generic Keyboard: XkbLayout: "pt"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(**) RADEON(0): RADEONSaveScreen(2)





daemon.log:

ec 18 21:32:33 localhost init: Switching to runlevel: 6
Dec 18 21:32:43 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Dec 18 21:32:49 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Dec 18 21:32:55 localhost sdpd[4631]: terminating...   
Dec 18 21:32:55 localhost hcid[4627]: Exit.
Dec 18 21:33:59 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 18 21:34:00 localhost gdm[4294]: gdm_slave_xioerror_handler: Erro X fatal - A reiniciar :0
Dec 18 21:34:04 localhost hcid[4654]: Bluetooth HCI daemon
Dec 18 21:34:04 localhost sdpd[4658]: Bluetooth SDP daemon 
Dec 18 21:34:04 localhost hcid[4654]: Can't get system message bus name: Connection ":1.1" is not allowed to own the service "org.bluez" due to security policies in the configuration file
Dec 18 21:34:04 localhost gdm[4384]: gdm_slave_xioerror_handler: Erro X fatal - A reiniciar :0
Dec 18 21:34:09 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Dec 18 21:34:09 localhost gdm[4700]: gdm_slave_xioerror_handler: Erro X fatal - A reiniciar :0
Dec 18 21:34:09 localhost gdm[4286]: deal_with_x_crashes: A executar o script XKeepsCrashing
Dec 18 21:34:21 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Dec 18 21:34:42 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 18 21:34:45 localhost dhclient: No DHCPOFFERS received.
Dec 18 21:34:45 localhost dhclient: No working leases in persistent database - sleeping.
Dec 18 21:34:45 localhost ntpdate[4951]: step time server 82.211.81.145 offset -0.444323 sec
Dec 18 21:35:28 localhost gdm[4286]: Várias tentativas falhadas, num curto espaço de tempo, ao tentar iniciar o servidor X; a desactivar o ecrã :0
Dec 18 21:40:31 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec 18 21:40:35 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 18 21:40:42 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 18 21:40:52 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 18 21:40:59 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 18 21:41:09 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 18 21:41:24 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 18 21:41:32 localhost dhclient: No DHCPOFFERS received.
Dec 18 21:41:32 localhost dhclient: No working leases in persistent database - sleeping.
Dec 18 21:46:06 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec 18 21:46:10 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec 18 21:46:14 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67



Since your last poste I had one freeze/crash. I will search for more errors when the system crash again.

Regards

---

### Post by Ecthelion on 2006-12-20
> (EE) xf86OpenSerial: Cannot open device /dev/wacom
No such file or directory.
Error opening /dev/wacom :** No such file or directory**
I have this error too in my Xorg.o.log, except that I have "success" instead of "No such file or directory"
I don't think the error is here

> Dec 18 21:34:09 localhost gdm[4700]: gdm_slave_xioerror_handler: Erro X fatal - A reiniciar :0
Dec 18 21:34:09 localhost gdm[4286]: deal_with_x_crashes: **A executar o script XKeepsCrashing**
This looks more like the wrongdoer to me. But I don't really know how to solve this without knowing which script crashes.
What I think is that this keeps crashing and after a while the whole system crashes.
If we could somehow find out which script crashes then we could blacklist it or fix it.

> Dec 18 21:35:28 localhost gdm[4286]: Várias tentativas falhadas, num curto espaço de tempo, ao tentar iniciar o servidor X; a desactivar o ecrã :0
Could you translate this? I'm not good in spanish...(is it Spanish?)
I understand "after failing multiple times in a short timespan, " , but I think it is what comes after that is interesting.

> Dec 18 21:46:14
Was it then that it crashed?

To be honest, I'm not a pro in this. Just trying to use my brains :-?  to find the error. So if someone else has ideas, please say so.

If it crashes more, post it. That'll give more info and keep this thread high in the list, so there is more chance that someone who knows more than I helps ;-)

I'll keep trying of course :)

---

### Post by nnn25 on 2006-12-20
First of all I want thank you for keep trying help me. That give me "courage" to still changing to Ubuntu and use less the Windows.

Second, why almost of the people confuse PORTUGAL as SPAIN? We are different. The text I wrote was in Portuguese, but I understand your doubt, our Write have some similar things than the Spanish... ... no problem :)


[I]Quote:
Dec 18 21:35:28 localhost gdm[4286]: Várias tentativas falhadas, num curto espaço de tempo, ao tentar iniciar o servidor X; a desactivar o ecrã :0[/I]

Could you translate this? I'm not good in spanish...(is it Spanish?)
I understand "after failing multiple times in a short timespan, " , but I think it is what comes after that is interesting.
[/I]

The translation is as you write: "After failing multiple times in a short timespan..." and "...when it tried to start the the server X; to deactivate the monitor: 0 "


I will post more errors, as soon as they appear.

Best Regards

---

### Post by Ecthelion on 2006-12-21
> Second, why almost of the people confuse PORTUGAL as SPAIN? We are different. The text I wrote was in Portuguese, but I understand your doubt, our Write have some similar things than the Spanish... ... no problem


Sorry mate. I've already been in Spain but never in Portugal, so I wouldn't know the difference.
(I mean in language of course)

> The translation is as you write: "After failing multiple times in a short timespan..." and "...when it tried to start the the server X; to deactivate the monitor: 0 "

There's something you could try... Although I don't really expect it to help, but maybe it's worth trying.
The problems you have are clearly something with your xserver. Maybe reconfiguring it could help.
I'm not sure it 'll help since it seems not really to be the xserver itself but more a script using it...
Anyway if you want to try to reconfigure:

Backup your old configuration:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back
```
If something goes wrong and you have no x after this just do this to have your old configuration back:
```
sudo cp /etc/X11/xorg.conf_back /etc/X11/xorg.conf
```

After backing up, reconfigure:
```
sudo dpkg-reconfigure xserver-xorg
```
Answer the questions you know, leave the other on the default answer

After this, restart your xserver:
```
sudo /etc/init.d/gdm restart
```

And wait till the next time it crashes.... Hopefully never. If it does, as you already know: post it :)

---

### Post by nnn25 on 2006-12-23
Hello Ecthelion,

I did want you said, but unfortnly it crashed.

1ºcrash before any chages:

USER.LOG
Dec 19 23:04:55 localhost gconfd (nunoct-5692): Resolvido o endereço "xml:readonly:/var/lib/gconf/defaults" para uma fonte de configuração apenas de leitura na posição 4
Dec 19 23:04:55 localhost gconfd (nunoct-5694): a iniciar (versão 2.14.0), pid 5694 utilizador 'nunoct'
Dec 19 23:04:55 localhost gconfd (nunoct-5694): Falha ao obter exclusividade no daemon, a terminar: Falha ao obter exclusividade sobre '/tmp/gconfd-nunoct/lock/ior': provavelmente outro processo tem a exclusividade ou o seu sistema operativo tem a exclusividade NFS de ficheiros mal configurada (Recurso temporariamente indisponível)
Dec 19 23:04:58 localhost shutdown[4292]: shutting down for system halt
Dec 21 21:07:41 localhost hpiod: 0.9.7 accepting connections at 49893... 
Dec 21 21:24:12 localhost gconfd (nunoct-5011): a iniciar (versão 2.14.0), pid 5011 utilizador 'nunoct'
Dec 21 21:24:12 localhost gconfd (nunoct-5011): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.mandatory" para uma fonte de configuração apenas de leitura na posição 0
Dec 21 21:24:12 localhost gconfd (nunoct-5011): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 1
Dec 21 21:24:12 localhost gconfd (nunoct-5011): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.defaults" para uma fonte de configuração apenas de leitura na posição 2
Dec 21 21:24:12 localhost gconfd (nunoct-5011): Resolvido o endereço "xml:readonly:/var/lib/gconf/debian.defaults" para uma fonte de configuração apenas de leitura na posição 3
Dec 21 21:24:12 localhost gconfd (nunoct-5011): Resolvido o endereço "xml:readonly:/var/lib/gconf/defaults" para uma fonte de configuração apenas de leitura na posição 4
Dec 21 21:24:17 localhost gconfd (nunoct-5011): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 0
Dec 21 21:38:47 localhost hpiod: 0.9.7 accepting connections at 44816... 
Dec 21 21:39:07 localhost gconfd (nunoct-4851): a iniciar (versão 2.14.0), pid 4851 utilizador 'nunoct'
Dec 21 21:39:07 localhost gconfd (nunoct-4851): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.mandatory" para uma fonte de configuração apenas de leitura na posição 0
Dec 21 21:39:07 localhost gconfd (nunoct-4851): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 1
Dec 21 21:39:07 localhost gconfd (nunoct-4851): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.defaults" para uma fonte de configuração apenas de leitura na posição 2
Dec 21 21:39:07 localhost gconfd (nunoct-4851): Resolvido o endereço "xml:readonly:/var/lib/gconf/debian.defaults" para uma fonte de configuração apenas de leitura na posição 3
Dec 21 21:39:07 localhost gconfd (nunoct-4851): Resolvido o endereço "xml:readonly:/var/lib/gconf/defaults" para uma fonte de configuração apenas de leitura na posição 4
Dec 21 21:39:13 localhost gconfd (nunoct-4851): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 0


XOR.0.LOG
*) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		10 256x256 slots
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 770)
(II) RADEON(0): Largest offscreen area available: 1024 x 1274
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): Detected Radeon Mobility M6, disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) Synaptics touchpad driver version 0.14.3
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad touchpad found
(**) RADEON(0): RADEONSaveScreen(2)
ProcXCloseDevice to close or not ?






Have a nice Christmas and a Happy Year 2007

Best Regards

---

### Post by nnn25 on 2006-12-23
2ºCrash-after server changes_23/12/2006- +/- 19H

USER,LOG
Dec 23 18:59:40 localhost hpiod: 0.9.7 accepting connections at 46506... 
Dec 23 18:59:58 localhost gconfd (nunoct-4852): a iniciar (versão 2.14.0), pid 4852 utilizador 'nunoct'
Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.mandatory" para uma fonte de configuração apenas de leitura na posição 0
Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 1
Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.defaults" para uma fonte de configuração apenas de leitura na posição 2
Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readonly:/var/lib/gconf/debian.defaults" para uma fonte de configuração apenas de leitura na posição 3
Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readonly:/var/lib/gconf/defaults" para uma fonte de configuração apenas de leitura na posição 4
Dec 23 19:00:04 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 0
Dec 23 19:04:27 localhost hpiod: 0.9.7 accepting connections at 40534... 
Dec 23 19:04:44 localhost gconfd (nunoct-4847): a iniciar (versão 2.14.0), pid 4847 utilizador 'nunoct'
Dec 23 19:04:44 localhost gconfd (nunoct-4847): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.mandatory" para uma fonte de configuração apenas de leitura na posição 0
Dec 23 19:04:44 localhost gconfd (nunoct-4847): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 1
Dec 23 19:04:44 localhost gconfd (nunoct-4847): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.defaults" para uma fonte de configuração apenas de leitura na posição 2
Dec 23 19:04:44 localhost gconfd (nunoct-4847): Resolvido o endereço "xml:readonly:/var/lib/gconf/debian.defaults" para uma fonte de configuração apenas de leitura na posição 3
Dec 23 19:04:44 localhost gconfd (nunoct-4847): Resolvido o endereço "xml:readonly:/var/lib/gconf/defaults" para uma fonte de configuração apenas de leitura na posição 4
Dec 23 19:04:50 localhost gconfd (nunoct-4847): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 0



MESAGES
Dec 23 18:57:01 localhost syslogd 1.4.1#17ubuntu7: restart.
Dec 23 18:59:36 localhost syslogd 1.4.1#17ubuntu7: restart.
Dec 23 18:59:36 localhost kernel: Inspecting /boot/System.map-2.6.15-27-386
Dec 23 18:59:36 localhost kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Dec 23 18:59:36 localhost kernel: Symbols match kernel version 2.6.15.
Dec 23 18:59:36 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Dec 23 18:59:36 localhost kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006
Dec 23 18:59:36 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Dec 23 18:59:36 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Dec 23 18:59:36 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Dec 23 18:59:36 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
Dec 23 18:59:36 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000000ff60000 (usable)
Dec 23 18:59:36 localhost kernel: [17179569.184000]  BIOS-e820: 000000000ff60000 - 000000000ff6fc00 (ACPI data)
Dec 23 18:59:36 localhost kernel: [17179569.184000]  BIOS-e820: 000000000ff6fc00 - 000000000ff80000 (ACPI NVS)
Dec 23 18:59:36 localhost kernel: [17179569.184000]  BIOS-e820: 000000000ff80000 - 0000000010000000 (reserved)
Dec 23 18:59:36 localhost kernel: [17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
Dec 23 18:59:36 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Dec 23 18:59:36 localhost kernel: [17179569.184000] 0MB HIGHMEM available.
Dec 23 18:59:36 localhost kernel: [17179569.184000] 255MB LOWMEM available.
Dec 23 18:59:36 localhost kernel: [17179569.184000] DMI present.
Dec 23 18:59:36 localhost kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x1008
Dec 23 18:59:36 localhost kernel: [17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:ef800000)
Dec 23 18:59:36 localhost kernel: [17179569.184000] Built 1 zonelists
Dec 23 18:59:36 localhost kernel: [17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
Dec 23 18:59:36 localhost kernel: [17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
Dec 23 18:59:36 localhost kernel: [17179569.184000] Initializing CPU#0
Dec 23 18:59:36 localhost kernel: [17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
Dec 23 18:59:36 localhost kernel: [17179569.184000] Detected 1129.704 MHz processor.
Dec 23 18:59:36 localhost kernel: [17179569.184000] Using pmtmr for high-res timesource
Dec 23 18:59:36 localhost kernel: [17179569.184000] Console: colour VGA+ 80x25
Dec 23 18:59:36 localhost kernel: [17179569.204000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 23 18:59:36 localhost kernel: [17179569.204000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 23 18:59:36 localhost kernel: [17179569.220000] Memory: 248500k/261504k available (1976k kernel code, 12352k reserved, 606k data, 288k init, 0k highmem)
Dec 23 18:59:36 localhost kernel: [17179569.220000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 23 18:59:36 localhost kernel: [17179569.300000] Calibrating delay using timer specific routine.. 2261.15 BogoMIPS (lpj=4522312)
Dec 23 18:59:36 localhost kernel: [17179569.300000] Security Framework v1.0.0 initialized
Dec 23 18:59:36 localhost kernel: [17179569.300000] SELinux:  Disabled at boot.
Dec 23 18:59:36 localhost kernel: [17179569.300000] Mount-cache hash table entries: 512
Dec 23 18:59:36 localhost kernel: [17179569.300000] CPU: L1 I cache: 16K, L1 D cache: 16K
Dec 23 18:59:36 localhost kernel: [17179569.300000] CPU: L2 cache: 512K
Dec 23 18:59:36 localhost kernel: [17179569.300000] mtrr: v2.0 (20020519)
Dec 23 18:59:36 localhost kernel: [17179569.300000] CPU: Intel(R) Pentium(R) III Mobile CPU      1133MHz stepping 01
Dec 23 18:59:36 localhost kernel: [17179569.300000] Enabling fast FPU save and restore... done.
Dec 23 18:59:36 localhost kernel: [17179569.300000] Enabling unmasked SIMD FPU exception support... done.
Dec 23 18:59:36 localhost kernel: [17179569.300000] Checking 'hlt' instruction... OK.
Dec 23 18:59:36 localhost kernel: [17179569.316000] checking if image is initramfs... it is
Dec 23 18:59:36 localhost kernel: [17179570.616000] Freeing initrd memory: 6616k freed
Dec 23 18:59:36 localhost kernel: [17179570.636000] ACPI: Looking for DSDT ... not found!
Dec 23 18:59:36 localhost kernel: [17179570.640000] ACPI: setting ELCR to 0200 (from 0e20)
Dec 23 18:59:36 localhost kernel: [17179570.640000] NET: Registered protocol family 16
Dec 23 18:59:36 localhost kernel: [17179570.640000] EISA bus registered
Dec 23 18:59:36 localhost kernel: [17179570.640000] ACPI: bus type pci registered
Dec 23 18:59:36 localhost kernel: [17179570.644000] PCI: PCI BIOS revision 2.10 entry at 0xfd99b, last bus=2
Dec 23 18:59:36 localhost kernel: [17179570.644000] PCI: Using configuration type 1
Dec 23 18:59:36 localhost kernel: [17179570.644000] ACPI: Subsystem revision 20051216
Dec 23 18:59:36 localhost kernel: [17179570.660000] ACPI: Interpreter enabled
Dec 23 18:59:36 localhost kernel: [17179570.660000] ACPI: Using PIC for interrupt routing
Dec 23 18:59:36 localhost kernel: [17179570.660000] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 23 18:59:36 localhost kernel: [17179570.664000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
Dec 23 18:59:36 localhost kernel: [17179570.664000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
Dec 23 18:59:36 localhost kernel: [17179570.664000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
Dec 23 18:59:36 localhost kernel: [17179570.664000] PCI: Transparent bridge - 0000:00:1e.0
Dec 23 18:59:36 localhost kernel: [17179570.668000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 14 15)
Dec 23 18:59:36 localhost kernel: [17179570.668000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 14 15)
Dec 23 18:59:36 localhost kernel: [17179570.668000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
Dec 23 18:59:36 localhost kernel: [17179570.668000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 14 15)
Dec 23 18:59:36 localhost kernel: [17179570.668000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 14 15)
Dec 23 18:59:36 localhost kernel: [17179570.668000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
Dec 23 18:59:36 localhost kernel: [17179570.668000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
Dec 23 18:59:36 localhost kernel: [17179570.668000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 14 15) *0, disabled.
Dec 23 18:59:36 localhost kernel: [17179570.672000] ACPI: Embedded Controller [H8] (gpe 29) interrupt mode.
Dec 23 18:59:36 localhost kernel: [17179570.680000] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 23 18:59:36 localhost kernel: [17179570.680000] pnp: PnP ACPI init
Dec 23 18:59:36 localhost kernel: [17179570.684000] pnp: PnP ACPI: found 11 devices
Dec 23 18:59:36 localhost kernel: [17179570.684000] PnPBIOS: Disabled by ACPI PNP
Dec 23 18:59:36 localhost kernel: [17179570.684000] PCI: Using ACPI for IRQ routing
Dec 23 18:59:36 localhost kernel: [17179570.684000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 23 18:59:36 localhost kernel: [17179570.688000] pnp: 00:03: ioport range 0x600-0x60f has been reserved
Dec 23 18:59:36 localhost kernel: [17179570.688000] PCI: Bridge: 0000:00:01.0
Dec 23 18:59:36 localhost kernel: [17179570.688000]   IO window: 2000-2fff
Dec 23 18:59:36 localhost kernel: [17179570.688000]   MEM window: d0100000-d01fffff
Dec 23 18:59:36 localhost kernel: [17179570.688000]   PREFETCH window: d8000000-dfffffff
Dec 23 18:59:36 localhost kernel: [17179570.688000] PCI: Bus 3, cardbus bridge: 0000:02:06.0
Dec 23 18:59:36 localhost kernel: [17179570.688000]   IO window: 00003400-000034ff
Dec 23 18:59:36 localhost kernel: [17179570.688000]   IO window: 00003800-000038ff
Dec 23 18:59:36 localhost kernel: [17179570.688000]   PREFETCH window: 20000000-21ffffff
Dec 23 18:59:36 localhost kernel: [17179570.688000]   MEM window: 24000000-25ffffff
Dec 23 18:59:36 localhost kernel: [17179570.688000] PCI: Bridge: 0000:00:1e.0
Dec 23 18:59:36 localhost kernel: [17179570.688000]   IO window: 3000-3fff
Dec 23 18:59:36 localhost kernel: [17179570.688000]   MEM window: d0200000-d02fffff
Dec 23 18:59:36 localhost kernel: [17179570.688000]   PREFETCH window: 20000000-21ffffff
Dec 23 18:59:36 localhost kernel: [17179571.048000] **** SET: Misaligned resource pointer: cf9715e2 Type 07 Len 0
Dec 23 18:59:36 localhost kernel: [17179571.048000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
Dec 23 18:59:36 localhost kernel: [17179571.048000] PCI: setting IRQ 10 as level-triggered
Dec 23 18:59:36 localhost kernel: [17179571.048000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Dec 23 18:59:36 localhost kernel: [17179571.048000] Simple Boot Flag at 0x38 set to 0x1
Dec 23 18:59:36 localhost kernel: [17179571.048000] audit: initializing netlink socket (disabled)
Dec 23 18:59:36 localhost kernel: [17179571.048000] audit(1166900340.048:1): initialized
Dec 23 18:59:36 localhost kernel: [17179571.048000] VFS: Disk quotas dquot_6.5.1
Dec 23 18:59:36 localhost kernel: [17179571.048000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 23 18:59:36 localhost kernel: [17179571.048000] Initializing Cryptographic API
Dec 23 18:59:36 localhost kernel: [17179571.048000] io scheduler noop registered
Dec 23 18:59:36 localhost kernel: [17179571.048000] io scheduler anticipatory registered
Dec 23 18:59:36 localhost kernel: [17179571.048000] io scheduler deadline registered
Dec 23 18:59:36 localhost kernel: [17179571.048000] io scheduler cfq registered
Dec 23 18:59:36 localhost kernel: [17179571.048000] isapnp: Scanning for PnP cards...
Dec 23 18:59:36 localhost kernel: [17179571.400000] isapnp: No Plug & Play device found
Dec 23 18:59:36 localhost kernel: [17179571.428000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 23 18:59:36 localhost kernel: [17179571.432000] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 23 18:59:36 localhost kernel: [17179571.432000] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 23 18:59:36 localhost kernel: [17179571.432000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Dec 23 18:59:36 localhost kernel: [17179571.432000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Dec 23 18:59:36 localhost kernel: [17179571.436000] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
Dec 23 18:59:36 localhost kernel: [17179571.436000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 23 18:59:36 localhost kernel: [17179571.436000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec 23 18:59:36 localhost kernel: [17179571.436000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec 23 18:59:36 localhost kernel: [17179571.436000] mice: PS/2 mouse device common for all mice
Dec 23 18:59:36 localhost kernel: [17179571.440000] EISA: Probing bus 0 at eisa.0
Dec 23 18:59:36 localhost kernel: [17179571.440000] Cannot allocate resource for EISA slot 1
Dec 23 18:59:36 localhost kernel: [17179571.440000] Cannot allocate resource for EISA slot 2
Dec 23 18:59:36 localhost kernel: [17179571.440000] Cannot allocate resource for EISA slot 3
Dec 23 18:59:36 localhost kernel: [17179571.440000] EISA: Detected 0 cards.
Dec 23 18:59:36 localhost kernel: [17179571.440000] NET: Registered protocol family 2
Dec 23 18:59:36 localhost kernel: [17179571.460000] input: AT Translated Set 2 keyboard as /class/input/input0
Dec 23 18:59:36 localhost kernel: [17179571.480000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Dec 23 18:59:36 localhost kernel: [17179571.480000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
Dec 23 18:59:36 localhost kernel: [17179571.480000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
Dec 23 18:59:36 localhost kernel: [17179571.480000] TCP: Hash tables configured (established 16384 bind 16384)
Dec 23 18:59:36 localhost kernel: [17179571.480000] TCP reno registered
Dec 23 18:59:36 localhost kernel: [17179571.480000] TCP bic registered
Dec 23 18:59:36 localhost kernel: [17179571.480000] NET: Registered protocol family 1
Dec 23 18:59:36 localhost kernel: [17179571.480000] NET: Registered protocol family 8
Dec 23 18:59:36 localhost kernel: [17179571.480000] NET: Registered protocol family 20
Dec 23 18:59:36 localhost kernel: [17179571.480000] Using IPI Shortcut mode
Dec 23 18:59:36 localhost kernel: [17179571.480000] ACPI wakeup devices: 
Dec 23 18:59:36 localhost kernel: [17179571.480000]   AC  LID PWRB PCIB CRD0  LAN PS2K PS2M   H8 USB0 USB1 USB2 
Dec 23 18:59:36 localhost kernel: [17179571.480000] ACPI: (supports S0 S1 S4 S5)
Dec 23 18:59:36 localhost kernel: [17179571.480000] Freeing unused kernel memory: 288k freed
Dec 23 18:59:36 localhost kernel: [17179571.556000] vga16fb: mapped to 0xc00a0000
Dec 23 18:59:36 localhost kernel: [17179571.672000] Console: switching to colour frame buffer device 80x25
Dec 23 18:59:36 localhost kernel: [17179571.672000] fb0: VGA16 VGA frame buffer device
Dec 23 18:59:36 localhost kernel: [17179572.744000] Capability LSM initialized
Dec 23 18:59:36 localhost kernel: [17179572.872000] ACPI: CPU0 (power states: C1[C1] C2[C2])
Dec 23 18:59:36 localhost kernel: [17179572.872000] ACPI: Thermal Zone [TZ0] (38 C)
Dec 23 18:59:36 localhost kernel: [17179573.460000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
Dec 23 18:59:36 localhost kernel: [17179573.460000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
Dec 23 18:59:36 localhost kernel: [17179573.460000] **** SET: Misaligned resource pointer: cfc0c1c2 Type 07 Len 0
Dec 23 18:59:36 localhost kernel: [17179573.460000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
Dec 23 18:59:36 localhost kernel: [17179573.460000] PCI: setting IRQ 11 as level-triggered
Dec 23 18:59:36 localhost kernel: [17179573.460000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Dec 23 18:59:36 localhost kernel: [17179573.460000] ICH3M: chipset revision 2
Dec 23 18:59:36 localhost kernel: [17179573.460000] ICH3M: not 100%% native mode: will probe irqs later
Dec 23 18:59:36 localhost kernel: [17179573.460000]     ide0: BM-DMA at 0x1800-0x1807, BIOS settings: hda:DMA, hdb:pio
Dec 23 18:59:36 localhost kernel: [17179573.460000]     ide1: BM-DMA at 0x1808-0x180f, BIOS settings: hdc:DMA, hdd:pio
Dec 23 18:59:36 localhost kernel: [17179573.972000] hda: SAMSUNG HM080IC, ATA DISK drive
Dec 23 18:59:36 localhost kernel: [17179574.644000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Dec 23 18:59:36 localhost kernel: [17179575.868000] hdc: SD-R2102, ATAPI CD/DVD-ROM drive
Dec 23 18:59:36 localhost kernel: [17179576.540000] ide1 at 0x170-0x177,0x376 on irq 15
Dec 23 18:59:36 localhost kernel: [17179576.548000] hda: max request size: 1024KiB
Dec 23 18:59:36 localhost kernel: [17179576.564000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
Dec 23 18:59:36 localhost kernel: [17179576.564000] hda: cache flushes supported
Dec 23 18:59:36 localhost kernel: [17179576.564000]  hda: hda1 hda2 hda3 < hda5 >
Dec 23 18:59:36 localhost kernel: [17179576.700000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, DMA
Dec 23 18:59:36 localhost kernel: [17179576.700000] Uniform CD-ROM driver Revision: 3.20
Dec 23 18:59:36 localhost kernel: [17179577.032000] usbcore: registered new driver usbfs
Dec 23 18:59:36 localhost kernel: [17179577.032000] usbcore: registered new driver hub
Dec 23 18:59:36 localhost kernel: [17179577.036000] USB Universal Host Controller Interface driver v2.3
Dec 23 18:59:36 localhost kernel: [17179577.036000] **** SET: Misaligned resource pointer: cfce94e2 Type 07 Len 0
Dec 23 18:59:36 localhost kernel: [17179577.036000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Dec 23 18:59:36 localhost kernel: [17179577.036000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Dec 23 18:59:36 localhost kernel: [17179577.036000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 23 18:59:36 localhost kernel: [17179577.036000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Dec 23 18:59:36 localhost kernel: [17179577.036000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001840
Dec 23 18:59:36 localhost kernel: [17179577.036000] hub 1-0:1.0: USB hub found
Dec 23 18:59:36 localhost kernel: [17179577.036000] hub 1-0:1.0: 2 ports detected
Dec 23 18:59:36 localhost kernel: [17179577.140000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Dec 23 18:59:36 localhost kernel: [17179577.140000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 23 18:59:36 localhost kernel: [17179577.140000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Dec 23 18:59:36 localhost kernel: [17179577.140000] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001860
Dec 23 18:59:36 localhost kernel: [17179577.140000] hub 2-0:1.0: USB hub found
Dec 23 18:59:36 localhost kernel: [17179577.140000] hub 2-0:1.0: 2 ports detected
Dec 23 18:59:36 localhost kernel: [17179577.244000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
Dec 23 18:59:36 localhost kernel: [17179577.244000] **** SET: Misaligned resource pointer: cea6bc02 Type 07 Len 0
Dec 23 18:59:36 localhost kernel: [17179577.244000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
Dec 23 18:59:36 localhost kernel: [17179577.244000] PCI: setting IRQ 9 as level-triggered
Dec 23 18:59:36 localhost kernel: [17179577.244000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
Dec 23 18:59:36 localhost kernel: [17179577.296000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[9]  MMIO=[d0201000-d02017ff]  Max Packet=[2048]
Dec 23 18:59:36 localhost kernel: [17179577.380000] usb 1-1: new low speed USB device using uhci_hcd and address 2
Dec 23 18:59:36 localhost kernel: [17179577.400000] Attempting manual resume
Dec 23 18:59:36 localhost kernel: [17179577.416000] EXT3-fs: INFO: recovery required on readonly filesystem.
Dec 23 18:59:36 localhost kernel: [17179577.416000] EXT3-fs: write access will be enabled during recovery.
Dec 23 18:59:36 localhost kernel: [17179577.568000] usbcore: registered new driver hiddev
Dec 23 18:59:36 localhost kernel: [17179577.588000] input: Logitech USB Receiver as /class/input/input1
Dec 23 18:59:36 localhost kernel: [17179577.588000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
Dec 23 18:59:36 localhost kernel: [17179577.588000] usbcore: registered new driver usbhid
Dec 23 18:59:36 localhost kernel: [17179577.588000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Dec 23 18:59:36 localhost kernel: [17179580.168000] EXT3-fs: hda2: orphan cleanup on readonly fs
Dec 23 18:59:36 localhost kernel: [17179580.168000] EXT3-fs: hda2: 5 orphan inodes deleted
Dec 23 18:59:36 localhost kernel: [17179580.168000] EXT3-fs: recovery complete.
Dec 23 18:59:36 localhost kernel: [17179580.168000] kjournald starting.  Commit interval 5 seconds
Dec 23 18:59:36 localhost kernel: [17179580.176000] EXT3-fs: mounted filesystem with ordered data mode.
Dec 23 18:59:36 localhost kernel: [17179589.956000] ts: Compaq touchscreen protocol output
Dec 23 18:59:36 localhost kernel: [17179592.404000] Linux agpgart interface v0.101 (c) Dave Jones
Dec 23 18:59:36 localhost kernel: [17179592.408000] agpgart: Detected an Intel 830M Chipset.
Dec 23 18:59:36 localhost kernel: [17179592.424000] agpgart: AGP aperture is 256M @ 0xe0000000
Dec 23 18:59:36 localhost kernel: [17179592.760000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 23 18:59:36 localhost kernel: [17179592.764000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 23 18:59:36 localhost kernel: [17179593.080000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
Dec 23 18:59:36 localhost kernel: [17179593.080000] **** SET: Misaligned resource pointer: ce4ad422 Type 07 Len 0
Dec 23 18:59:36 localhost kernel: [17179593.080000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
Dec 23 18:59:36 localhost kernel: [17179593.080000] PCI: setting IRQ 5 as level-triggered
Dec 23 18:59:36 localhost kernel: [17179593.080000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
Dec 23 18:59:36 localhost kernel: [17179593.140000] Real Time Clock Driver v1.12
Dec 23 18:59:36 localhost kernel: [17179593.396000] intel8x0_measure_ac97_clock: measured 54800 usecs
Dec 23 18:59:36 localhost kernel: [17179593.396000] intel8x0: clocking to 48000
Dec 23 18:59:36 localhost kernel: [17179594.136000] Floppy drive(s): fd0 is 1.44M
Dec 23 18:59:36 localhost kernel: [17179594.152000] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Dec 23 18:59:36 localhost kernel: [17179594.152000] Yenta: CardBus bridge found at 0000:02:06.0 [0e11:b103]
Dec 23 18:59:36 localhost kernel: [17179594.152000] Yenta: Enabling burst memory read transactions
Dec 23 18:59:36 localhost kernel: [17179594.152000] Yenta: Using CSCINT to route CSC interrupts to PCI
Dec 23 18:59:36 localhost kernel: [17179594.152000] Yenta: Routing CardBus interrupts to PCI
Dec 23 18:59:36 localhost kernel: [17179594.152000] Yenta TI: socket 0000:02:06.0, mfunc 0x012c1202, devctl 0x64
Dec 23 18:59:36 localhost kernel: [17179594.384000] Yenta: ISA IRQ mask 0x0098, PCI irq 10
Dec 23 18:59:36 localhost kernel: [17179594.384000] Socket status: 30000020
Dec 23 18:59:36 localhost kernel: [17179594.384000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Dec 23 18:59:36 localhost kernel: [17179594.384000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
Dec 23 18:59:36 localhost kernel: [17179594.384000] cs: IO port probe 0x3000-0x3fff: clean.
Dec 23 18:59:36 localhost kernel: [17179594.384000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
Dec 23 18:59:36 localhost kernel: [17179594.384000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x21ffffff
Dec 23 18:59:36 localhost kernel: [17179594.552000] parport: PnPBIOS parport detected.
Dec 23 18:59:36 localhost kernel: [17179594.552000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Dec 23 18:59:36 localhost kernel: [17179594.580000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
Dec 23 18:59:36 localhost kernel: [17179594.580000] e100: Copyright(c) 1999-2005 Intel Corporation
Dec 23 18:59:36 localhost kernel: [17179594.580000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
Dec 23 18:59:36 localhost kernel: [17179594.608000] e100: eth0: e100_probe: addr 0xd0200000, irq 9, MAC addr 00:02:A5:9D:36:8E
Dec 23 18:59:36 localhost kernel: [17179594.724000] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x1d48b1, caps: 0x904713/0x4006
Dec 23 18:59:36 localhost kernel: [17179594.756000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
Dec 23 18:59:36 localhost kernel: [17179595.044000] pccard: CardBus card inserted into slot 0
Dec 23 18:59:36 localhost kernel: [17179595.244000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Dec 23 18:59:36 localhost kernel: [17179595.244000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Dec 23 18:59:36 localhost kernel: [17179595.248000] rt2500 1.1.0 CVS 2005/07/10 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
Dec 23 18:59:36 localhost kernel: [17179595.276000] cs: IO port probe 0x100-0x3af: clean.
Dec 23 18:59:36 localhost kernel: [17179595.276000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Dec 23 18:59:36 localhost kernel: [17179595.276000] cs: IO port probe 0x820-0x8ff: clean.
Dec 23 18:59:36 localhost kernel: [17179595.276000] cs: IO port probe 0xc00-0xcf7: clean.
Dec 23 18:59:36 localhost kernel: [17179595.276000] cs: IO port probe 0xa00-0xaff: clean.
Dec 23 18:59:36 localhost kernel: [17179596.484000] NET: Registered protocol family 17
Dec 23 18:59:36 localhost kernel: [17179597.152000] floppy0: no floppy controllers found
Dec 23 18:59:36 localhost kernel: [17179597.556000] lp0: using parport0 (interrupt-driven).
Dec 23 18:59:36 localhost kernel: [17179597.624000] SCSI subsystem initialized
Dec 23 18:59:36 localhost kernel: [17179597.640000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
Dec 23 18:59:36 localhost kernel: [17179597.640000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Dec 23 18:59:36 localhost kernel: [17179597.640000] ieee1394: sbp2: Try serialize_io=0 for better performance
Dec 23 18:59:36 localhost kernel: [17179597.740000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
Dec 23 18:59:36 localhost kernel: [17179597.868000] EXT3 FS on hda2, internal journal
Dec 23 18:59:36 localhost kernel: [17179598.076000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Dec 23 18:59:36 localhost kernel: [17179598.076000] md: bitmap version 4.39
Dec 23 18:59:36 localhost kernel: [17179598.768000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Dec 23 18:59:36 localhost kernel: [17179598.976000] NET: Registered protocol family 10
Dec 23 18:59:36 localhost kernel: [17179598.976000] lo: Disabled Privacy Extensions
Dec 23 18:59:36 localhost kernel: [17179598.976000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 18:59:36 localhost kernel: [17179598.976000] IPv6 over IPv4 tunneling driver
Dec 23 18:59:36 localhost kernel: [17179599.536000] cdrom: open failed.
Dec 23 18:59:36 localhost kernel: [17179606.288000] ACPI: AC Adapter [AC] (on-line)
Dec 23 18:59:36 localhost kernel: [17179606.292000] ACPI: Battery Slot [CMB0] (battery absent)
Dec 23 18:59:36 localhost kernel: [17179606.424000] ACPI: Lid Switch [LID]
Dec 23 18:59:36 localhost kernel: [17179606.424000] ACPI: Power Button (CM) [PWRB]
Dec 23 18:59:36 localhost kernel: [17179606.424000] ACPI: Sleep Button (CM) [SLPB]
Dec 23 18:59:36 localhost kernel: [17179606.632000] pcc_acpi: loading...
Dec 23 18:59:36 localhost kernel: [17179606.784000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Dec 23 18:59:40 localhost hpiod: 0.9.7 accepting connections at 46506... 
Dec 23 18:59:40 localhost kernel: [17179611.680000] [drm] Initialized drm 1.0.1 20051102
Dec 23 18:59:40 localhost kernel: [17179611.720000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Dec 23 18:59:40 localhost kernel: [17179611.724000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
Dec 23 18:59:41 localhost kernel: [17179612.864000] ppdev: user-space parallel port driver
Dec 23 18:59:42 localhost kernel: [17179613.652000] apm: BIOS not found.
Dec 23 18:59:47 localhost kernel: [17179618.996000] Bluetooth: Core ver 2.8
Dec 23 18:59:47 localhost kernel: [17179618.996000] NET: Registered protocol family 31
Dec 23 18:59:47 localhost kernel: [17179618.996000] Bluetooth: HCI device and connection manager initialized
Dec 23 18:59:47 localhost kernel: [17179618.996000] Bluetooth: HCI socket layer initialized
Dec 23 18:59:47 localhost kernel: [17179619.052000] Bluetooth: L2CAP ver 2.8
Dec 23 18:59:47 localhost kernel: [17179619.052000] Bluetooth: L2CAP socket layer initialized
Dec 23 18:59:47 localhost kernel: [17179619.084000] Bluetooth: RFCOMM socket layer initialized
Dec 23 18:59:47 localhost kernel: [17179619.084000] Bluetooth: RFCOMM TTY layer initialized
Dec 23 18:59:47 localhost kernel: [17179619.084000] Bluetooth: RFCOMM ver 1.7
Dec 23 18:59:58 localhost gconfd (nunoct-4852): a iniciar (versão 2.14.0), pid 4852 utilizador 'nunoct'
Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.mandatory" para uma fonte de configuração apenas de leitura na posição 0
Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 1
Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.defaults" para uma fonte de configuração apenas de leitura na posição 2
Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readonly:/var/lib/gconf/debian.defaults" para uma fonte de configuração apenas de leitura na posição 3
Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readonly:/var/lib/gconf/defaults" para uma fonte de configuração apenas de leitura na posição 4
Dec 23 19:00:04 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 0
Dec 23 19:04:24 localhost syslogd 1.4.1#17ubuntu7: restart.
Dec 23 19:04:24 localhost kernel: Inspecting /boot/System.map-2.6.15-27-386
Dec 23 19:04:24 localhost kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Dec 23 19:04:24 localhost kernel: Symbols match kernel version 2.6.15.
Dec 23 19:04:24 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Dec 23 19:04:24 localhost kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006
Dec 23 19:04:24 localhost kernel: [17179569.184000] BIOS-provided physical RAM map:
Dec 23 19:04:24 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Dec 23 19:04:24 localhost kernel: [17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Dec 23 19:04:24 localhost kernel: [17179569.184000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
Dec 23 19:04:24 localhost kernel: [17179569.184000]  BIOS-e820: 0000000000100000 - 000000000ff60000 (usable)
Dec 23 19:04:24 localhost kernel: [17179569.184000]  BIOS-e820: 000000000ff60000 - 000000000ff6fc00 (ACPI data)
Dec 23 19:04:24 localhost kernel: [17179569.184000]  BIOS-e820: 000000000ff6fc00 - 000000000ff80000 (ACPI NVS)
Dec 23 19:04:24 localhost kernel: [17179569.184000]  BIOS-e820: 000000000ff80000 - 0000000010000000 (reserved)
Dec 23 19:04:24 localhost kernel: [17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
Dec 23 19:04:24 localhost kernel: [17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Dec 23 19:04:24 localhost kernel: [17179569.184000] 0MB HIGHMEM available.
Dec 23 19:04:24 localhost kernel: [17179569.184000] 255MB LOWMEM available.
Dec 23 19:04:24 localhost kernel: [17179569.184000] DMI present.
Dec 23 19:04:24 localhost kernel: [17179569.184000] ACPI: PM-Timer IO Port: 0x1008
Dec 23 19:04:24 localhost kernel: [17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:ef800000)
Dec 23 19:04:24 localhost kernel: [17179569.184000] Built 1 zonelists
Dec 23 19:04:24 localhost kernel: [17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
Dec 23 19:04:24 localhost kernel: [17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
Dec 23 19:04:24 localhost kernel: [17179569.184000] Initializing CPU#0
Dec 23 19:04:24 localhost kernel: [17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
Dec 23 19:04:24 localhost kernel: [17179569.184000] Detected 1129.704 MHz processor.
Dec 23 19:04:24 localhost kernel: [17179569.184000] Using pmtmr for high-res timesource
Dec 23 19:04:24 localhost kernel: [17179569.184000] Console: colour VGA+ 80x25
Dec 23 19:04:24 localhost kernel: [17179569.788000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 23 19:04:24 localhost kernel: [17179569.788000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 23 19:04:24 localhost kernel: [17179569.804000] Memory: 248500k/261504k available (1976k kernel code, 12352k reserved, 606k data, 288k init, 0k highmem)
Dec 23 19:04:24 localhost kernel: [17179569.804000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 23 19:04:24 localhost kernel: [17179569.884000] Calibrating delay using timer specific routine.. 2261.13 BogoMIPS (lpj=4522271)
Dec 23 19:04:24 localhost kernel: [17179569.884000] Security Framework v1.0.0 initialized
Dec 23 19:04:24 localhost kernel: [17179569.884000] SELinux:  Disabled at boot.
Dec 23 19:04:24 localhost kernel: [17179569.884000] Mount-cache hash table entries: 512
Dec 23 19:04:24 localhost kernel: [17179569.884000] CPU: L1 I cache: 16K, L1 D cache: 16K
Dec 23 19:04:24 localhost kernel: [17179569.884000] CPU: L2 cache: 512K
Dec 23 19:04:24 localhost kernel: [17179569.884000] mtrr: v2.0 (20020519)
Dec 23 19:04:24 localhost kernel: [17179569.884000] CPU: Intel(R) Pentium(R) III Mobile CPU      1133MHz stepping 01
Dec 23 19:04:24 localhost kernel: [17179569.884000] Enabling fast FPU save and restore... done.
Dec 23 19:04:24 localhost kernel: [17179569.884000] Enabling unmasked SIMD FPU exception support... done.
Dec 23 19:04:24 localhost kernel: [17179569.884000] Checking 'hlt' instruction... OK.
Dec 23 19:04:24 localhost kernel: [17179569.900000] checking if image is initramfs... it is
Dec 23 19:04:24 localhost kernel: [17179571.200000] Freeing initrd memory: 6616k freed
Dec 23 19:04:24 localhost kernel: [17179571.220000] ACPI: Looking for DSDT ... not found!
Dec 23 19:04:24 localhost kernel: [17179571.224000] ACPI: setting ELCR to 0200 (from 0e20)
Dec 23 19:04:24 localhost kernel: [17179571.224000] NET: Registered protocol family 16
Dec 23 19:04:24 localhost kernel: [17179571.224000] EISA bus registered
Dec 23 19:04:24 localhost kernel: [17179571.224000] ACPI: bus type pci registered
Dec 23 19:04:24 localhost kernel: [17179571.228000] PCI: PCI BIOS revision 2.10 entry at 0xfd99b, last bus=2

---

### Post by nnn25 on 2006-12-23
DAEMON
c 23 18:59:39 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 23 18:59:47 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 23 18:59:47 localhost hcid[4629]: Bluetooth HCI daemon
Dec 23 18:59:47 localhost hcid[4629]: Can't get system message bus name: Connection ":1.1" is not allowed to own the service "org.bluez" due to security policies in the configuration file
Dec 23 18:59:47 localhost sdpd[4634]: Bluetooth SDP daemon 
Dec 23 18:59:58 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Dec 23 19:00:11 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
Dec 23 19:00:30 localhost dhclient: No DHCPOFFERS received.
Dec 23 19:00:30 localhost dhclient: No working leases in persistent database - sleeping.
Dec 23 19:00:27 localhost ntpdate[4953]: step time server 82.211.81.145 offset -3.030463 sec
Dec 23 19:04:24 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 23 19:04:32 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 23 19:04:35 localhost hcid[4621]: Bluetooth HCI daemon
Dec 23 19:04:35 localhost sdpd[4626]: Bluetooth SDP daemon 
Dec 23 19:04:35 localhost hcid[4621]: Can't get system message bus name: Connection ":1.1" is not allowed to own the service "org.bluez" due to security policies in the configuration file
Dec 23 19:04:39 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Dec 23 19:04:52 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Dec 23 19:05:09 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 23 19:05:16 localhost dhclient: No DHCPOFFERS received.
Dec 23 19:05:16 localhost dhclient: No working leases in persistent database - sleeping.
Dec 23 19:05:13 localhost ntpdate[4955]: step time server 82.211.81.145 offset -3.046729 sec
Dec 23 19:09:21 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec 23 19:09:25 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 23 19:09:35 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Dec 23 19:09:51 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 23 19:10:06 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Dec 23 19:10:22 localhost dhclient: No DHCPOFFERS received.
Dec 23 19:10:22 localhost dhclient: No working leases in persistent database - sleeping.
Dec 23 19:13:57 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Dec 23 19:14:01 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Dec 23 19:14:07 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Dec 23 19:14:19 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 23 19:14:27 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 23 19:14:38 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 23 19:14:46 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Dec 23 19:14:58 localhost dhclient: No DHCPOFFERS received.
Dec 23 19:14:58 localhost dhclient: No working leases in persistent database - sleeping.



Have a nice Christmas and a Happy Year 2007

Best Regards

---

### Post by Ecthelion on 2006-12-23
Hey

> I did want you said, but unfortnly it crashed.
When did it crash?
While reconfiguring? Then you have no x anymore except if you use your backup.

Or do you mean that it didn't helped to reconfigure...
That's possible of course.

Some remarks & questions about the logs:

I can't find anything that could cause a crash in your first couple of logs.
(Again I'm no pro, so I could be wrong)

In your second couple of logs:

> Dec 23 18:59:58 localhost gconfd (nunoct-4852): Resolvido o endereço "xml:readonly:/var/lib/gconf/debian.defaults" para uma fonte de configuração apenas de leitura na posição 3
Since I have these messages too after each boot up, I guess these messages are normal.
Surely no cause of a crash.

> Dec 23 18:59:36 localhost kernel: [17179570.668000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 *10 11 14 15)
ACPI stands for "Advanced Configuration and Power Interface"
Bad power management can, I think, make your computer freeze. But I would expect that such a freeze would be immediate and then it wouldn't have been in a log.
So I don't think that 'll be it.
> Dec 23 18:59:36 localhost kernel: [17179606.424000] ACPI: Sleep Button (CM) [SLPB]
Dec 23 18:59:36 localhost kernel: [17179606.632000] pcc_acpi: loading...
This is I think proof that the power management is ok.


> Dec 23 19:04:24 localhost kernel: [17179571.228000] PCI: PCI BIOS revision 2.10 entry at 0xfd99b, last bus=2
Is this the last entry in your logs before the crash?

> Dec 23 18:59:58 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
As far as I know these are errors with the DHCP. If you have no problems with your internet connection, then you can ignore this. Shouldn't make a system crash.

So all by all, doesn't seem much info on th problem out of the logs.
Only thing I can think you could try is trying to reinstall ubuntu.
But even that wouldn't guarantee that those freezes wouldn't happen anymore.
Although there's a good chance.
Guess that's all the advice I have left. :???: 

> Have a nice Christmas and a Happy Year 2007
Same to you!

---

### Post by nnn25 on 2006-12-24
Hello,
It had crashed as the others, in a randon way.

To reinstall the ubuntu, is the same that i did to install it?

thanks

---

### Post by Ecthelion on 2006-12-25
> Hello,
It had crashed as the others, in a randon way.

To reinstall the ubuntu, is the same that i did to install it?

thanks

... :-|  ...

Yes.

Too bad we couldn't find the cause nor the solution.

Succes with your new install and happy new year!

Ps. Don't forget to back up your important stuff :-)

---

### Post by nnn25 on 2006-12-26
How is the best way to reinstall the ubuntu again? Insert the cd and do the same as the first installation?

I remember that I have dualboot.

Thanks
Nuno Costa

---

### Post by Ecthelion on 2006-12-27
> 	How is the best way to reinstall the ubuntu again? Insert the cd and do the same as the first installation?

I remember that I have dualboot.
Yes.
Start up from the cd and say install again.
When you get at the step where you have to choose the partitions, choose to do it manually and make sure he uses the partitions of your earlier install.
You'll have to reformat your old /
That's all I think.

---

### Post by nnn25 on 2006-12-27
Hello,

In all crash I had, I discover allways this text in /var/log just before it crash:

ec 23 18:59:47 localhost kernel: [17179618.996000] Bluetooth: HCI socket layer initialized
Dec 23 18:59:47 localhost kernel: [17179619.052000] Bluetooth: L2CAP ver 2.8
Dec 23 18:59:47 localhost kernel: [17179619.052000] Bluetooth: L2CAP socket layer initialized
Dec 23 18:59:47 localhost kernel: [17179619.084000] Bluetooth: RFCOMM socket layer initialized
Dec 23 18:59:47 localhost kernel: [17179619.084000] Bluetooth: RFCOMM TTY layer initialized
Dec 23 18:59:47 localhost kernel: [17179619.084000] Bluetooth: RFCOMM ver 1.7
Dec 23 19:04:24 localhost kernel: Inspecting /boot/System.map-2.6.15-27-386

My notebook dave not Bluetooh. Could this part make the crash? Could we desctivate this?

Many thanks for the help. 
When I have more time and if it does not improve, I will try the reinstalltion.

---

### Post by nnn25 on 2006-12-27
Another example:

Dec 27 22:27:36 localhost kernel: [17179595.512000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
Dec 27 22:27:36 localhost kernel: [17179595.512000] e100: Copyright(c) 1999-2005 Intel Corporation
Dec 27 22:27:36 localhost kernel: [17179595.688000] Yenta: ISA IRQ mask 0x0018, PCI irq 10
Dec 27 22:27:36 localhost kernel: [17179595.688000] Socket status: 30000020
Dec 27 22:27:36 localhost kernel: [17179595.688000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
Dec 27 22:27:36 localhost kernel: [17179595.688000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
Dec 27 22:27:36 localhost kernel: [17179595.688000] cs: IO port probe 0x3000-0x3fff: clean.
Dec 27 22:27:36 localhost kernel: [17179595.688000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
Dec 27 22:27:36 localhost kernel: [17179595.688000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x21ffffff
Dec 27 22:27:36 localhost kernel: [17179595.696000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
Dec 27 22:27:36 localhost kernel: [17179595.720000] e100: eth0: e100_probe: addr 0xd0200000, irq 9, MAC addr 00:02:A5:9D:36:8E
Dec 27 22:27:36 localhost kernel: [17179596.396000] pccard: CardBus card inserted into slot 0
Dec 27 22:27:36 localhost kernel: [17179596.472000] cs: IO port probe 0x100-0x3af: clean.
Dec 27 22:27:36 localhost kernel: [17179596.476000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
Dec 27 22:27:36 localhost kernel: [17179596.476000] cs: IO port probe 0x820-0x8ff: clean.
Dec 27 22:27:36 localhost kernel: [17179596.476000] cs: IO port probe 0xc00-0xcf7: clean.
Dec 27 22:27:36 localhost kernel: [17179596.476000] cs: IO port probe 0xa00-0xaff: clean.
Dec 27 22:27:36 localhost kernel: [17179596.532000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
Dec 27 22:27:36 localhost kernel: [17179596.532000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
Dec 27 22:27:36 localhost kernel: [17179596.532000] rt2500 1.1.0 CVS 2005/07/10 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
Dec 27 22:27:36 localhost kernel: [17179596.532000] PCI: Setting latency timer of device 0000:03:00.0 to 64
Dec 27 22:27:36 localhost kernel: [17179596.660000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
Dec 27 22:27:36 localhost kernel: [17179596.660000] rt2500 EEPROM:  6  6  6  6  6  6  6  6  6  5  5  5  5  5  dBm Maximum
Dec 27 22:27:36 localhost kernel: [17179596.932000] floppy0: no floppy controllers found
Dec 27 22:27:36 localhost kernel: [17179597.084000] NET: Registered protocol family 17
Dec 27 22:27:36 localhost kernel: [17179597.268000] lp0: using parport0 (interrupt-driven).
Dec 27 22:27:36 localhost kernel: [17179597.336000] SCSI subsystem initialized
Dec 27 22:27:36 localhost kernel: [17179597.376000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
Dec 27 22:27:36 localhost kernel: [17179597.376000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
Dec 27 22:27:36 localhost kernel: [17179597.376000] ieee1394: sbp2: Try serialize_io=0 for better performance
Dec 27 22:27:36 localhost kernel: [17179597.472000] Adding 746980k swap on /dev/hda5.  Priority:-1 extents:1 across:746980k
Dec 27 22:27:36 localhost kernel: [17179597.604000] EXT3 FS on hda2, internal journal
Dec 27 22:27:36 localhost kernel: [17179597.820000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
Dec 27 22:27:36 localhost kernel: [17179597.820000] md: bitmap version 4.39
Dec 27 22:27:36 localhost kernel: [17179598.288000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Dec 27 22:27:36 localhost kernel: [17179598.968000] cdrom: open failed.
Dec 27 22:27:36 localhost kernel: [17179601.392000] NET: Registered protocol family 10
Dec 27 22:27:36 localhost kernel: [17179601.392000] lo: Disabled Privacy Extensions
Dec 27 22:27:36 localhost kernel: [17179601.392000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 27 22:27:36 localhost kernel: [17179601.392000] IPv6 over IPv4 tunneling driver
Dec 27 22:27:36 localhost kernel: [17179605.900000] ACPI: AC Adapter [AC] (on-line)
Dec 27 22:27:36 localhost kernel: [17179605.904000] ACPI: Battery Slot [CMB0] (battery absent)
Dec 27 22:27:36 localhost kernel: [17179606.036000] ACPI: Lid Switch [LID]
Dec 27 22:27:36 localhost kernel: [17179606.036000] ACPI: Power Button (CM) [PWRB]
Dec 27 22:27:36 localhost kernel: [17179606.036000] ACPI: Sleep Button (CM) [SLPB]
Dec 27 22:27:36 localhost kernel: [17179606.200000] ibm_acpi: ec object not found
Dec 27 22:27:36 localhost kernel: [17179606.244000] pcc_acpi: loading...
Dec 27 22:27:36 localhost kernel: [17179606.396000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Dec 27 22:27:37 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 27 22:27:39 localhost hpiod: 0.9.7 accepting connections at 36969... 
Dec 27 22:27:40 localhost kernel: [17179611.280000] [drm] Initialized drm 1.0.1 20051102
Dec 27 22:27:40 localhost kernel: [17179611.320000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Dec 27 22:27:40 localhost kernel: [17179611.324000] [drm] Initialized radeon 1.24.0 20060225 on minor 0
Dec 27 22:27:40 localhost kernel: [17179611.696000] ra0: no IPv6 routers present
Dec 27 22:27:41 localhost kernel: [17179612.396000] ppdev: user-space parallel port driver
Dec 27 22:27:42 localhost kernel: [17179612.920000] apm: BIOS not found.
Dec 27 22:27:47 localhost hcid[4627]: Bluetooth HCI daemon
Dec 27 22:27:47 localhost kernel: [17179618.464000] Bluetooth: Core ver 2.8
Dec 27 22:27:47 localhost kernel: [17179618.464000] NET: Registered protocol family 31
Dec 27 22:27:47 localhost kernel: [17179618.464000] Bluetooth: HCI device and connection manager initialized
Dec 27 22:27:47 localhost kernel: [17179618.464000] Bluetooth: HCI socket layer initialized
Dec 27 22:27:47 localhost kernel: [17179618.520000] Bluetooth: L2CAP ver 2.8
Dec 27 22:27:47 localhost kernel: [17179618.520000] Bluetooth: L2CAP socket layer initialized
Dec 27 22:27:47 localhost sdpd[4631]: [B][B][B]Bluetooth SDP daemon 
Dec 27 22:27:47 localhost hcid[4627]: Can't get system message bus name: Connection ":1.1" is not allowed to own the service "org.bluez" due to security policies in the configuration file
Dec 27 22:27:47 localhost kernel: [17179618.564000] B[B]luetooth: RFCOMM socket layer initialized
Dec 27 22:27:47 localhost kernel: [17179618.564000] Bluetooth: RFCOMM TTY layer initialized
Dec 27 22:27:47 localhost kernel: [17179618.564000] Bluetooth: RFCOMM ver 1.7[/B]
Dec 27 22:27:47 localhost anacron[4682]: Anacron 2.3 started on 2006-12-27[/B][/B][/B]
Dec 27 22:27:48 localhost anacron[4682]: Normal exit (0 jobs run)
Dec 27 22:27:48 localhost /usr/sbin/cron[4707]: (CRON) INFO (pidfile fd = 3)
Dec 27 22:27:48 localhost /usr/sbin/cron[4708]: (CRON) STARTUP (fork ok)
Dec 27 22:27:48 localhost /usr/sbin/cron[4708]: (CRON) INFO (Running @reboot jobs)
Dec 27 22:27:52 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Dec 27 22:27:56 localhost gconfd (nunoct-4855): a iniciar (versão 2.14.0), pid 4855 utilizador 'nunoct'
Dec 27 22:27:56 localhost gconfd (nunoct-4855): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.mandatory" para uma fonte de configuração apenas de leitura na posição 0
Dec 27 22:27:56 localhost gconfd (nunoct-4855): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 1
Dec 27 22:27:56 localhost gconfd (nunoct-4855): Resolvido o endereço "xml:readonly:/etc/gconf/gconf.xml.defaults" para uma fonte de configuração apenas de leitura na posição 2
Dec 27 22:27:56 localhost gconfd (nunoct-4855): Resolvido o endereço "xml:readonly:/var/lib/gconf/debian.defaults" para uma fonte de configuração apenas de leitura na posição 3
Dec 27 22:27:56 localhost gconfd (nunoct-4855): Resolvido o endereço "xml:readonly:/var/lib/gconf/defaults" para uma fonte de configuração apenas de leitura na posição 4
Dec 27 22:28:02 localhost gconfd (nunoct-4855): Resolvido o endereço "xml:readwrite:/home/nunoct/.gconf" para uma fonte de configuração com permissão de escrita na posição 0
Dec 27 22:28:06 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 27 22:28:17 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Dec 27 22:28:28 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Dec 27 22:28:30 localhost dhclient: No DHCPOFFERS received.
Dec 27 22:28:30 localhost dhclient: No working leases in persistent database - sleeping.
Dec 27 22:28:27 localhost ntpdate[4953]: step time server 82.211.81.145 offset -5.157528 sec
Dec 27 22:34:31 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 27 22:34:39 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
Dec 27 22:34:59 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 27 22:35:06 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Dec 27 22:35:20 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Dec 27 22:35:32 localhost dhclient: No DHCPOFFERS received.
Dec 27 22:35:32 localhost dhclient: No working leases in persistent database - sleeping.

---

### Post by Ecthelion on 2006-12-30
> My notebook dave not Bluetooh. Could this part make the crash? Could we desctivate this?
I suppose it could be blacklisted somehow.
If you would want to do that you have to look for the exact process name that gets started. (maybe google for it. If this is the cause you would probably find people who had the same problems.)
Then add it to "/etc/modprobe.d/blacklist"
Altough maybe blacklisting only works for processes that start up with your computer. But then, this probably also starts with your computer ;-)

To be honest, I would be quite surprised if this would make a computer freeze. It is of course possible.

---

### Post by nickdolan on 2007-02-26
It's more likely that you have a hardware fault.

If the OS installs without problem and then crashes randomly while use I would firstly rule out all hardware.

make sure you test (full) test your memory and that your machine is not over heating (i.e. CPU)

Good Luck

---

### Post by nnn25 on 2007-03-01
OK

I will try that.

Thanks

---

### Post by javierfh on 2007-03-03
Hello Nuno,

i just saw your post while looking for compaq presario 1700 since i have one of these.
Not that i want to be negative, but im quite disappointed with it.. it crashes for me also, without any reason, everything freezes, and only way to do anything it is to reboot, but that has happened both in linux and windows, since i have dual boot. To be honest is quite frustrating and im afraid it is something to do with hardware and i bet that it has something to do with processor or mother board. Maybe gets overheated and decides to stop..

I hope that if you can find some solution you can post it here.. i would try it too.
I have presario 1714 ea, its a portuguesse machine :D but i bought it in spain , where i am from :)

Good luck and let me know if you get some solution for it.

Javi

---

