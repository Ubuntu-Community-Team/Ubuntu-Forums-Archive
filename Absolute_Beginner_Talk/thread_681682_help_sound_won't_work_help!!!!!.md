---
title: "help sound won't work help!!!!!"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-29
I just installed linux mint to my system I set it up with desktop stuff and programs now I need to get sound wokring I've been on this for a while picked up some things I have an alc880 realtek [intel] which I know has a lot of problems working so I've come up with a list of things that could get the sound to work or possibly hamper sound from working I AM NOT APPOSED TO BUYING A NEW SOUNDCARD but I'm afraid it won't work when I boot up heres the list 
1.I have several mixer apps could they be conflicting
2.could alsa and pulseaudio be conflicting
3. could I disable the realtek from the bios and re enable it 
4.should I run alsa config
5.I upgraded alsa if thats more infor 
6.should I upgrade pulse audio 
7. are there any graphical tools to config my sound 
8.how do I reconfig sound 
9.could I install the driver via sudo apt-get 
10.I know intel has realsed a linux driver but its to hard to install and I don't know when to run what bash script I use linux mint 4.0

---

### Post by laidback on 2008-01-29
See if you can get the test sounds from System>Preferences >Sound (I'm running 7.04). That's certainly where I'd start.

---

### Post by jeffus_il on 2008-01-29
What happens if you [LIST]
[*] log out
[*] <ctrl-alt-f1> to a console
[*] login
[*] stop gdm (sudo /etc/init.d/gdm stop)
[*]find pulseaudio (ps -ef | grep pulseaudio)
[*]kill it (kill -9 <the pid from above>)
[*] play something (mplayer "myfavouritemp3")[/LIST]PS: pulseaudio may not be there after logout or may be system wide so then ```
sudo /etc/init,d/pulseaudio stop
```

---

### Post by exneo002 on 2008-01-29
cool I'll try that so I kill pulse audio and play stuff I've tried playing stuff before I installed pulse audio.... it didn't work I  try flash regularly k so I'll try your commands but I can't say I can exacute them all

---

