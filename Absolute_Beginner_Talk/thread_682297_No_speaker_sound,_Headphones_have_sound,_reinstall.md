---
title: "No speaker sound, Headphones have sound, reinstalled alsamixer"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by spyman40 on 2008-01-29
I've recently installed Ubuntu and everything works great except for some reason no sound seems to want to come out of my speakers. 

I'm not quite sure what information I should be posting along side this or what commands to run, I had looked up some posts on how to reinstall alsamixer and tried to manually re-install and then after being introduced to the repository i used that the re-install alsa. 

Sound does work if I plug headphones, so I would assume the driver is loading fine.

And yes I've muted and unmuted every sound channel in various configurations. 

Any tips or additional information I should post would be greatly appreciated

Thanks in advance.

---

### Post by spiderbatdad on 2008-01-29
You might try```
asoundconf list
```
this should produce a card parameter. Then:```
asoundconf set-default-card PARAMETER
``` where PARAMETER is the output of the previous command. This will create a hidden file in you home directory called .asoundconfrc.asoundconf  It is a configuration file for alsa.
Also. checkout```
man asoundconf
```

---

### Post by spyman40 on 2008-01-29
Ok I ran the commands you have given me and the file contains something that looks a little like this:

!defaults.pcm.card Intel
defaults.ctl.card Intel
defaults.pcm.device 0
defaults.pcm.subdevice -1
defaults.pcm.nonblock 1
defaults.pcm.ipc_key 5678293
defaults.pcm.ipc_gid audio
defaults.pcm.ipc_perm 0660
defaults.pcm.dmix.max_periods 0
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format S16_LE
defaults.pcm.dmix.card defaults.pcm.card
defaults.pcm.dmix.device defaults.pcm.device
defaults.pcm.dsnoop.card defaults.pcm.card
defaults.pcm.dsnoop.device defaults.pcm.device
defaults.pcm.front.card defaults.pcm.card
defaults.pcm.front.device defaults.pcm.device
defaults.pcm.rear.card defaults.pcm.card
defaults.pcm.rear.device defaults.pcm.device
defaults.pcm.center_lfe.card defaults.pcm.card
defaults.pcm.center_lfe.device defaults.pcm.device
defaults.pcm.side.card defaults.pcm.card
defaults.pcm.side.device defaults.pcm.device
defaults.pcm.surround40.card defaults.pcm.card
defaults.pcm.surround40.device defaults.pcm.device
defaults.pcm.surround41.card defaults.pcm.card
defaults.pcm.surround41.device defaults.pcm.device
defaults.pcm.surround50.card defaults.pcm.card
defaults.pcm.surround50.device defaults.pcm.device
defaults.pcm.surround51.card defaults.pcm.card
defaults.pcm.surround51.device defaults.pcm.device
defaults.pcm.surround71.card defaults.pcm.card
defaults.pcm.surround71.device defaults.pcm.device
defaults.pcm.iec958.card defaults.pcm.card
defaults.pcm.iec958.device defaults.pcm.device
defaults.pcm.modem.card defaults.pcm.card
defaults.pcm.modem.device defaults.pcm.device
defaults.rawmidi.card 0
defaults.rawmidi.device 0
defaults.rawmidi.subdevice -1
defaults.hwdep.card 0
defaults.hwdep.device 0
defaults.timer.class 2
defaults.timer.sclass 0
defaults.timer.card 0
defaults.timer.device 0
defaults.timer.subdevice 0
defaults.namehint.showall off
defaults.namehint.basic on
defaults.namehint.extended off

I'm not exactly sure which values would mostly cause problems so some additional direction would be helpful. 

Also if restarting would be advisable at some point in time let me know when to do so

Oh and the output of asoundconf list was "Intel". Gnome volume control shows Realtek ALC885 (OSS Mixer) and HDA Intel (Alsa Mixer). Not sure if that helps at all.

---

### Post by spiderbatdad on 2008-01-30
hmmm. my understanding, from using the search utility, and searching file system for asoundconf, then reading the documentation, and reading```
 man asoundconf
```, was that the above commands would generate the necessary file for alsa to work properly. If you read the same documentation, you'll see there are some other commands to run which may solve your issue...like pulse audio. I have read that the file should not be edited by hand, but instead, through the use of asoundconf commands.
Sorry if this was of no help to you.

The "intel" output of asoundlist seems lacking...maybe a driver issue. my output is: I82801CAICH3 and it is an intel card. I have no idea what would happen if you tried that as the parameter...personally, I'll try anything once. But then I've had to re-install my os several times. You can always disable that configuration file by commenting out ( adding # to the beginning) of the script line in the .asoundrc file...that's the other hidden file in the home directory with one line of script in it.

---

### Post by BandD on 2008-01-30
> **spyman40 said:**
> 
Oh and the output of asoundconf list was "Intel". Gnome volume control shows Realtek ALC885 (OSS Mixer) and HDA Intel (Alsa Mixer). Not sure if that helps at all.


I don't know if you've looked through these threds yet, but they may help:

[https://help.ubuntu.com/community/HdaIntelSoundHow to]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

[http://ohioloco.ubuntuforums.org/sho...d.php?t=530374]("http://ohioloco.ubuntuforums.org/sho...d.php?t=530374")

I don't have this particular chip set, I've got an HDA Intel ICH6 family with a Realtek ALC260 and had some trouble with the mic not working. I finally got it working by editing /etc/modprobe.d/alsa-base with an option where model=acer (even though I'm on a Sony Vaio) at the bottom of the file.

But both of those post might point you in the right direction.  Also, you might look into upgrading from ALSA 1.0.14 to 1.0.15, as it has much better support for the HDA intel devices.

Let us know how it goes.

---

### Post by Jmejme on 2008-01-30
i have the same problem except no sound even with the head phones...? any clue?

---

