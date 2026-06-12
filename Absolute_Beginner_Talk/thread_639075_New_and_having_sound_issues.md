---
title: "New and having sound issues"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Evil Jinn on 2007-12-12
I just installed Ubuntu 7.10 and know absolutely nothing about Linux.  I did manage with a bit of help and alot of trial and error over the past day to get my ET and PB up and running.  Now if someone would be kind enough to help me set up my sound for ingame, I'd really appreciate it.

When I do the sound tests in the volume control panel, I can hear all the sounds.  When I initiate ET, I get no ingame sound.

Also, I have my ET and PB path here:  /usr/local/games/enemy-territory/et by setting a customized desktop icon.  Now if i can get sound, I'll be all set to frag the daylights outta the guys. :biggrin:

Please be very specific with your instructions if you help, because this is all new to me.  I need to know exactly what to put where.  Make an example.

---

### Post by DutyDuty on 2007-12-12
Make sure you are running alsa properly.

---

### Post by Evil Jinn on 2007-12-12
I had a few people helping me find the info I needed to solve this problem.

Here's the solution for solving this problem.

I changed my settings on sound/volume control to OSS option.(Also make sure your speakers/headphones are not muted)


to make sound work(temporary until reboot):

 Code:
 sudo -s 
 echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
 echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 
 exit

===========================================
 
 
 
to get this commands started after booting automatically: 
 

open an editor with root rights (gedit) and type 
 
Code:
 #!/bin/sh 
 #Bug in Wolfenstein ET 
 echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss 
 echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
 
save the file as "et-sound" in "/etc/init.d/". after this file is created you need to tell your system about it: 
 
Code:
 sudo chmod 755 /etc/init.d/et-sound 
 sudo update-rc.d et-sound defaults

---

