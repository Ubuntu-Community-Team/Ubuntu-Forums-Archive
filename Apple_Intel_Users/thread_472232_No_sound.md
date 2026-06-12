---
title: "No sound"
date: 2007-06-12
forum: Apple Intel Users
---

### Post by Citizen Nate on 2007-06-12
Sorry for the question that's been asked too many times. I'm running a dual-boot of osx and ubuntu on an intel quad-core mac-pro, and there is no sound. There are a very large number of posts about such a problem, but none of the fixes seem to work. Does anyone know how to get it working?

---

### Post by nicfagn on 2007-06-13
If I'm not wrong, Feisty doesn't support macpros directly. You probably have to install the latest alsa sound driver (1.0.14) from source code.
Before doing this, you should post some info about your sound configuration like the output of the following commands:

- lspci -v
- cat /proc/asound/card0/codec#0
- amixer

From this data it is possible to see if your system is supported and the mixer volumes configuration.

Bye

Nicola

---

### Post by Citizen Nate on 2007-06-13
I attached the files to this post. Another problem: After a recent "fix", the volume icon on the top-right has disappeared. I killed a process that was controlling it (And didn't reopen after prompt about a crash), and after a reboot, the icon is still gone.

---

### Post by nicfagn on 2007-06-13
Sound support for macpro macs was introduced in alsa 1.0.14rc2 and subsequently refined until the current 1.0.14 release. 
I don't have a clean Feisty install but, if I remember correctly, the alsa version was 1.0.14rc1. 
You can verify your version with:
```
cat /proc/asound/version 
```
If you want sound working I think the best option is to do as follows.
Download [alsa-driver-1.0.14]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2") and expand it in a directory of your choice then open a terminal window and cd into the alsa-driver-1.0.14 directory.
Do a configure for the HDA intel chipset:
 
```
./configure --with-cards=hda-intel
```

Install the libc6 developer libraries and headers, if missing:

```
sudo apt-get install libc6-dev
```

Compile with the make command:

```
make
```

To Install the compiled modules:

```
sudo make install-modules
```

Restart the sound subsystem:

```
sudo /etc/init.d/alsasound restart
```

Reload the snd_hda_intel module:

```
sudo modprobe snd_hda_intel
```

If you have problems restarting alsa, simply reboot.
If all went ok, you should hear sound now ;)
Unfortunately, you have to repeat this process every time you update the kernel.

About the icon you can try this: right click on the top panel and select the 'add to panel' menu item, then choose the volume applet and add it to the panel.

Bye

---

### Post by Citizen Nate on 2007-06-13
I updated to alsa 1.0.14rc4, and there is still no sound.

---

### Post by nicfagn on 2007-06-14
You can try to unmute and raise the volume of playback channels with alsamixer (type alsamixer in a terminal  window, left and right arrow keys to move between channels, spacebar to toggle mute on a channel, up and down arrow keys to change the volume level).

You should check if you have any of the files /etc/asound.conf or ~/.asoundrc*, rename them and restart alsa.

If the above doesn't work, you can create a new user and log on with it to check if sound works with a clean user configuration.

If everything fails you should post your configuration files again plus the output of 'cat /proc/asound/version', hopefully I could spot the anomaly.

Some questions: no sound only from the speakers or from the headphones too? The sound works in Mac Os X, right?

Bye

---

### Post by Citizen Nate on 2007-06-14
It "just works" with OSX, and the startup sound works fine too. I haven't heard a bit of sound from ubuntu on anything.

---

### Post by Citizen Nate on 2007-06-14
Nothing. Here are the configuration files again.
I have tested sound on internal speakers, headphones plugged into the normal slot, usb speakers, and headphones plugged into the usb speakers. My guess is that it isn't a problem with the drivers. If I can't get this working, is it possible I can get AirTunes working?
BTW, the main reason I'm doing this is to get DDR working on a computer with a dance-pad. The dance-pad didn't work in OSX, so I'm trying linux.

---

### Post by nicfagn on 2007-06-14
Sorry Citizen Nate. I didn't find anything relevant, as far as I know, in your config files.
Unfortunately I don't have a quad-core macpro to test the code, I assumed it was working from the alsa commit log...
Is there anyone with macpro sound working? If so, please chime in!

Bye
Nicola

---

