---
title: "tascam US-122 and feisty"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by elov on 2007-08-22
We followed all the directions from richardjennings post and are trying to make it the default soundcard and it still is not working. The USB light on the Tascam came on as soon as we pluged it in to anything, i guess thats normal, we're just going crazy thinking of what it is. Please          help. this is what we're getting for 4a and 4b steps      
elov@elov-desktop:~$ sudo mv alsa-firmware-1.0.14rc3/usx2yloader/ /lib/firmware/mv: cannot move `alsa-firmware-1.0.14rc3/usx2yloader/' to a subdirectory of itself, `/lib/firmware/usx2yloader'
elov@elov-desktop:~$ sudo cp -r /lib/firmware/usx2yloader /usr/share/alsa/firmware/
cp: target `/usr/share/alsa/firmware/' is not a directory: No such file or directory

---

### Post by kidcharles on 2007-08-22
Could you provide a link to the post you are referring to?

---

### Post by elov on 2007-08-22
sure.

[http://ubuntuforums.org/showthread.php?t=431066&page=2](http://ubuntuforums.org/showthread.php?t=431066&page=2)

and this is the post i'm referring to:

 Re: HOWTO: Tascam US-122 in Fiesty
this is the revised howto: aka post1. I'd like to think this is now completely correct. I apologize for previous inaccuracies.

revision 2 /16/05/07

I have followed several tutorials that have led to success. However every one I have found requires manually introducing the Tascam to Ubuntu after a reboot or an unplug.

This following procedure worked perfectly for me in Fiesty, is easy to do, and best of all - allows you to hot plug your Tascam, reboot & just generally take it easy.

I found the original tutorial here : [http://alsa.opensrc.org/Tascam_US-122](http://alsa.opensrc.org/Tascam_US-122)

Unplug the Tascam US-122 USB cable

1)
Code:

sudo apt-get install fxload alsa-firmware-loaders

2)
Code:

wget [http://www.alsa-project.org/alsa/ftp/firmware/alsa-firmware-1.0.14rc3.tar.bz2](http://www.alsa-project.org/alsa/ftp/firmware/alsa-firmware-1.0.14rc3.tar.bz2)

3)
Code:

tar xjf alsa-firmware-1.0.14rc3.tar.bz2

4)
Code:

sudo mv alsa-firmware-1.0.14rc3/usx2yloader/ /lib/firmware/

4b)
Code:

sudo cp -r /lib/firmware/usx2yloader /usr/share/alsa/firmware/


//revision 1

5)

Code:

 sudo gedit /etc/udev/rules.d/55-tascam.rules

the rules file is now open in gedit..

6) copy the following into the 55-tascam.rules file in gedit

Code:

 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8006", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/sbin/fxload -D %N -s /lib/firmware/usx2yloader/tascam_loader.ihx -I /lib/firmware/usx2yloader/us122fw.ihx'"
 BUS=="usb", ACTION=="add", SYSFS{idProduct}=="8007", SYSFS{idVendor}=="1604", RUN+="/bin/sh -c '/usr/bin/usx2yloader'"

Save the file.


Plug in your usb cable and your tascam usb led should light up.

//revision 2

assuming it does, you can add another rule to 55-tascam.rules that automatically configures alsa to use the tascam as your default soundcard.

repeat step 5)

add below the previous rule:
Code:

KERNEL=="pcmC[D0-9cp]*", ACTION=="add", PROGRAM="/bin/sh -c 'K=%k; K=$${K#pcmC}; K=$${K%%D*}; echo defaults.ctl.card $$K > /etc/asound.conf; echo defaults.pcm.card $$K >>/etc/asound.conf'"
KERNEL=="pcmC[D0-9cp]*", ACTION=="remove", PROGRAM="/bin/sh -c 'echo defaults.ctl.card 0 > /etc/asound.conf; echo defaults.pcm.card 0 >>/etc/asound.conf'"

Save the file

unplug / plug your tascam back in.

Now alsa should be working correctly with the tascam!

_____________________________________________________________________
since then the only thing that has changed is that we've totally lost sound (from the original soundcard)

---

### Post by kidcharles on 2007-08-22
I think we are just looking at a simple case of non-preexisting folders. Why don't you try this set of codes instead as a replacement for his steps 4. and 4b. Run these commands from the directory where you downloaded alsa-firmware-1.0.14rc3.tar.bz2 to (probably your home folder). The 'mkdir' lines are to 'make directories'.

```

sudo mkdir /lib/firmware
sudo mv alsa-firmware-1.0.14rc3/usx2yloader/ /lib/firmware/
sudo mkdir /usr/share/alsa/firmware
sudo cp -r /lib/firmware/usx2yloader /usr/share/alsa/firmware/

```

If there are any errors during this, come back for help.

---

### Post by elov on 2007-08-22
ok now we got a string of error messages that we've never got before.... 

elov@elov-desktop:~$  sudo gedit /etc/udev/rules.d/55-tascam.rules
ALSA lib conf.c:974: (parse_value) card is not a string
ALSA lib conf.c:1587: (snd_config_load1) _toplevel_:2:0:Invalid argument
ALSA lib conf.c:2848: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075: (snd_config_update_r) hooks failed, removing configuration
ALSA lib conf.c:974: (parse_value) card is not a string
ALSA lib conf.c:1587: (snd_config_load1) _toplevel_:2:0:Invalid argument
ALSA lib conf.c:2848: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075: (snd_config_update_r) hooks failed, removing configuration
ALSA lib conf.c:974: (parse_value) card is not a string
ALSA lib conf.c:1587: (snd_config_load1) _toplevel_:2:0:Invalid argument
ALSA lib conf.c:2848: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075: (snd_config_update_r) hooks failed, removing configuration
ALSA lib conf.c:974: (parse_value) card is not a string
ALSA lib conf.c:1587: (snd_config_load1) _toplevel_:2:0:Invalid argument
ALSA lib conf.c:2848: (snd_config_hook_load) /etc/asound.conf may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712: (snd_config_hooks_call) function snd_config_hook_load returned error: Invalid argument
ALSA lib conf.c:3075: (snd_config_update_r) hooks failed, removing configuration




somethings that i'm worried about. we've done this process a million times and possibly the files are backing up or something. also there's some of the rules repeated in the gedit file from different people trying to work on it. its a mess.

---

### Post by elov on 2007-08-22
(i had to edit the code because it was giving me a :( face)

---

### Post by kidcharles on 2007-08-22
This problem has officially become "out of my league" :). You might try a new post starting where this one left off, perhaps in the "Multimedia and Video" forum. Otherwise hopefully someone else will chime in.

---

### Post by elov on 2007-08-22
if theres a god

---

### Post by elov on 2007-08-26
anyone?

---

