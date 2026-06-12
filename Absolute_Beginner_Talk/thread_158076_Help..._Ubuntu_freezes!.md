---
title: "Help... Ubuntu freezes!"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by Amorphous_Snake on 2006-04-10
I have installed Automatix and the following updates:

multimedia codecs
all Firefox plugins
RAR, ACE and UNRAR archive support
Acrobat reader 7 and firefox plugin
Frostwire (GPL clone of Limewire)
Mplayer and mplayerplug-in version 3.05 for Firefox
totem-xine, Realplayer, VLC and Beep Media Player (with docklet)
Opera Browser
Bittornado and Azureus (Bittorrent clients)
Enables Numlock on (turns numlock on Gnome startup)
GnomePPP (Graphical Dial up connection tool)
MS true type fonts
NON-FREE audio and dvd codecs
Open Office to 2.0 (final version), installs openoffice clipart and installs OO2 thumbnailer.
SUN'S JAVA JRE version 1.5
wine
AMSN 0.95 (MSN client with webcam support)
Gamepads (Makes USB gamepads work)
Turns DMA ON on Intel and AMD machines (needs a restart)
NVIDIA cards (Detects Nvidia cards and installs drivers) (Needs a restart)
Adds midi capability to your Ubuntu box


I also installed Samba and the other thing beneath it in the shared folder settings (I don't know its name).

Now, what happens is that the system freezes, only the mouse can move, but nothing is active. This happened 3 times. The first time, I solved it by pressing reset. The next 2 times, I pressed the power button once and the computer shut down itself (as in Windows). During shutdown, I got a screen with distorted colours before the PC finally was shutdown.

The first 2 times I was browsing. The third time I was downloading Mozilla Browser from the Add Software Menu and I was also checking the RAM consumption in the system monitor window.

My system is a Celeron 1.2 GHz, 256 MB SDRAM, 128 MB GeForce 4 MX 440, 40 GB IDE ATA66 HDD, Dial-up modem PCI, PCI network card and a USB gamepad (I don't find a use for it in Linux, but I installed it during the gamepad driver installation!)

Sorry for the long post, but I really need your post. I am using my Windows PC now and I still have highspeed internet and a DVD burner, so I can easily download any fixes and move them to the other PC (I also have them connected by a home network, but without a switch).

Thanks!

---

### Post by Amorphous_Snake on 2006-04-10
Hello... your help will be greatly appreciated!

---

### Post by taurus on 2006-04-10
How much space (left) do you have on your Ubuntu?  Also, may want to have a peak at your ~/.xsession-errors to see if there is any error!

---

### Post by Amorphous_Snake on 2006-04-10
I have used only 8% of my 37 GB EXT3 partition.

I will get this info in about 2 hours. Is it a text file? Or do I have to write a command in the terminal?

---

### Post by taurus on 2006-04-10
It's a text file so you can use more from a terminal as
```

more ~/.xsession-errors

```

---

### Post by Amorphous_Snake on 2006-04-10
moataz@ubuntu:~$ more ~/.xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "moataz"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/ubuntu:/tmp/.ICE-unix/7301

** (gnome-session:7301): WARNING **: Host name lookup failure on localhost.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command =
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 1
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 0
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

(gnome-terminal:7494): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:7494): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:7448): WARNING **: IPP request failed with status 1030

---

### Post by Amorphous_Snake on 2006-04-10
Here is the file. Ubuntu crashed once during getting it!

---

### Post by taurus on 2006-04-10
What are the processes you have running when you boot your machine anyway.  Again, from a terminal, type
```

ps -A | more

```
Hit the space bar for the next page if it's more than one screen...  And yes, paste the output here if you don't mind!  ;)

---

### Post by Amorphous_Snake on 2006-04-10
OK I will get it. But is there anything else you might need? Because I have to go to another room, start the PC and be real quick before it freezes. Just tell me if there was anything else to get. I am waiting.

---

### Post by taurus on 2006-04-10
Not sure until I see what stuff you have running when your machine boots...  Sorry I can't give you a definite answer on that!  :-|

---

### Post by Amorphous_Snake on 2006-04-10
moataz@ubuntu:~$ ps -A | more
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
    5 ?        00:00:00 kthread
    7 ?        00:00:00 kacpid
   78 ?        00:00:00 kblockd/0
  104 ?        00:00:00 pdflush
  105 ?        00:00:00 pdflush
  107 ?        00:00:00 aio/0
  106 ?        00:00:00 kswapd0
  692 ?        00:00:00 kseriod
 1836 ?        00:00:00 khubd
 2912 ?        00:00:00 kjournald
 3038 ?        00:00:00 udevd
 5250 ?        00:00:00 kgameportd
 6020 ?        00:00:00 portmap
 6354 ?        00:00:00 acpid
 6369 ?        00:00:00 syslogd
 6386 ?        00:00:00 dd
 6388 ?        00:00:00 klogd
 6401 ?        00:00:00 dbus-daemon
 6414 ?        00:00:00 hald
 6419 ?        00:00:00 hald-addon-acpi
 6430 ?        00:00:00 hald-addon-stor
 6840 ?        00:00:00 gdm
 6844 ?        00:00:00 gdm
 6903 ?        00:00:06 Xorg
 6927 ?        00:00:00 cupsd
 6951 ?        00:00:00 hpiod
 6973 ?        00:00:00 python
 7174 ?        00:00:00 nmbd
 7176 ?        00:00:00 smbd
 7190 ?        00:00:00 rpc.statd
 7191 ?        00:00:00 smbd
 7204 ?        00:00:00 hcid
 7210 ?        00:00:00 sdpd
 7220 ?        00:00:00 krfcommd
 7239 ?        00:00:00 anacron
 7252 ?        00:00:00 atd
 7265 ?        00:00:00 cron
 7308 ?        00:00:00 timidity
 7312 tty1     00:00:00 getty
 7313 tty2     00:00:00 getty
 7314 tty3     00:00:00 getty
 7315 tty4     00:00:00 getty
 7316 tty5     00:00:00 getty
 7317 tty6     00:00:00 getty
 7338 ?        00:00:00 x-session-manag
 7380 ?        00:00:00 ssh-agent
 7383 ?        00:00:00 dbus-launch
 7384 ?        00:00:00 dbus-daemon
 7386 ?        00:00:01 gconfd-2
 7389 ?        00:00:00 gnome-keyring-d
 7391 ?        00:00:00 esd
 7395 ?        00:00:00 bonobo-activati
 7397 ?        00:00:00 gnome-settings-
 7400 ?        00:00:00 gam_server
 7412 ?        00:00:00 xscreensaver
 7436 ?        00:00:00 metacity
 7441 ?        00:00:01 gnome-panel
 7443 ?        00:00:01 nautilus
 7445 ?        00:00:00 gnome-volume-ma
 7450 ?        00:00:00 gnome-vfs-daemo
 7452 ?        00:00:00 wnck-applet
 7454 ?        00:00:00 trashapplet
 7460 ?        00:00:00 update-notifier
 7462 ?        00:00:00 gnome-cups-icon
 7464 ?        00:00:00 notification-da
 7475 ?        00:00:00 mapping-daemon
 7479 ?        00:00:00 notification-ar
 7481 ?        00:00:00 mixer_applet2
 7483 ?        00:00:00 clock-applet
 7487 ?        00:00:06 opera
 7502 ?        00:00:00 gnome-terminal
 7504 ?        00:00:00 gnome-pty-helpe
 7505 pts/0    00:00:00 bash
 7523 pts/0    00:00:00 ps
 7524 pts/0    00:00:00 more

---

### Post by Amorphous_Snake on 2006-04-10
Here it is. I started getting it before reading you message. It crashed 3 times. But I think that it's something on the "outside" because the computer shuts down normally (without anything on the screen other than the distortions I mentioned before) when I press the power button once.

---

### Post by Amorphous_Snake on 2006-04-10
Hello...

Unfortunately I can't stay any longer. Everyone, please leave what you think should be done here and I will do it tomorrow. It's 1.30 am now in Egypt, and I have to wake up early.

Thanks everyone.

---

### Post by Amorphous_Snake on 2006-04-11
Come on guys... Help me!

---

### Post by sublime on 2006-04-11
make sure you have enough power from your power supply.  if you jsut installed some new hardware, that could be a cause.  also check and see if your processor isnt over heating.  make sure the fans are going on.  make sure there isnt a ton of dust in the heatsink and fans.  try turning the comp on without any excess cards or hardware.  just use the barebones.

---

### Post by Amorphous_Snake on 2006-04-11
I am sure that my hardware is good. This problem happened soon after downloading and installing the programs/updates from Automatix. Maybe I installed something that caused incompatibility.

---

### Post by sublime on 2006-04-11
automatix is just a program self-installer.  but if you think thats it then go with it.  if you dont have anything of importance and since it was a fesh install, why not just format and reinstall?  if it was caused by automatix, tehn at least that will give you a stable system again.  then you can go through installing one program at a time from automatix and see which one might give you problems.

---

### Post by Amorphous_Snake on 2006-04-11
I switched on my PC today and strange.... it doesn't freeze!

How can you uninstall JAVA and the nVidia drivers? I think that's the problem.

---

### Post by nalmeth on 2006-04-11
Sorry I don't know exactly how to uninstall java or your nvidia drivers, but when I have problems I always upgrade to the newest packages in the repositories and suprisingly things get cleared up.
There might be updates available in the system tray/notification area, or if you don't mind the terminal, open it up and
sudo apt-get update
sudo apt-get upgrade

Hopefully since last time you booted everything is indeed working well. This is not normal behavior.

---

### Post by Amorphous_Snake on 2006-04-11
Thanks Nalmeth. I already have the latest version of everything. But if I download the latest driver from nvidia.com and install it, will it overwrite the existing driver?

---

### Post by nalmeth on 2006-04-11
Essentially yes. If you really want to do this, follow this guide to doing so:
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by Amorphous_Snake on 2006-04-13
I didn't try the above solution yet. But as I noticed that the system freezes only when I am browsing, I tried to uninstall opera, firefox, thunderbird (not a browser, but I also tried to remove it), all of firefox plugins, etc.
I managed to remove all except Firefox, which I must remove from Synaptic. I'll try to do this tomorrow, and I'll also remove Java and OpenOffice, and see what happens. But before this, I'll try reinstalling the nVidia drivers.

---

### Post by Amorphous_Snake on 2006-04-14
Damn!

I reinstalled Ubuntu. I checked for the latest updates through Update Manager. I downloaded them. I installed Automatix (but didn't download anything from it, then), I noticed that there are more updates in the Update Manager. I downloaded them.

Next I opened Automatix and downloaded the nVidia drivers. I restarted. Then, I downloaded: Media players, non-free plugins, DMA on, NumLock on, FrostWire and MS true type fonts. I avoided Firefox updates and plugins. But during install, I noticed that Java started to get dwnloaded and installed, although I didn't select it.

Then came the test... I opened Firefox (1.07) and started browsing, and then... bang! The system froze, again! I pressed the power button once and the PC shutdown itself, as usual (if you have been reading all my above posts!).

Please, people, I need help!

---

### Post by Amorphous_Snake on 2006-04-14
Well... I thought Ubuntu had a nice community that is willing to help new comers. I guess I was wrong. I won't beg for help anymore. If anyone wants to help, he/she is more than welcome, but this is the last time I am posting in this topic.

I am disappointed!

---

### Post by Sonic132 on 2006-04-14
I am beginning  to have the same problem myself. I had a very small partition that Windows created accidentally during setup that I decided to use as a Linux partition. So now, running the livedisc and trying to download the full install. I opened Terminal, not fully knowing what it was, and everything freezes for 20mins or so.
Does anyone know how much space is needed for the Ubuntu Live CD on the HD?

---

### Post by Sonic132 on 2006-04-14
[QUOTE=Amorphous_Snake]Well... I thought Ubuntu had a nice community that is willing to help new comers. I guess I was wrong. I won't beg for help anymore. If anyone wants to help, he/she is more than welcome, but this is the last time I am posting in this topic.

I am disappointed![/QUOTE]
Unless I'm mistaken. Isn't everyone trying to help you already? :-k 
Some people are just plain stupid.

---

### Post by keikov on 2006-04-14
Hi Amorphous_Snake..
I have the exact same problem.. :(  i guess it's because of the video card.. since i have the same geforce mx 440, and remember having those distortions with other linux distribution.. but then it did not freeze.. now it does.

maybe nalmeth's suggestion will work.. i'll try it and let you know if it solves the problem..

---

### Post by Amorphous_Snake on 2006-04-14
[QUOTE=Sonic132]Does anyone know how much space is needed for the Ubuntu Live CD on the HD?[/QUOTE]

None.

And thanks for showing me how polite you are!

---

### Post by Amorphous_Snake on 2006-04-14
[QUOTE=keikov]Hi Amorphous_Snake..
I have the exact same problem.. :(  i guess it's because of the video card.. since i have the same geforce mx 440, and remember having those distortions with other linux distribution.. but then it did not freeze.. now it does.

maybe nalmeth's suggestion will work.. i'll try it and let you know if it solves the problem..[/QUOTE]

Oh God, I hate this card! It gave me hell when I ran Windows. Any new game will have the line "MX not supported". Now it's giving me hell in Linux! A good thing is that I got a GF6600 for my main PC.

---

### Post by Mustard on 2006-04-14
Wouldn't the geforce mx 440 need to use the legacy drivers?  The current nvidia drivers won't work with obsolete cards.

-edit-

Hmm..nevermind.  I think I'm confused about how old your graphics card is.  In your first posts you've described it as a geforce4 mx 440 card and then later it described as a geforce mx 440.  So I'm quite lost as to whether this card is old or not.  If it is an older card though, you will need the nvidia-legacy drivers.

---

### Post by Amorphous_Snake on 2006-04-15
What are the nVidia legacy drivers?

The card is a GeForce 4 MX 440. I didn't say that it was a GeForce MX, that was another user who said so. But my card is not listed among the cards that are not compatible with the latest drivers from nvidia.com

---

### Post by Mustard on 2006-04-15
It's ok, you don't need them for that card.

---

### Post by Amorphous_Snake on 2006-04-15
I am reinstalling Ubuntu again! (My 4th installation!). I am not going to install the nVidia drivers for now. But the screen is set at 1024x768 @ 60 Hz which is really irritiating. Even at 800x600 it is still @ 60 Hz. How can I fix this without installing any video drivers?

---

### Post by keikov on 2006-04-15
My mistake.. forgot the 4 in GeForce4 MX 440 :oops:

Tried installing the drivers downloaded from nvidia site.. but did not succeed
I had a default installation and seems that there were packages not installed, and the pc freezed many times while trying to add them..

this worked for me:
==================================
- Press Esc when booting
it will show a menu with 3 boot options
select to enter recovery mode
(it will start in console mode with root logged already)

- startx (to load graphic mode)
- go to: System>Administration>Add applications
there choose File>advanced
check and install the following components from the list
  * nvidia-glx
  * nvidia-settings
-log out -- System>Log Out
-back in console mode type:
Sudo nvidia-glx-config enable (maybe sudo is not necessary)
that will enable the driver
==================================
while doing that i had internet connection, and it downloaded
nvidia-glx and nvidia-settings from internet.
the downloaded version are: 
 * nvidia-glx 1.0.7667-0ubuntu25.1
 * nvidia-settings 1.0-3ubuntu6

maybe it's not necessary to be connected, but i'm not sure if it downloaded more recent version of the files.

i found an article on internet that shows the same thing, but it does not log in to graphic mode to install the driver. Not sure if doing it that way would check for more recent versions:

[http://easylinux.info/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29](http://easylinux.info/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29)
also shows how to create a "shortcut" to nvidia setting

[http://easylinux.info/wiki/Ubuntu#How_to_disable_NVIDIA_graphics_logo_on_GNOME_startup](http://easylinux.info/wiki/Ubuntu#How_to_disable_NVIDIA_graphics_logo_on_GNOME_startup)
there they show how to get rid of the nvidia logo when starting graphic mode.

hope it will solve your problem

---

### Post by Amorphous_Snake on 2006-04-15
Thanks Keikov. I haven't done what you posted, I'll try to install the latest nVidia drivers (The one you installed isn't the latest). If it didn't work out, I'll do what you said.

To all out there: I am 100% sure that the problem is from the driver that I installed in Automatix. If you have a GF4 MX 440, avoid this at all costs! I downloaded everything (almost) from Automatix, except the drivers, and the system is working just fine. Can anyone add this to the Wikis or the Automatix HowTo?

And I am sorry for being rude in one of the above posts.

---

### Post by Mustard on 2006-04-15
Glad to see both of you worked the problem out.  :)

---

