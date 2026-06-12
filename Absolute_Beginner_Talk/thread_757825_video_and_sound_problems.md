---
title: "video and sound problems"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by GaussianMonk on 2008-04-17
I'm running Kubuntu Gutsy, and I've spent a few days trying fix a couple of problems on my own/with a friends help with no luck. 

First, I was fiddling with monitor settings the day after I installed and something I did crashed KDE. Ever since then I haven't had any sound. When I run alsa from terminal it shows up as functioning, but Kmix is completely dead. I tried to install OSS as a replacement but haven't had any luck yet. 

Second, my glx is restricted to superuser. When i run glxgears in terminal I get about 300fps, but when I run sudo glxgears I get ~1560. Video card is Mobility X1400.

Any help with either problem is greatly appreciated.

---

### Post by victorgreen on 2008-04-17
Im sorry I cant be much help with ati drives [damn them!] but as for sound, my best solution whenever I kill my sound for whatever reason is to recompile alsa

head over to [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)  and download the latest alsa driver release, currentltly 1.0.16, It comes down as a tar. Untar it and move it to folder of your choice. In terminal, cd into the folder where you left the alsa driver source code [lets say I created a folder in home called src, so "cd ~/src/alsa-driver-1.0.16". 

Then you run the commands:
./configure  [this takes time]
when it is done run

make
    this will take more time, when it is done run

sudo make install 
    this will also take time

When these operations are complete, reboot and hopefully you will have sound if you tell your computer to try and use alsa again over oss.

---

### Post by mick8985 on 2008-04-17
Sounds like somehow  your user is not associated with the video groups, do```
sudo nano /etc/group
```
look for the line beginning "video:" and add your user (preceded by a comma if there are other users associated with it)
mine looks like
```
video:x:44:michael
```
It is possible your audio problems are happening for the same reason so while you have the file open check for the line beginning with "audio:"
mine looks like
```
audio:x:29:pulse,michael
```
I have the pulse user also because I am using hardy, If you're using gutsy you won't need it.
Hope this helps

---

### Post by GaussianMonk on 2008-04-17
well humph. I took advice from both of you and edited the /etc/group file as well as reinstalling alsa. Unfortunately, neither fix worked. After I rebooted I still had no sound output and my glx permissions are still locked. Thanks for your suggestions though.

---

