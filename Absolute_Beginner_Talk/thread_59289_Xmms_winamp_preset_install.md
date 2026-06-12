---
title: "Xmms winamp preset install"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by Rick069 on 2005-08-23
Is anyone besides me having a hell of a time trying to get the winamp presets for xmms to work? I've already put the eq.preset file into the appropriate folder and still the preset aren't loading or even show up on the list. Any suggestions? There are a lot of music players out there for linux with equalizers, but I only know of one that has presets. What the hell do I know about manually setting an equalizer.

---

### Post by joshpelkey on 2005-08-24
You've downloaded [this](http://www.xmms.org/misc/winamp_presets.gz) file and then issued this command: gunzip -c winamp_presets.gz > ~/.xmms/eq.preset ??

---

### Post by Rick069 on 2005-08-25
Ok, I've got everything to show up on the preset list, but the presets don't seem to have any effect on the music. I've made sure that the equalizer is on and I think I checked everything that I could. Anybody got any ideas?

---

### Post by joshpelkey on 2005-08-25
I won't be able to look at xmms til I get off work and home, but hopefully if you need a faster reply, someone else can help you.  You said that the presets seem to have no effect; when you change the equalizer manually, do you notice a difference?  Whenever I select a preset, it takes about 2-3 seconds to take effect.  Hope you figure it out soon!

---

### Post by psylvester on 2005-09-20
hi guys,
Im new to this linux. I need a hel-p, Hope anyone can help me.
I want to install Xmms. I installed.

#sudo apt-get install xmms

and it installed. When i open one Mp3 song, it doesnt play. The problem is , it just stays like hanged. The only thing i can do is , minimise and maximise, Nothing else.
I wonder if i have installede properly.

Can anyone help me ? thanks

sylvester.

---

### Post by Kapre on 2005-09-20
[QUOTE=psylvester]hi guys,
Im new to this linux. I need a hel-p, Hope anyone can help me.
I want to install Xmms. I installed.

#sudo apt-get install xmms

and it installed. When i open one Mp3 song, it doesnt play. The problem is , it just stays like hanged. The only thing i can do is , minimise and maximise, Nothing else.
I wonder if i have installede properly.

Can anyone help me ? thanks

sylvester.[/QUOTE]
psylvester - you need to change your sound settings in XMMS. Click on the upper portion of the XMMS and select sound settings.change it from OSD to ESD or OSS to whatver will work for you. Change it one at a time and try to load mp3 music.

K

---

### Post by joshpelkey on 2005-09-20
Most likely your install was just fine.  In order to play mp3's you have to download the appropriate codec.  streamer0.8-mad is what you will need i think.  Check out [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) first because I could be wrong.  I think all i did was "sudo apt-cache search mp3" and installed some of the mp3 codecs and eventually it worked  ;-)  Not exactly precise, but hey it's working!

---

### Post by psylvester on 2005-09-20
root@ubuntu:/home/sylvu # sudo apt-get install gstreamer0.8-misc
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-misc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@ubuntu:/home/sylvu # sudo apt-get install xmms
Reading package lists... Done
Building dependency tree... Done
xmms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/home/sylvu #


still it doesnt work...! when i play it just hangs.. let me restart xmms and give a try

---

### Post by psylvester on 2005-09-20
what will be the name of the process (xmms); i want to kill it..

---

