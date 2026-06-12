---
title: "macbook 4,1 sound quiet"
date: 2008-05-22
forum: Apple Hardware Users
---

### Post by skiwithpete on 2008-05-22
Hi,

My sound volume (even at max) is still very quiet.  Is there a way to make it louder? 

Am a newb so please go slow.

P

---

### Post by vanakush on 2008-05-26
hi
i have Macbook4,1 and using Ubuntu hardy heron 8.04 live cd, i can't hear any sound from internal speakers as well as from earphones connected to phone output i have tried installing alsa-driver 1.0.16 using following commands but it is not working

1.sudo apt-get update
2. sudo apt-get install build-essential
3. cd '/home/ubuntu/Desktop/alsa-driver-1.0.16' <-------- extracted package location.
4. ./configure
5. make
6. sudo make install.
7.sudo /etc/init.d/alsasound restart

pls help...........

---

### Post by maxmartin on 2008-05-26
I recently installed a Hardy partition on my Macbook, and I encountered some similar sound issues. To take care of them, I followed these instructions from the[Macbook community documentation]("https://help.ubuntu.com/community/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d"):

> 1. Add the following line to /etc/modprobe.d/alsa-base:

install snd-hda-intel position_fix=1 /sbin/modprobe --ignore-install snd-hda-intel $CMDLINE_OPTS && /lib/alsa/modprobe-post-install snd-hda-intel

2. Increase the volume (both using the key combination and the system tray applet) to its maximum possible value.

3. Right-click on the volume applet and choose Preferences. Select "PCM" as the device to control.

4. Open the Sound preferences (System-Preferences-Sound in GNOME). Select "PCM" as the device to control.

The above setting changes (step 3 and 4) can be done via the command line using these two gconftool-2 commands:

gconftool-2 --type list --list-type string --set /desktop/gnome/sound/default_mixer_tracks [PCM]
gconftool-2 --type string  --set /apps/panel/applets/mixer_screen0/prefs/active-track PCM

Also, I opened volume control (by right-clicking on the system tray volume applet) and increased the master volume some from where it was, and additionally added the surround track (which my headphones wouldn't work without) via the volume control preferences, and unmuted it. After that, sound worked fine.

---

### Post by skiwithpete on 2008-05-26
Yeah, I did that too, and it installed the device correctly, but at maximum volume (both in program [like VLC] and on system) the volume is still very quiet.  

Again, it works fine, its just quiet.  At 75% it is almost muted.  at 50% even in dead silence I can't hear anything. 

And, yes, I have right clicked and put the volumes up to max on all outputs.

I'm looking for some way to increase the volume.

---

### Post by maxmartin on 2008-05-26
I had that same problem, and I think it was the surround thing that did it for me. That, or my problem was randomly or unintentionally solved some other way at the same time.

---

### Post by stueng on 2008-05-27
None of this stuff is necesarry, you just need to edit one file... please read my guide here

[http://www.lostpeg.co.uk/content/view/36/78/]("http://www.lostpeg.co.uk/content/view/36/78/")

Since you are working off a live CD you obviously cant reboot and have the changes take effect - you should try restarting ALSA... or install Ubuntu :)

---

### Post by cunning linguist on 2008-05-27
I've tried all that and nothing seems to do it for me :-) no sound whatsoever.

I've got Ubuntu 8.04 on an intel MacBook. The installation went perfectly well, rEFIt is doing what it's supposed to do, all's well except for the sound which is missing. Nothing I do seems to change that :confused:

Any help or pointers appreciated!

---

### Post by cyberdork33 on 2008-05-27
> **cunning linguist said:**
> I've tried all that and nothing seems to do it for me :-) no sound whatsoever.

I've got Ubuntu 8.04 on an intel MacBook. The installation went perfectly well, rEFIt is doing what it's supposed to do, all's well except for the sound which is missing. Nothing I do seems to change that :confused:

Any help or pointers appreciated!If you have a Macbook4,1 like the OP, then you should use the information here:
[https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd](https://help.ubuntu.com/community/MacBook_Santa_Rosa#head-6a2f3399bd41e87c39ff69ff7a48a1953db51cdd)

---

### Post by cunning linguist on 2008-05-27
> On Hardy, after making this change you need to enable your speakers

OK, I'm stupid. All this while it was because my speakers weren't enabled. Kind of strange that you'd have to do that separately, but my bad for not reading carefully. Thanks for the hint, cyberdork33! Greatly appreciated.

---

### Post by skiwithpete on 2008-05-28
Stueng

I followed your instructions and yet the problem persists.  

At 100% volume it is audible, at 75% almost inaudible, and at 50% completely gone.


P

---

### Post by mariguango on 2008-05-28
I make all changes, and found one problem - when i use volume keys - it change both PCM and Surround levels, how i may make changes only in one? When other will be fixed?

---

### Post by cyberdork33 on 2008-05-28
> **skiwithpete said:**
> Stueng

I followed your instructions and yet the problem persists.  

At 100% volume it is audible, at 75% almost inaudible, and at 50% completely gone.


PI am unsure what your issue is due to. My post was directed at cunning linguist. The only thing i can offer is this. On my iMac, there are actually two different channel that have to be adjusted to get sound. Adjusting the Master channel doesn't do anything at all, and PCM adjusts the overall sound volume, but adjusting other channels such as "surround" can have an unexpected effect.

> **mariguango said:**
> I make all changes, and found one problem - when i use volume keys - it change both PCM and Surround levels, how i may make changes only in one? When other will be fixed?
You can change the channel that your volume keys adjust in System > Preferences > Sound.

Nothing will get fixed if a bug doesn't get filed (the devs won't even know something is wrong).

---

### Post by mariguango on 2008-05-30
where i should post bugs? in lounchpad i read that this place for developers.

---

### Post by pxwpxw on 2008-05-30
> **mariguango said:**
> where i should post bugs? in lounchpad i read that this place for developers.


[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by cyberdork33 on 2008-05-30
> **mariguango said:**
> where i should post bugs? in lounchpad i read that this place for developers.

launchpad is a place for developers, that is why you need to report bugs there so that the developers will see them. :)

---

